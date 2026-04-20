# Translate Existing Content

<!--#TYPO3v13 #Beginner #Backend #Translation #Languages @username -->

Once you have configured additional languages in your TYPO3 site, you can start translating existing content into those languages. TYPO3 provides a built-in translation workflow that lets you create translated versions of content elements directly in the Page module.
Each translation is linked to the original content element in the default language, making it easy to keep track of which elements have been translated and which still need attention.

## Learning objective

In this step-by-step guide you will translate existing content elements on a page into a different language using the TYPO3 Page module.

## Prerequisites

### Tools and technology

* A computer with a local TYPO3 installation
* Access to the TYPO3 backend (admin account or a user with permission to translate content)
* A web browser
* At least one additional language configured in your site configuration

### Knowledge and skills

* You know how to [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
* You know how to [Configure additional content languages](ConfigureContentlanguages.md).
* You know how to [Clear all caches](ClearingAllCachesUsingTheClearCacheMenu.md).

## Switch to the translation view

1. Log in to the TYPO3 backend as explained in [Log in to the TYPO3 backend](LogInToTheTypo3Backend.md).
2. In the left-hand module menu, navigate to **Web > Page**.
3. Select the page that contains the content you want to translate.
4. At the top of the page module, click the **Languages** dropdown and select the language you want to translate into, for example "Deutsch".

## Translate all content elements at once

If the page has not been translated yet, TYPO3 shows a translation wizard:

1. Click the **Translate** button that appears in the content area. A dialog opens with two options:
   * **Translate** creates connected translations that stay linked to the original content. Changes to the original structure are reflected in the translation.
   * **Copy** creates independent copies of the content in the target language. The copies are not linked to the original.
2. Select **Translate** for most use cases.
3. TYPO3 creates translation records for all content elements on the page. Each translated element opens in a form where you can enter the translated text.

> [!NOTE]
> The "Translate" option is recommended because it maintains a link between the original and the translation. This makes it easier to identify outdated translations when the original content changes.

## Translate a single content element

If translations already exist and you want to translate a specific element:

1. Make sure you are viewing the target language in the Page module.
2. Find the content element that shows the original language text with a note that no translation exists yet.
3. Click the **Translate** button on that specific content element.
4. A new form opens with the original content visible as reference. Enter the translated text in the corresponding fields.
5. Click **Save** at the top of the form.

## Edit an existing translation

1. In the Page module, select the target language from the **Languages** dropdown.
2. Click the pencil icon on the translated content element you want to edit.
3. Update the translated text in the form. The original content is displayed as reference on the right side.
4. Click **Save**.

> [!TIP]
> If you want to see all languages side by side, select **All languages** from the Languages dropdown. This gives you an overview of which elements have been translated and which are still missing.

## Verify the translation

1. Clear the frontend cache by following [Clearing All Caches Using the Clear Cache Menu](ClearingAllCachesUsingTheClearCacheMenu.md).
2. Open your website's frontend in a new browser tab.
3. Navigate to the translated version of the page by adding the language prefix to the URL (for example `/de/` for German).
4. Verify that the translated content appears correctly.

## Summary

Congratulations! You have translated existing content elements into another language using the TYPO3 Page module. You know how to use the translation wizard for bulk translations and how to translate or edit individual content elements.

## Next steps

Now that you can translate content, you might like to:

* [Configure additional content languages](ConfigureContentlanguages.md) to support more languages
* Add a language switcher to your frontend template so visitors can switch between languages
* Explore the translation overview in **Web > List** to see translation status across multiple pages

## Resources

* [Working with languages](https://docs.typo3.org/permalink/t3coreapi:languages)
* [Translation handling](https://docs.typo3.org/permalink/t3coreapi:internationalization)
