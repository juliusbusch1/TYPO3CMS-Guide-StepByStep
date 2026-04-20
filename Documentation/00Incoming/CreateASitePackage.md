# Create a Site Package

<!--#TYPO3v13 #Beginner #Backend #SitePackage #Extension @username -->

A site package is a TYPO3 extension that bundles everything your website needs in one place: Fluid templates, TypoScript configuration, CSS, JavaScript, and site sets.
Instead of scattering configuration across multiple locations, a site package keeps your project organized and version-controllable. Most TYPO3 projects start with creating a site package as the foundation for all frontend output.

## Learning objective

In this step-by-step guide you will create a basic TYPO3 site package extension with the required directory structure, configuration files, and a simple Fluid template.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser
* A code editor or IDE
* Composer (if using a Composer-based installation)

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md).
* You have basic knowledge of HTML and CSS.

## Create the extension directory structure

1. Open your code editor and navigate to your TYPO3 project.
2. In the `packages/` directory (Composer-based) or `typo3conf/ext/` directory (classic), create a new folder for your site package, for example `my_site_package`.
3. Inside `my_site_package/`, create the following directory structure:

   ```
   my_site_package/
   ├── Configuration/
   │   ├── Sets/
   │   │   └── MySitePackage/
   │   └── TypoScript/
   ├── Resources/
   │   ├── Private/
   │   │   ├── Layouts/
   │   │   │   └── Page/
   │   │   ├── Partials/
   │   │   │   └── Page/
   │   │   └── Templates/
   │   │       └── Page/
   │   └── Public/
   │       ├── Css/
   │       └── JavaScript/
   └── ext_emconf.php
   ```

## Create the extension registration file

1. Create the file `ext_emconf.php` in the root of your site package:

   ```php
   <?php

   $EM_CONF[$_EXTKEY] = [
       'title' => 'My Site Package',
       'description' => 'Site package for my TYPO3 project',
       'category' => 'templates',
       'author' => 'Your Name',
       'state' => 'stable',
       'version' => '1.0.0',
       'constraints' => [
           'depends' => [
               'typo3' => '13.0.0-13.99.99',
               'fluid_styled_content' => '13.0.0-13.99.99',
           ],
       ],
   ];
   ```

2. Save the file.

## Create the site set

1. Inside `Configuration/Sets/MySitePackage/`, create a file named `config.yaml`:

   ```yaml
   name: my-vendor/my-site-package
   label: My Site Package
   dependencies:
     - typo3/fluid-styled-content
   ```

2. Create a file named `setup.typoscript` in the same directory:

   ```typoscript
   page = PAGE
   page {
       typeNum = 0

       10 = FLUIDTEMPLATE
       10 {
           templateName = Default
           templateRootPaths {
               10 = EXT:my_site_package/Resources/Private/Templates/Page/
           }
           layoutRootPaths {
               10 = EXT:my_site_package/Resources/Private/Layouts/Page/
           }
           partialRootPaths {
               10 = EXT:my_site_package/Resources/Private/Partials/Page/
           }
       }

       includeCSS {
           main = EXT:my_site_package/Resources/Public/Css/main.css
       }
   }
   ```

3. Save both files.

## Create the Fluid templates

1. Create the layout file `Resources/Private/Layouts/Page/Default.html`:

   ```html
   <html data-namespace-typo3-fluid="true"
         xmlns:f="http://typo3.org/ns/TYPO3/CMS/Fluid/ViewHelpers">

   <f:render section="Main" />

   </html>
   ```

2. Create the template file `Resources/Private/Templates/Page/Default.html`:

   ```html
   <html data-namespace-typo3-fluid="true"
         xmlns:f="http://typo3.org/ns/TYPO3/CMS/Fluid/ViewHelpers">

   <f:layout name="Default" />

   <f:section name="Main">
       <header>
           <h1>{data.title}</h1>
       </header>
       <main>
           <f:cObject typoscriptObjectPath="lib.dynamicContent" />
       </main>
       <footer>
           <p>My TYPO3 Website</p>
       </footer>
   </f:section>

   </html>
   ```

3. Save both files.

## Add a basic CSS file

1. Create the file `Resources/Public/Css/main.css`:

   ```css
   body {
       font-family: Arial, sans-serif;
       margin: 0;
       padding: 0;
       line-height: 1.6;
   }

   header, main, footer {
       max-width: 960px;
       margin: 0 auto;
       padding: 1rem;
   }

   footer {
       border-top: 1px solid #ccc;
       margin-top: 2rem;
       color: #666;
   }
   ```

2. Save the file.

## Install and activate the site package

1. If you use Composer, add the package to your `composer.json` repository configuration and run:

   ```bash
   composer require my-vendor/my-site-package:@dev
   ```

   If you use a classic installation, the extension is already in `typo3conf/ext/` and can be activated in the Extension Manager.

2. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
3. Activate the site set as explained in [Activating the Site Set in the Site Configuration](ActivatingSiteset.md).
4. Clear all caches as explained in [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
5. Open your website's frontend in a new browser tab. You should see your page rendered with the Fluid template and CSS from your site package.

> [!TIP]
> If you see a blank page, check that the site set is activated and that the TypoScript template paths match your actual directory structure.

## Summary

Congratulations! You have created a TYPO3 site package with a Fluid template, TypoScript configuration, a site set, and a basic CSS file. Your site package is the foundation for all frontend output of your project.

## Next steps

Now that you have a site package, you might like to:

* [Create a site set with editable settings and custom CSS](CreateASiteSet.md) to add configurable options
* Add more page templates for different layouts
* Create partials for reusable components like navigation or header

## Resources

* [Site package tutorial](https://docs.typo3.org/permalink/t3sitepackage:start)
* [Fluid templating](https://docs.typo3.org/permalink/t3coreapi:fluid)
* [Site sets](https://docs.typo3.org/permalink/t3coreapi:site-sets)
