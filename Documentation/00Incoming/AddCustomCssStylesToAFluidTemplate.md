# Add Custom CSS Styles to a Fluid Template

<!--#TYPO3v13 #Beginner #Frontend #CSS #FluidTemplate #SitePackage @username -->

Fluid templates define the HTML structure of your TYPO3 pages, but without CSS they have no visual styling. By including custom CSS files in your site package, you control the look and feel of your website: colors, fonts, spacing, and responsive behavior.
TYPO3 offers several ways to include CSS, from TypoScript to Fluid ViewHelpers. This guide covers the most common approaches.

## Learning objective

In this step-by-step guide you will add custom CSS styles to your Fluid templates by including CSS files through TypoScript and directly in Fluid.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser
* A code editor or IDE
* A site package extension with Fluid templates (see [Create a Site Package](CreateASitePackage.md))

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md).
* You know how to [Create a site package](CreateASitePackage.md).
* You have basic knowledge of HTML and CSS.

## Create a CSS file

1. Open your site package extension in your code editor.
2. Navigate to the `Resources/Public/Css/` directory. Create it if it does not exist.
3. Create a new file, for example `styles.css`:

   ```css
   body {
       font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
       color: #333;
       background-color: #fff;
       margin: 0;
       padding: 0;
       line-height: 1.6;
   }

   h1, h2, h3 {
       color: #1a1a1a;
   }

   a {
       color: #0078d4;
       text-decoration: none;
   }

   a:hover {
       text-decoration: underline;
   }

   .container {
       max-width: 1200px;
       margin: 0 auto;
       padding: 0 1rem;
   }
   ```

4. Save the file.

## Include CSS via TypoScript

This is the most common method. TypoScript adds the CSS file to the `<head>` section of every page.

1. Open your TypoScript setup file, for example `Configuration/Sets/<YourSet>/setup.typoscript`.
2. Add the CSS include:

   ```typoscript
   page.includeCSS {
       styles = EXT:my_site_package/Resources/Public/Css/styles.css
   }
   ```

3. To include multiple CSS files, add more entries:

   ```typoscript
   page.includeCSS {
       styles = EXT:my_site_package/Resources/Public/Css/styles.css
       navigation = EXT:my_site_package/Resources/Public/Css/navigation.css
       footer = EXT:my_site_package/Resources/Public/Css/footer.css
   }
   ```

4. Save the file.

> [!TIP]
> TypoScript also supports `includeCSSLibs` for external CSS files like Google Fonts or a CSS framework. Use `includeCSS` for your own files and `includeCSSLibs` for third-party libraries.

## Include CSS directly in a Fluid template

For CSS that should only load on specific page templates, you can use the `f:asset.css` ViewHelper directly in your Fluid template:

```html
<f:asset.css identifier="my-special-styles"
    href="EXT:my_site_package/Resources/Public/Css/special.css" />
```

Place this anywhere in your Fluid template. TYPO3 will automatically move it into the `<head>` section of the rendered page.

> [!NOTE]
> The `identifier` must be unique. If two ViewHelpers use the same identifier, the second one will overwrite the first.

## Include external CSS resources

To include a CSS framework like Bootstrap or a Google Font:

```typoscript
page.includeCSSLibs {
    googlefonts = https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap
    googlefonts.external = 1
}
```

Or in Fluid:

```html
<f:asset.css identifier="google-fonts"
    href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap"
    external="1" />
```

## Control CSS loading order

TypoScript lets you control the order of CSS files using the `forceOnTop` option:

```typoscript
page.includeCSS {
    reset = EXT:my_site_package/Resources/Public/Css/reset.css
    reset.forceOnTop = 1

    styles = EXT:my_site_package/Resources/Public/Css/styles.css
}
```

The `reset.css` file will always be loaded before `styles.css`, regardless of the order in TypoScript.

## Verify your styles

1. Clear all caches as explained in [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
2. Open your website's frontend in a new browser tab.
3. Perform a hard refresh (Ctrl + F5 or Cmd + Shift + R) to bypass the browser cache.
4. Verify that your CSS styles are applied. Use your browser's developer tools (F12) to inspect the `<head>` section and confirm that your CSS files are loaded.

## Summary

Congratulations! You have added custom CSS styles to your TYPO3 Fluid templates using TypoScript and Fluid ViewHelpers. You know how to include your own CSS files, external resources, and control the loading order.

## Next steps

Now that you can style your templates, you might like to:

* [Create a two-column layout with Fluid](CreateATwoColumnLayoutWithFluid.md) and style it with CSS
* [Create a site set with editable settings](CreateASiteSet.md) to make colors and fonts configurable in the backend
* Add JavaScript to your site package using `page.includeJS` or `f:asset.script`

## Resources

* [TypoScript PAGE object](https://docs.typo3.org/permalink/t3tsref:page)
* [Asset ViewHelpers](https://docs.typo3.org/permalink/t3coreapi:fluid-viewhelpers-asset)
* [Fluid templating](https://docs.typo3.org/permalink/t3coreapi:fluid)
