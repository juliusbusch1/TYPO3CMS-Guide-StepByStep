# Create a Page with the Context Menu

<!--#TYPO3v13 #Beginner #Backend #PageTree #ContextMenu @username -->

The page tree in the TYPO3 backend represents the structure of your website. Each entry in the tree corresponds to a page that can hold content, act as a folder, or serve as a link.
The fastest way to create a new page is by right-clicking an existing page in the page tree to open the context menu. From there you can insert a new page directly above, below, or as a subpage of the selected page.

## Learning objective

In this step-by-step guide you will create a new page in the TYPO3 page tree by using the context menu.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account or a user with permission to create pages)
* A web browser

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You are familiar with the TYPO3 page tree in the left-hand navigation area.

## Create a new page

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).

2. In the left-hand module menu, click on **Web > Page** to open the page module. The page tree appears on the left side of the screen.

3. In the page tree, right-click the page that should be the parent or sibling of your new page. The context menu opens with several options.

4. Hover over **Page Actions** in the context menu. A submenu with positioning options appears.

5. Select one of the following options:
   * **New page into** to create the new page as a subpage (child) of the selected page
   * **New page after** to create the new page directly below the selected page at the same level

6. A new page entry appears in the page tree with a default title. Type a title for your new page, for example "Contact", and press **Enter** to confirm.

> [!NOTE]
> The new page is hidden by default. It will not appear on your website's frontend until you make it visible in the page properties.

> [!TIP]
> You can also drag and drop pages in the page tree to rearrange them after creation.

## Make the page visible

7. Click on your newly created page in the page tree to open it in the page module.

8. Click the **Edit page properties** button (pencil icon) at the top of the page module.

9. Switch to the **Access** tab, uncheck **Disable**, and click **Save**.

10. Clear the frontend cache by following [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).

11. Open your website's frontend in a new browser tab and verify that the new page appears in the navigation.

## Summary

Congratulations! You have created a new page in the TYPO3 page tree using the context menu and made it visible on your website.

## Next steps

Now that you have created a page, you might like to:

* [Add content elements to the page](../10GettingStarted/30CreatingContent/AddContentElementsToAPage.md) to fill it with text, images, or other content
* [Modify the page properties](ModifyingThePageProperties.md) to change the page title, URL slug, or visibility
* Create subpages to build a deeper navigation structure

## Resources

* [Pages](https://docs.typo3.org/permalink/t3coreapi:pages)
* [Page types](https://docs.typo3.org/permalink/t3coreapi:page-types)
