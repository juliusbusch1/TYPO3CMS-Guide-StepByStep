# Activating the Site Set in the Site Configuration

<!--#TYPO3v13 #Beginner #Backend #SiteConfiguration #SiteSet @username -->

TYPO3 uses site sets to bundle configuration, TypoScript, and settings that belong to a specific extension or site package.
A site set is only active when it has been added to the site configuration of your project.
Until you activate it, none of the TypoScript, settings, or dependencies defined in that set will take effect.

## Learning objective

In this step-by-step guide you will activate a site set in the TYPO3 site configuration so that its TypoScript and settings are applied to your site.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser
* At least one extension or site package that provides a site set (a `Configuration/Sets/` directory with a `config.yaml` file)

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You understand the basic concept of TYPO3 site configuration.

## Activate a site set

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. In the left-hand module menu, navigate to **Site Management > Sites**.
3. Click the pencil icon next to the site configuration you want to edit.
4. Switch to the **Sets** tab in the site configuration form.
5. In the **Sets** field, click **Add set**. A modal opens listing all available site sets.
6. Select the site set you want to activate (for example, "My Site Package") and confirm.
7. Click **Save** at the top of the form to store your changes.

> [!NOTE]
> Site sets can depend on other site sets. When you activate a set, TYPO3 automatically resolves and loads its dependencies. You do not need to add dependent sets manually.

> [!TIP]
> If the site set you expect does not appear in the list, verify that the extension providing it is installed and that its `Configuration/Sets/` directory contains a valid `config.yaml`.

8. Clear all caches by following [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md) to ensure the new configuration takes effect.
9. Verify the activation by checking that the TypoScript or settings provided by the site set are now applied to your site's frontend output.

## Summary

Congratulations! You have activated a site set in your TYPO3 site configuration. The TypoScript, settings, and dependencies defined in the set are now applied to your site.

## Next steps

Now that you have activated a site set, you might like to:

* [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md) after making further configuration changes
* Explore creating your own site set in a custom site package
* Review the site set's settings and override them in the site configuration

## Resources

* [Site sets](https://docs.typo3.org/permalink/t3coreapi:site-sets)
* [Site configuration](https://docs.typo3.org/permalink/t3coreapi:sitehandling)
