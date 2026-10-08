# Disparités i18n — core-contenthandler_text_translation

- Dépôt : `pankosmia/core-contenthandler_text_translation`
- Branche analysée : `dev` (commit `a37a551284b0b671db306c69ab0006372663deba`)
- Fichier i18n : `pankosmia_metadata.json` (clé `i18n`, 101 entrées) — le fichier s'appelle `pankosmia_metadata.json` et non `metadata.json`
- Code analysé : tous les fichiers `src/**/*.js` et `src/**/*.jsx` (appels `doI18n`). Lecture seule, rien n'a été modifié dans l'organisation.
- Préfixe des clés de ce dépôt : `pages:core-contenthandler_text_translation:<clé>`

## 1. Entrées i18n orphelines (présentes dans le metadata, jamais appelées par `doI18n`) — 37

1. `title`
2. `summary`
3. `import_local_book`
4. `pick_one_book_export`
5. `export_zip`
6. `export_usfm`
7. `export_pdf`
8. `book_code`
9. `book_abbr`
10. `book_title`
11. `add_versification_checkbox`
12. `protestant_books_only`
13. `import`
14. `lang_code`
15. `lang_name`
16. `new_translation_text`
17. `lang_code_bcp47_list`
18. `lang_code_burrito`
19. `lang_code_custom_language`
20. `description_bcp47_list`
21. `description_lang_code_burrito`
22. `description_custom_language`
23. `local_resource`
24. `local_project`
25. `burrito_resources`
26. `choose_language`
27. `helper_language_code`
28. `document`
29. `title_section_burrito`
30. `back_button`
31. `next_button`
32. `delete_book`
33. `book_deleted`
34. `book_delete_error`
35. `delete_button`
36. `no_book`
37. `pick_book_format`

Remarques :
- `title` et `summary` sont des champs standards du metadata (probablement lus par l'application hôte, pas via `doI18n`) : à confirmer.
- Aucun appel dynamique n'utilise le préfixe de ce dépôt (les appels dynamiques trouvés concernent `scripture:books:*`, `scripture:versifications:*` et les `menuSpecs`, tous hors de ce dépôt).

## 2. Clés appelées par `doI18n` avec le préfixe de ce dépôt mais absentes du metadata — 3

| Clé | Fichier:ligne |
|---|---|
| `pages:core-contenthandler_text_translation:select_books` | `src/TextTranslationContent/ContentZip.jsx:98` |
| `pages:core-contenthandler_text_translation:no_usfm_id_found` | `src/pages/Import/UsfmImport.jsx:131` |
| `pages:core-contenthandler_text_translation:bad_usfm_id_line` | `src/pages/Import/UsfmImport.jsx:142` |

## 3. Clés appelées avec le préfixe d'un autre dépôt / espace de noms (non définies ici, à vérifier ailleurs)

Ces clés ne sont pas dans le metadata de ce dépôt ; elles sont probablement fournies par d'autres dépôts (`core-content`, `core-local-workspace`, etc.). Je n'ai pas vérifié ces dépôts.

| Clé | Fichier:ligne |
|---|---|
| `pages:content:books` | `src/pages/Export/ZipExport.jsx:198`, `:222` |
| `pages:content:books_selected` | `src/pages/Export/UsfmExport.jsx:166` |
| `pages:content:cancel` | `UsfmExport.jsx:207`, `PdfGenerate.jsx:915`, `ZipExport.jsx:264` |
| `pages:content:contents` | `src/pages/Export/ZipExport.jsx:66` |
| `pages:content:could_not_fetch` | `src/components/textTranslationMuncher/muncher/Helpers/components/PreviewText.jsx:69` |
| `pages:content:print` | `PreviewText.jsx:161` |
| `pages:content:saved` | `UsfmExport.jsx:69`, `ZipExport.jsx:66` |
| `pages:content:to_download_folder` | `UsfmExport.jsx:69`, `ZipExport.jsx:66` |
| `pages:core-contenthandler_bcv:book` | `src/components/textTranslationMuncher/wrapperMuncher/BcvPicker.jsx:71` |
| `pages:core-contenthandler_juxta:error` | `src/components/textTranslationMuncher/wrapperMuncher/BurritoSelect.jsx:15` |
| `pages:core-contenthandler_translation_plan:error` | `BcvPicker.jsx:43` |
| `pages:core-translation_plan:error` | `src/pages/MuncherTest.jsx:43` |
| `pages:core-local-workspace:book` | `src/components/textTranslationMuncher/muncher/Helpers/components/BookPicker.jsx:48` |
| `pages:core-local-workspace:button_edit_layout` | `EditorTools.jsx:166` |
| `pages:core-local-workspace:pdf_preview` | `PreviewText.jsx:350` |
| `pages:core-local-workspace:print` | `PreviewText.jsx:328` |
| `pages:core-local-workspace:save_error` | `src/components/textTranslationMuncher/muncher/Helpers/components/SaveButton.jsx:48` |
| `pages:core-local-workspace:saved` | `SaveButton.jsx:41` |
| `pages:core-local-workspace:usfm_error` | `src/components/textTranslationMuncher/muncher/Editor/TextTranslationEditorMuncher.jsx:189` |
| `scripture:books:${…}` (dynamique) | `BcvPicker.jsx:84`, `BookPicker.jsx:62`, `UsfmExport.jsx:193`, `PdfGenerate.jsx:643,653`, `ZipExport.jsx:205,229` |
| `scripture:versifications:${listItem}` (dynamique) | `src/TextTranslationContent/ContentZip.jsx:83` |
| `t[1]` / `t[2]` (dynamique, `EditableTag.jsx:63,85,97`) | valeurs issues de `menuSpecs/*.json`, toutes de la forme `pages:core-local-workspace:*` |

## 4. Points à signaler

- `BurritoSelect.jsx` et `MuncherTest.jsx` appellent `doI18n` sans l'importer depuis `pankosmia-lib/i18n` (vérifié dans l'import des fichiers) : bug potentiel (`ReferenceError`).
