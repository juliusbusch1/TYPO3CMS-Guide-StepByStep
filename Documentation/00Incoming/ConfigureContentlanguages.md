# Configure Additional Content Languages

<!--#TYPO3v13 #Beginner #Backend #Languages #SiteConfiguration @username -->

TYPO3 supports multilingual websites out of the box. Before editors can translate content, you need to configure which languages are available for your site.
Each language is defined in the site configuration with a locale, a language title, and a navigation prefix or subdomain. Once configured, editors can create and manage content in multiple languages directly in the backend.

## Learning objective

In this step-by-step guide you will add a new content language to your TYPO3 site configuration so that editors can create translated content.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md).
* You understand the basic concept of TYPO3 site configuration.

## Open the site configuration

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. In the left-hand module menu, navigate to **Site Management > Sites**.
3. Click the pencil icon next to the site configuration you want to edit.

## Review the default language

1. Switch to the **Languages** tab in the site configuration form.
2. You will see the default language already configured (usually English or your installation language). This is the language with ID 0.
3. Note the settings for the default language: **Title**, **Locale**, **Base** (URL prefix), and **Navigation Title**. Your new language will follow the same pattern.

## Add a new language

1. In the **Languages** tab, click **Add language** at the bottom of the language list.
2. Fill in the following fields for your new language:

   * **Language** select the language from the dropdown, for example "German" or "French"
   * **Title** enter a descriptive title, for example "Deutsch" or "Français"
   * **Navigation Title** enter the title as it should appear in a language switcher, for example "DE" or "FR"
   * **Locale** enter the full locale identifier, for example `de_DE.UTF-8` or `fr_FR.UTF-8`
   * **Base** enter the URL prefix for this language, for example `/de/` or `/fr/`
   * **Fallback Type** select how TYPO3 should handle missing translations:
     * **Strict** shows an error if no translation exists
     * **Fallback to other language** falls back to the default language
     * **Free mode** allows independent content per language

3. Click **Save** at the top of the form.

> [!NOTE]
> The language ID is assigned automatically by TYPO3. You do not need to set it manually.

> [!TIP]
> For most projects, "Fallback to other language" is the safest option. It ensures pages are always accessible, even when not all content has been translated yet.

## Add more languages

Repeat the previous step for each additional language you want to support. Each language needs its own unique locale and URL base.

## Verify the configuration

1. Clear all caches as explained in [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
2. Navigate to **Web > Page** and select a page.
3. At the top of the page module, you should now see a language dropdown or language columns showing your newly configured languages.
4. Open your website's frontend and append the language prefix to the URL (for example `/de/`). The page should load in the configured fallback mode.

## Summary

Congratulations! You have added a new content language to your TYPO3 site configuration. Editors can now create and manage translated content in the backend.

## Next steps

Now that you have configured additional languages, you might like to:

* [Translate existing content](TranslateContent.md) into your newly configured language
* Add a language switcher to your frontend template
* Configure language-specific domains or subdomains

## Resources

* [Site languages](https://docs.typo3.org/permalink/t3coreapi:sitehandling-addingLanguages)
* [Working with languages](https://docs.typo3.org/permalink/t3coreapi:languages)
