# Adding Page TSconfig to a Site Package

<!--#TYPO3v13 #Beginner #Backend #TSconfig #SitePackage @username -->

Page TSconfig lets you customize the TYPO3 backend for editors: you can restrict available content element types, configure backend layouts, adjust form fields, and control which options appear in dropdown menus.
By adding Page TSconfig to your site package instead of individual pages, you ensure that your backend customizations are version-controlled, consistent across all pages, and easy to maintain.

## Learning objective

In this step-by-step guide you will add Page TSconfig to a TYPO3 site package so that it is automatically applied to your entire site.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser
* A code editor or IDE
* A site package extension (see [Create a Site Package](CreateASitePackage.md))

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md).
* You know how to [Create a site package](CreateASitePackage.md).

## Create the TSconfig file

1. Open your site package extension in your code editor.
2. Create the directory `Configuration/page.tsconfig` if it does not exist. In TYPO3 v13 you can also use `Configuration/Sets/<YourSet>/page.tsconfig` to include it automatically via your site set.
3. Add your Page TSconfig. For example, to restrict the available content element types to only text, textmedia, and header:

   ```tsconfig
   mod.wizards.newContentElement.wizardItems {
       common.show := removeFromList(bullets, table, uploads, div, html)
   }
   ```

4. Save the file.

## Register the TSconfig via site set

If you use a site set (recommended for TYPO3 v13), the file `Configuration/Sets/<YourSet>/page.tsconfig` is loaded automatically when the site set is active. No additional registration is needed.

> [!TIP]
> This is the simplest approach. If your site set is already activated, just place the file and clear caches.

## Alternative: Register via ext_localconf.php

If you do not use a site set, you can register the TSconfig file globally in your extension:

1. Open or create the file `ext_localconf.php` in the root of your site package.
2. Add the following code:

   ```php
   <?php

   defined('TYPO3') or die();

   \TYPO3\CMS\Core\Utility\ExtensionManagementUtility::addPageTSConfig(
       '@import "EXT:my_site_package/Configuration/TsConfig/Page/page.tsconfig"'
   );
   ```

3. In this case, place your TSconfig file at `Configuration/TsConfig/Page/page.tsconfig`.
4. Save both files.

## Common Page TSconfig examples

### Restrict content element types

```tsconfig
mod.wizards.newContentElement.wizardItems {
    common.show = header, text, textmedia, image
}
```

### Define backend layouts

```tsconfig
mod.web_layout.BackendLayouts {
    two_column {
        title = Two Column
        config {
            backend_layout {
                colCount = 2
                rowCount = 1
                rows {
                    1 {
                        columns {
                            1 {
                                name = Left
                                colPos = 0
                            }
                            2 {
                                name = Right
                                colPos = 1
                            }
                        }
                    }
                }
            }
        }
    }
}
```

### Set default values for new content elements

```tsconfig
TCAdefaults.tt_content {
    header_layout = 2
}
```

## Verify your changes

1. Clear all caches as explained in [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
2. Navigate to **Web > Page** and select a page.
3. Click **+ Content** to open the content element wizard and verify that your restrictions are applied.
4. If you added backend layouts, check the **Appearance** tab in the page properties to see your new layouts.

> [!NOTE]
> Page TSconfig added via a site set or `ext_localconf.php` applies to all pages. If you need TSconfig only on specific page branches, set it on individual pages via the page properties instead.

## Summary

Congratulations! You have added Page TSconfig to your site package. Your backend customizations are now version-controlled and applied consistently across your entire TYPO3 site.

## Next steps

Now that you can add Page TSconfig to your site package, you might like to:

* [Create a two-column layout with Fluid](CreateATwoColumnLayoutWithFluid.md) using the backend layout you defined
* Restrict available page types or hide unused fields for editors
* Explore User TSconfig to customize the backend per user or group

## Resources

* [Page TSconfig reference](https://docs.typo3.org/permalink/t3tsconfig:pagetsconfig)
* [Backend layouts](https://docs.typo3.org/permalink/t3coreapi:be-layout)
