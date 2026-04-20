# Create a Two-Column Layout With Fluid

<!--#TYPO3v13 #Beginner #Backend #FluidTemplate #BackendLayout #Layout @username -->

Many websites need more than a single content column. A two-column layout lets editors place content side by side, for example a main content area next to a sidebar.
In TYPO3, multi-column layouts are built by combining a backend layout (which defines the column structure in the backend) with a Fluid template (which renders the columns on the frontend).

## Learning objective

In this step-by-step guide you will create a two-column page layout using a backend layout and a Fluid template in your site package.

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
* You know how to [Add Page TSconfig to a site package](AddPageTsconfigToASitePackage.md).
* You have basic knowledge of HTML, CSS, and Fluid templating.

## Define the backend layout

The backend layout tells TYPO3 how many content columns exist and how they are arranged in the Page module.

1. Open your site package and create or edit the file `Configuration/Sets/<YourSet>/page.tsconfig` (or wherever you keep your Page TSconfig).
2. Add the following backend layout definition:

   ```tsconfig
   mod.web_layout.BackendLayouts {
       two_column {
           title = Two Column
           icon = EXT:my_site_package/Resources/Public/Icons/BackendLayouts/TwoColumn.svg
           config {
               backend_layout {
                   colCount = 2
                   rowCount = 1
                   rows {
                       1 {
                           columns {
                               1 {
                                   name = Main Content
                                   colPos = 0
                               }
                               2 {
                                   name = Sidebar
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

3. Save the file. The Page module will now show two content columns when this layout is selected.

## Create the Fluid template

1. In your site package, create a new file `Resources/Private/Templates/Page/TwoColumn.html`:

   ```html
   <html data-namespace-typo3-fluid="true"
         xmlns:f="http://typo3.org/ns/TYPO3/CMS/Fluid/ViewHelpers">

   <f:layout name="Default" />

   <f:section name="Main">
       <div class="two-column-layout">
           <div class="two-column-layout__main">
               <f:cObject typoscriptObjectPath="lib.dynamicContent" data="{colPos: 0}" />
           </div>
           <div class="two-column-layout__sidebar">
               <f:cObject typoscriptObjectPath="lib.dynamicContent" data="{colPos: 1}" />
           </div>
       </div>
   </f:section>

   </html>
   ```

2. Save the file.

## Map the backend layout to the Fluid template

1. Open or create your TypoScript setup file, for example `Configuration/Sets/<YourSet>/setup.typoscript`.
2. Add the template mapping so TYPO3 knows which Fluid template to use for the two-column backend layout:

   ```typoscript
   page.10 {
       templateName = Default
       templateName.stdWrap.cObject = CASE
       templateName.stdWrap.cObject {
           key.data = pagelayout

           two_column = TEXT
           two_column.value = TwoColumn

           default = TEXT
           default.value = Default
       }
   }
   ```

3. Save the file.

## Add CSS for the two-column layout

1. Open your CSS file, for example `Resources/Public/Css/main.css`.
2. Add the following styles:

   ```css
   .two-column-layout {
       display: grid;
       grid-template-columns: 2fr 1fr;
       gap: 2rem;
   }

   @media (max-width: 768px) {
       .two-column-layout {
           grid-template-columns: 1fr;
       }
   }
   ```

3. Save the file. The layout will be responsive, collapsing to a single column on small screens.

## Apply the layout to a page

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. Clear all caches as explained in [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
3. Navigate to **Web > Page** and select the page you want to use the two-column layout on.
4. Click the **Edit page properties** button (pencil icon).
5. Switch to the **Appearance** tab.
6. In the **Backend Layout (this page only)** dropdown, select **Two Column**.
7. Click **Save**.
8. The Page module now shows two content columns: "Main Content" and "Sidebar". Add content elements to both columns.

## Verify the layout

1. Clear the frontend cache.
2. Open the page in your website's frontend.
3. You should see the main content on the left and the sidebar content on the right, arranged in a two-column grid.

## Summary

Congratulations! You have created a two-column page layout in TYPO3 by defining a backend layout, creating a matching Fluid template, and adding responsive CSS.

## Next steps

Now that you have a two-column layout, you might like to:

* Create additional layouts (three columns, full width, content with hero image)
* [Add custom CSS styles to a Fluid template](AddCustomCssStylesToAFluidTemplate.md) for more design options
* Allow editors to choose layouts for subpages using "Backend Layout (subpages of this page)"

## Resources

* [Backend layouts](https://docs.typo3.org/permalink/t3coreapi:be-layout)
* [Fluid templating](https://docs.typo3.org/permalink/t3coreapi:fluid)
* [Page TSconfig reference](https://docs.typo3.org/permalink/t3tsconfig:pagetsconfig)
