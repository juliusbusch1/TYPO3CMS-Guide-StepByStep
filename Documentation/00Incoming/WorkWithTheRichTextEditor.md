# Work with the Rich Text Editor

<!--#TYPO3v13 #Beginner #Backend #RTE #ContentEditing @username -->

The Rich Text Editor (RTE) in TYPO3 allows you to format text content directly in the backend without writing HTML. You can create headings, bold or italic text, links, lists, and tables using a toolbar similar to common word processors.
TYPO3 ships with CKEditor as its default Rich Text Editor, which is available in most text-based content elements.

## Learning objective

In this step-by-step guide you will learn how to use the Rich Text Editor in the TYPO3 backend to format text, create links, and insert lists in a content element.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account or a user with permission to edit content)
* A web browser
* At least one page with a text-based content element (for example "Regular Text Element")

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Add content elements to a page](../10GettingStarted/30CreatingContent/AddContentElementsToAPage.md).

## Open the Rich Text Editor

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. In the left-hand module menu, navigate to **Web > Page**.
3. Select the page that contains the content element you want to edit.
4. Click the pencil icon on the content element to open it for editing.
5. The Rich Text Editor appears in the **Text** field with a formatting toolbar at the top.

## Format text

1. Type or select the text you want to format in the editor area.
2. Use the toolbar buttons to apply formatting:
   * **Bold** (B) to make text bold
   * **Italic** (I) to make text italic
   * **Block quote** to indent a paragraph as a quote
3. To create a heading, place your cursor in the line you want to change, then select a heading level (for example **Heading 2** or **Heading 3**) from the **Paragraph format** dropdown in the toolbar.

> [!NOTE]
> Avoid using Heading 1 inside content elements. The page title already serves as Heading 1 on the frontend.

## Create a link

1. Select the text you want to turn into a link.
2. Click the **Link** button in the toolbar. A dialog opens with several link types.
3. Choose the link type:
   * **Page** to link to another page in your TYPO3 site. Use the page tree or search to find the target page.
   * **External URL** to link to an external website. Enter the full URL including `https://`.
   * **Email** to create a mailto link. Enter the email address.
   * **File** to link to a file in the TYPO3 file system.
4. Configure any additional options like opening the link in a new window.
5. Click **Set link** to confirm.

> [!TIP]
> To remove a link, click on the linked text and then click the **Unlink** button in the toolbar.

## Insert a list

1. Place your cursor where you want to start the list.
2. Click the **Bulleted list** or **Numbered list** button in the toolbar.
3. Type the first list item and press **Enter** to create the next item.
4. Press **Enter** twice or click the list button again to end the list.

## Insert a table

1. Click the **Table** button in the toolbar.
2. Select the number of rows and columns from the grid that appears.
3. Click to insert the table. A table with empty cells appears in the editor.
4. Click into each cell to enter content.

> [!TIP]
> Right-click inside a table to access options for adding or removing rows and columns.

## Save and verify

1. After you are done editing, click **Save** at the top of the form.
2. Clear the frontend cache by following [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
3. Open your website's frontend in a new browser tab and navigate to the page. Your formatted text, links, lists, and tables should appear as expected.

## Summary

Congratulations! You have used the TYPO3 Rich Text Editor to format text, create links, insert lists, and add tables to a content element.

## Next steps

Now that you can work with the Rich Text Editor, you might like to:

* [Add content elements to a page](../10GettingStarted/30CreatingContent/AddContentElementsToAPage.md) to create more content
* [Modify the page properties](ModifyingThePageProperties.md) to adjust the page title or URL
* Explore the RTE configuration to customize which toolbar buttons are available

## Resources

* [Rich Text Editor](https://docs.typo3.org/permalink/t3coreapi:rte)
* [CKEditor configuration](https://docs.typo3.org/permalink/t3coreapi:rte-ckeditor-configuration)
