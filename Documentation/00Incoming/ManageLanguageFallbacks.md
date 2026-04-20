# Manage Language Fallbacks

<!--#TYPO3v13 #Beginner #Backend #Languages #Fallback #SiteConfiguration @username -->

When your TYPO3 site supports multiple languages, not every page or content element will have a translation right away. Language fallbacks control what happens when a visitor requests a page in a language that has no translation yet.
You can configure TYPO3 to fall back to another language, show the default language content, or display an error page. Choosing the right fallback strategy avoids blank pages and gives your visitors a consistent experience.

## Learning objective

In this step-by-step guide you will configure and manage language fallback behavior for your TYPO3 site so that untranslated pages remain accessible.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account)
* A web browser
* At least two languages configured in your site configuration

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Configure additional content languages](ConfigureContentlanguages.md).
* You know how to [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md).

## Open the language configuration

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. In the left-hand module menu, navigate to **Site Management > Sites**.
3. Click the pencil icon next to your site configuration.
4. Switch to the **Languages** tab.

## Understand the fallback types

TYPO3 offers three fallback types for each language. Click on the language you want to configure and look for the **Fallback Type** field:

* **Fallback to other language** shows content from a fallback language when no translation exists. This is the most common choice. Visitors always see content, even if it is not in their preferred language.
* **Strict** returns a 404 error if no translation exists for the requested page. Use this when you want to ensure that only fully translated pages are accessible.
* **Free mode** treats each language as independent. Content is not connected to the default language. Use this when your languages have completely different content structures.

## Configure a fallback chain

When using "Fallback to other language", you can define which languages TYPO3 should try before giving up:

1. In the language configuration, find the **Fallback Language IDs** field.
2. Enter the language IDs in the order TYPO3 should try them, separated by commas. For example:
   * For a German language entry, enter `0` to fall back to the default language (English).
   * For a Swiss German entry, enter `1,0` to first try German (ID 1), then fall back to English (ID 0).
3. Click **Save** at the top of the form.

> [!NOTE]
> The default language (ID 0) does not have a fallback configuration. It always shows its own content.

> [!TIP]
> You can find the language IDs in the **Languages** tab of your site configuration. Each language entry shows its ID.

## Example: Three-language setup with fallbacks

Consider a site with English (ID 0), German (ID 1), and French (ID 2):

| Language | Fallback Type | Fallback IDs | Behavior |
|---|---|---|---|
| English (0) | Default language | none | Always shows English content |
| German (1) | Fallback to other language | `0` | Shows German, falls back to English |
| French (2) | Fallback to other language | `0` | Shows French, falls back to English |

This setup ensures that visitors always see content, even if a page has not been translated yet.

## Test your fallback configuration

1. Clear all caches as explained in [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
2. Open your website's frontend in a new browser tab.
3. Navigate to a page that has **not** been translated into your secondary language by adding the language prefix to the URL (for example `/de/`).
4. Verify the behavior:
   * With "Fallback to other language", the page should show the fallback language content.
   * With "Strict", you should see a 404 error page.
   * With "Free mode", you should see only content explicitly created for that language.

## Change the fallback type for an existing language

1. Open your site configuration as described above.
2. In the **Languages** tab, click on the language you want to change.
3. Change the **Fallback Type** dropdown to your preferred option.
4. Adjust the **Fallback Language IDs** if needed.
5. Click **Save**.
6. Clear all caches and test in the frontend.

## Summary

Congratulations! You now understand the three language fallback types in TYPO3 and have configured fallback behavior for your site. Untranslated pages remain accessible according to your chosen strategy.

## Next steps

Now that you have configured language fallbacks, you might like to:

* [Translate existing content](TranslateContent.md) to reduce the need for fallbacks
* [Configure additional content languages](ConfigureContentlanguages.md) for more languages
* Add a language switcher to your frontend that indicates which pages are translated

## Resources

* [Site languages](https://docs.typo3.org/permalink/t3coreapi:sitehandling-addingLanguages)
* [Working with languages](https://docs.typo3.org/permalink/t3coreapi:languages)
