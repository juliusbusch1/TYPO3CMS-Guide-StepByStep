# Create Custom Content Elements

<!--#TYPO3v13 #Beginner #Backend #ContentElements #Customization @username -->

TYPO3 ships with a set of default content elements like text, images, and lists, but many projects need content elements tailored to a specific design or functionality.
Custom content elements let you define your own fields, templates, and rendering logic that editors can use like any other element.

## Learning objective

In this step-by-step guide you will create a custom content element in TYPO3 with its own fields, Fluid template, and TypoScript configuration.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser
* A code editor or IDE to create and edit files in your site package extension
* A site package extension with a basic directory structure

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Add content elements to a page](../10GettingStarted/30CreatingContent/AddContentElementsToAPage.md).
* You know how to [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md).
* You have basic knowledge of Fluid templating and TypoScript.

## Register the content element type

1. Open your site package extension in your code editor.
2. Navigate to the file `Configuration/TCA/Overrides/tt_content.php`. Create it if it does not exist.
3. Add the following code to register a new content element type:

   ```php
   <?php

   defined('TYPO3') or die();

   \TYPO3\CMS\Core\Utility\ExtensionManagementUtility::addTcaSelectItem(
       'tt_content',
       'CType',
       [
           'label' => 'My Custom Element',
           'value' => 'my_custom_element',
           'icon' => 'content-text',
           'group' => 'default',
       ]
   );
   ```

4. Save the file. TYPO3 now recognizes the new CType.

## Define the fields for the content element

1. In the same file `Configuration/TCA/Overrides/tt_content.php`, add the TCA configuration for your element:

   ```php
   $GLOBALS['TCA']['tt_content']['types']['my_custom_element'] = [
       'showitem' => '
           --div--;LLL:EXT:core/Resources/Private/Language/Form/locallang_tabs.xlf:general,
               --palette--;;general,
               header; Header,
               bodytext; Text,
           --div--;LLL:EXT:core/Resources/Private/Language/Form/locallang_tabs.xlf:access,
               --palette--;;hidden,
               --palette--;;access,
       ',
       'columnsOverrides' => [
           'bodytext' => [
               'config' => [
                   'enableRichtext' => true,
               ],
           ],
       ],
   ];
   ```

2. Save the file. This defines which fields appear when editing your custom content element.

## Add the content element to the new content element wizard

1. Create or open the file `Configuration/TsConfig/Page/ContentElement.tsconfig` in your extension.
2. Add the following page TSconfig:

   ```tsconfig
   mod.wizards.newContentElement.wizardItems.common {
       elements {
           my_custom_element {
               iconIdentifier = content-text
               title = My Custom Element
               description = A custom content element with header and rich text
               tt_content_defValues {
                   CType = my_custom_element
               }
           }
       }
       show := addToList(my_custom_element)
   }
   ```

3. Save the file. The element now appears in the content element wizard when adding new content.

## Create the Fluid template

1. Create the directory `Resources/Private/Templates/ContentElements/` in your extension if it does not exist.
2. Create a file named `MyCustomElement.html` in that directory:

   ```html
   <html data-namespace-typo3-fluid="true"
         xmlns:f="http://typo3.org/ns/TYPO3/CMS/Fluid/ViewHelpers">

   <f:if condition="{data.header}">
       <h2>{data.header}</h2>
   </f:if>

   <f:if condition="{data.bodytext}">
       <div class="my-custom-element">
           <f:format.html>{data.bodytext}</f:format.html>
       </div>
   </f:if>

   </html>
   ```

3. Save the file.

## Configure TypoScript rendering

1. Create or open the file `Configuration/TypoScript/setup.typoscript` in your extension.
2. Add the TypoScript configuration to map the CType to the Fluid template:

   ```typoscript
   tt_content.my_custom_element =< lib.contentElement
   tt_content.my_custom_element {
       templateName = MyCustomElement
       templateRootPaths {
           10 = EXT:my_site_package/Resources/Private/Templates/ContentElements/
       }
   }
   ```

3. Save the file.

> [!NOTE]
> Make sure your site set or TypoScript include loads this setup file. Otherwise TYPO3 will not know how to render your custom element.

## Test the custom content element

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. Clear all caches as explained in [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
3. Navigate to **Web > Page** and select a page.
4. Click **+ Content** to open the content element wizard.
5. Find **My Custom Element** in the list and click it to add it to the page.
6. Fill in the **Header** and **Text** fields and click **Save**.
7. Clear the frontend cache and open the page in your website's frontend. Your custom content element should appear with the header and formatted text.

> [!TIP]
> If the element does not render on the frontend, check that the TypoScript is loaded and that the Fluid template path is correct.

## Summary

Congratulations! You have created a custom content element in TYPO3 with its own TCA configuration, Fluid template, and TypoScript rendering setup. The element is available in the backend content element wizard and renders on the frontend.

## Next steps

Now that you have created a custom content element, you might like to:

* Add more fields like images or select boxes to your element
* Create additional custom content elements for different use cases
* Style your element with custom CSS using a [site set](CreateASiteSet.md)

## Resources

* [Content elements](https://docs.typo3.org/permalink/t3coreapi:content-elements)
* [Fluid templating](https://docs.typo3.org/permalink/t3coreapi:fluid)
* [TCA reference](https://docs.typo3.org/permalink/t3tca:start)
