# Create a Site Set with Editable Settings and Custom CSS

<!--#TYPO3v13 #Beginner #Backend #SiteSet #Configuration @username -->

TYPO3 site sets bundle TypoScript, settings, and assets for a site or extension into a single, reusable package.
By defining editable settings in a site set, you allow backend users to adjust values like colors, fonts, or feature toggles without touching TypoScript directly.
You can also include custom CSS that is automatically loaded when the site set is active.

## Learning objective

In this step-by-step guide you will create a site set that provides editable settings and a custom CSS file for your TYPO3 site.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser
* A code editor or IDE to create and edit files in your site package extension
* A site package extension with a `Configuration/Sets/` directory

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Activate a site set in the site configuration](ActivatingSiteset.md).
* You know how to [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md).

## Create the site set directory

1. Open your site package extension in your code editor.
2. Inside the extension, navigate to the `Configuration/Sets/` directory. If it does not exist, create it.
3. Create a new subdirectory for your site set, for example `Configuration/Sets/MySiteSet/`.

## Define the site set in config.yaml

1. Inside `Configuration/Sets/MySiteSet/`, create a file named `config.yaml`.
2. Add the following content:

   ```yaml
   name: my-vendor/my-site-set
   label: My Site Set
   ```

3. Save the file. TYPO3 now recognizes this directory as a site set.

## Add editable settings

1. Inside `Configuration/Sets/MySiteSet/`, create a file named `settings.definitions.yaml`.
2. Define your editable settings, for example:

   ```yaml
   settings:
     my-vendor/my-site-set.primaryColor:
       label: Primary color
       description: The main brand color used across the site
       type: string
       default: '#0078d4'
     my-vendor/my-site-set.showBreadcrumb:
       label: Show breadcrumb
       description: Toggle breadcrumb navigation on all pages
       type: bool
       default: true
   ```

3. Save the file.

> [!NOTE]
> The setting keys must be prefixed with the site set name to avoid conflicts with other sets.

## Provide default setting values

1. Inside `Configuration/Sets/MySiteSet/`, create a file named `settings.yaml`.
2. Add your default values:

   ```yaml
   settings:
     my-vendor/my-site-set.primaryColor: '#0078d4'
     my-vendor/my-site-set.showBreadcrumb: true
   ```

3. Save the file. These values apply unless a backend user overrides them in the site configuration.

## Include custom CSS

1. Inside `Configuration/Sets/MySiteSet/`, create a file named `setup.typoscript`.
2. Add TypoScript to include your CSS file:

   ```typoscript
   page.includeCSS.mySiteSet = EXT:my_site_package/Resources/Public/Css/MySiteSet.css
   ```

3. Create the CSS file at `Resources/Public/Css/MySiteSet.css` in your extension and add your styles:

   ```css
   :root {
       --primary-color: #0078d4;
   }

   body {
       font-family: Arial, sans-serif;
   }
   ```

4. Save both files.

> [!TIP]
> To make the CSS dynamic based on your editable settings, use TypoScript constants in your `setup.typoscript` that reference the site set settings.

## Activate the site set and verify

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. Activate the site set as explained in [Activating the Site Set in the Site Configuration](ActivatingSiteset.md).
3. Clear all caches as explained in [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
4. Navigate to **Site Management > Sites** and click the pencil icon next to your site.
5. Switch to the **Settings** tab. Your editable settings (Primary color, Show breadcrumb) should appear here.
6. Change a setting value and click **Save**.
7. Clear all caches again and open your site's frontend in a new browser tab. Verify that the custom CSS is loaded and your setting changes are reflected.

## Summary

Congratulations! You have created a TYPO3 site set with editable settings and a custom CSS file. Backend users can now adjust the settings you defined without editing TypoScript or CSS files directly.

## Next steps

Now that you have created a site set, you might like to:

* [Activate the site set in the site configuration](ActivatingSiteset.md) on additional sites
* Add more settings for fonts, layout options, or feature toggles
* Create additional site sets for different aspects of your project

## Resources

* [Site sets](https://docs.typo3.org/permalink/t3coreapi:site-sets)
* [Site set settings](https://docs.typo3.org/permalink/t3coreapi:site-sets-settings)
* [Site configuration](https://docs.typo3.org/permalink/t3coreapi:sitehandling)
