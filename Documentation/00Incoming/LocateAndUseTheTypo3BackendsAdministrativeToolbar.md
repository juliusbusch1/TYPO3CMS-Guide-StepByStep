# Locate and Use the TYPO3 Backend's Administrative Toolbar

<!--#TYPO3v13 #Beginner #Backend #Toolbar #Navigation @username -->

The administrative toolbar is the horizontal bar at the very top of the TYPO3 backend. It gives you quick access to frequently used actions like clearing caches, searching for records, switching between users, and managing bookmarks.
Understanding the toolbar helps you navigate the backend more efficiently and perform common tasks without searching through menus.

## Learning objective

In this step-by-step guide you will locate the administrative toolbar in the TYPO3 backend and learn what each toolbar item does.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).

## Locate the administrative toolbar

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. Look at the very top of the backend interface. The administrative toolbar spans the full width of the screen as a dark horizontal bar.
3. On the left side of the toolbar you find the TYPO3 logo and the top bar menu. On the right side you find several icon buttons for common actions.

## Explore the toolbar items

The toolbar contains the following items from left to right:

### Left side

* **TYPO3 logo** opens the About page with version information and installed extensions.
* **Top bar menu** contains links to available backend modules.

### Right side

* **Search** (magnifying glass icon) opens a search field that lets you find pages, content elements, and other records across the entire installation.
* **Bookmarks** (star icon) lets you save and access frequently used backend pages. Click the star to see your saved bookmarks or to add the current page.
* **Clear Cache** (lightning icon) opens a dropdown with cache clearing options. Use this to flush frontend caches or all caches after making changes.
* **Debug Console** (bug icon, visible for admins) gives access to debug and system information tools.
* **User menu** (person icon) opens a dropdown with your account settings, preferences, and the logout button.

> [!NOTE]
> The exact items visible in the toolbar depend on your user role and permissions. Non-admin users may see fewer options.

> [!TIP]
> You can use the keyboard shortcut **Ctrl + K** (or **Cmd + K** on Mac) to open the search directly without clicking the magnifying glass icon.

## Use the search

1. Click the magnifying glass icon in the toolbar or press **Ctrl + K** (or **Cmd + K** on Mac).
2. Type a search term, for example a page title or content element text.
3. Results appear immediately below the search field, grouped by type (pages, content, files).
4. Click a result to navigate directly to that record in the backend.

## Use bookmarks

1. Navigate to a backend page you want to bookmark, for example a specific page in the Page module.
2. Click the star icon in the toolbar and select **Create bookmark for this page**.
3. To access your bookmarks later, click the star icon again. Your saved bookmarks appear in the dropdown.

## Use the user menu

1. Click the person icon on the far right of the toolbar.
2. A dropdown opens with the following options:
   * **User Settings** to change your password, language, and backend preferences
   * **Switch to user** (admin only) to impersonate another backend user for testing
   * **Logout** to end your session

## Summary

Congratulations! You now know where to find the administrative toolbar in the TYPO3 backend and how to use its main features: searching for records, managing bookmarks, clearing caches, and accessing your user settings.

## Next steps

Now that you are familiar with the toolbar, you might like to:

* [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md) using the Clear Cache menu in the toolbar
* [Modify the page properties](ModifyingThePageProperties.md) of a page you found via the search
* Customize your backend preferences in the User Settings

## Resources

* [The administrative toolbar](https://docs.typo3.org/permalink/t3coreapi:backend-toolbar)
* [Backend user settings](https://docs.typo3.org/permalink/t3coreapi:be-user-configuration)
