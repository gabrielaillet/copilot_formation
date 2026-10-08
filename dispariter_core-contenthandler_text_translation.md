# Disparités i18n — core-contenthandler_text_translation

- Dépôt analysé : `Pankosmia/core-contenthandler_text_translation` (lecture seule, commit `00079b9c09fb520989be47f8351f2f2cbcca05a3`)
- Fichier i18n : `pankosmia_metadata.json` (section `i18n`, 97 clés). Le fichier `metadata.json` n'existe pas dans ce dépôt.
- Code analysé : tous les `.js`/`.jsx` de `src/` (135 occurrences de `doI18n(`).
- Format d'une clé appelée : `pages:core-contenthandler_text_translation:<clé>`.

## 1. Entrées orphelines (présentes dans le JSON, jamais appelées par `doI18n`)

32 clés sur 97 (65 utilisées).

| # | Clé | Remarque |
|---|-----|----------|
| 1 | `title` | Clé de métadonnées du dépôt (non appelée via `doI18n` dans `src/`). |
| 2 | `summary` | Clé de métadonnées du dépôt (non appelée via `doI18n` dans `src/`). |
| 3 | `import_local_book` |  |
| 4 | `pick_one_book_export` |  |
| 5 | `export_zip` |  |
| 6 | `export_usfm` |  |
| 7 | `export_pdf` |  |
| 8 | `book_abbr` |  |
| 9 | `book_title` |  |
| 10 | `add_versification_checkbox` |  |
| 11 | `protestant_books_only` |  |
| 12 | `import` |  |
| 13 | `lang_code` |  |
| 14 | `lang_name` |  |
| 15 | `new_translation_text` | Non appelée via `doI18n`, mais utilisée comme `label` de l'endpoint `create_document` dans `pankosmia_metadata.json` (`pages:core-contenthandler_text_translation:new_translation_text`). |
| 16 | `lang_code_bcp47_list` |  |
| 17 | `lang_code_burrito` |  |
| 18 | `lang_code_custom_language` |  |
| 19 | `description_bcp47_list` |  |
| 20 | `description_lang_code_burrito` |  |
| 21 | `description_custom_language` |  |
| 22 | `local_resource` |  |
| 23 | `local_project` |  |
| 24 | `burrito_resources` |  |
| 25 | `choose_language` |  |
| 26 | `helper_language_code` |  |
| 27 | `document` |  |
| 28 | `title_section_burrito` |  |
| 29 | `back_button` |  |
| 30 | `next_button` |  |
| 31 | `no_book` |  |
| 32 | `pick_book_format` |  |

## 2. Entrées appelées par `doI18n` mais absentes du `i18n` du dépôt

### 2.1 Même espace de noms (`pages:core-contenthandler_text_translation:`)

| Clé appelée | Fichier |
|-------------|---------|
| `pages:core-contenthandler_text_translation:select_books` | `src/TextTranslationContent/ContentZip.jsx:98` |

### 2.2 Autres espaces de noms (clés définies hors de ce dépôt)

| Clé appelée | Fichier(s) |
|-------------|-----------|
| `pages:content:about_document` | `src/pages/AboutRepo.jsx:97` |
| `pages:content:about_repo_dateUdapted` | `src/pages/AboutRepo.jsx:144` |
| `pages:content:about_repo_flavor` | `src/pages/AboutRepo.jsx:135` |
| `pages:content:about_repo_language-code` | `src/pages/AboutRepo.jsx:138` |
| `pages:content:about_repo_language-name` | `src/pages/AboutRepo.jsx:141` |
| `pages:content:book_or_books` | `src/pages/AboutRepo.jsx:147` |
| `pages:content:books` | `src/pages/Export/ZipExport.jsx:203`, `src/pages/Export/ZipExport.jsx:227` |
| `pages:content:books_selected` | `src/pages/Export/UsfmExport.jsx:167` |
| `pages:content:cancel` | `src/pages/Export/PdfGenerate.jsx:913`, `src/pages/Export/UsfmExport.jsx:208`, `src/pages/Export/ZipExport.jsx:269` |
| `pages:content:close` | `src/pages/AboutRepo.jsx:158` |
| `pages:content:contents` | `src/pages/Export/ZipExport.jsx:71` |
| `pages:content:local_project` | `src/pages/AboutRepo.jsx:64` |
| `pages:content:local_resource` | `src/pages/AboutRepo.jsx:63` |
| `pages:content:saved` | `src/pages/Export/UsfmExport.jsx:69`, `src/pages/Export/ZipExport.jsx:71` |
| `pages:content:to_download_folder` | `src/pages/Export/UsfmExport.jsx:69`, `src/pages/Export/ZipExport.jsx:71` |

### 2.3 Clés dynamiques (non vérifiables statiquement)

| Expression | Fichier |
|-----------|---------|
| `` `scripture:versifications:${listItem}` `` | `src/TextTranslationContent/ContentZip.jsx:82` |
| `` `scripture:books:${listItem}` `` | `src/pages/DeleteTextTranslationBook.jsx:171` |
| `repoInfo.source` | `src/pages/AboutRepo.jsx:97` |
| `` `scripture:books:${bookName}` `` | `src/pages/Export/UsfmExport.jsx:194` |
| `` `scripture:books:${selected}` `` / `${bookName}` | `src/pages/Export/PdfGenerate.jsx:641, 651` |
| `` `scripture:books:${s}` `` / `${bookName}` | `src/pages/Export/ZipExport.jsx:210, 234` |

## Points à confirmer
1. Les clés des sections 2.2 et 2.3 appartiennent à d'autres dépôts (`pages:content:*`, `scripture:*`, `pages:core-dashboard:title`) : faut-il les compter comme « absentes » ? Elles sont listées par transparence.
2. `new_translation_text` est référencée dans les `label` des endpoints du JSON : doit-elle être considérée orpheline (définition stricte « `doI18n` seulement ») ? Elle est listée comme orpheline avec remarque.
