# Locale Tool for JSON

An online inspect/export tool for [Vue i18n](https://github.com/intlify/vue-i18n-next) JSON locale file.  
Auto merge incremental translations, and more. [CHANGELOG](CHANGELOG.md) | [中文文档](README_zh.md)

## Features

- __View:__ Display key/value in the table for a JSON locale file.
- __Compare:__ Show term changes between two JSON locale files.
- __Differ:__ Export added/updated terms from the current file as JSON for translators.
- __Merge:__ Merge added/updated terms into the previous file and export as JSON for developers.
- __Clean:__ Delete removed terms from the previous file and export as JSON for developers.
- __Swap:__ Show terms with different keys but the same value.
- __Reset:__ Clear previous/current data on the page, settings remain.

## Tutorials

### Incremental translation

The main scenario for version-based translation workflow, and supports communication between developers and translators.

1. Import LAST_VER baseline `en.json` as previous, and CURR_VER `en.json` as current.
2. Export *Different* as `exported.json`, and submit to translators.
3. Import CURR_VER `zh.json` as previous, and `exported_zh.json` from translator as current.
4. Export *Merged* as `zh.json`, and replace it.
5. Repeat steps 3-4 for the rest locale files.

### Margin with baseline

To eliminate differences between current translation and baseline language.

1. Import baseline locale `en.json` as current.
2. __Do check__ *Skip Updated* in settings.
3. Import margin locale `zh.json` as previous.
4. Export *Cleaned* as `zh.json` and replace it.
5. Repeat steps 3-4 for the rest locale files.

### Merge with none key/value datasheet

How to benefit from this tool with pure translations by hand.

1. Import baseline `en.json` both as previous and current.
2. __Do check__ *Flat Keys* in settings.
3. Export *Cleaned* as `exported.json`.
4. __Only keep__ the keys(left value as null) from datasheet `en.xlsx`, and remove the rest key/value.
5. Save filtered `exported.json` as `exported_en.json` and fill in values from the datasheet.
6. Import `en.json` as previous, and `exported_en.json` as current.
7. Export *Merged* as `en.json`, and replace it.
8. Repeat steps 5-7 for the rest locale files.

## Settings

### Display

- __English UI:__ Show the page in English or Chinese.
- __File Info:__ Show extra info from locale files.
- __Label Special:__ Highlight null value for previous, and plurals/variables/links for current.
  - Plural: `Cat | Cats` (regexp `/\|/g`).
  - Variable: `Hello {name}!` (regexp `/{[^'\s]+}/g`).
  - Link: `Welcome to @:title{''}!` (regexp `/@:\S+{''}/g`).
- __Terms Checks:__ Show/hide same/added/removed/updated terms.
- __Table Checks:__ Show/hide key/value for previous/current locales.

### Export

- __Use Code:__ Import/export code other than JSON file. (Default: *No*, with a dialog)
- __Flat Keys:__ Treat the JSON key as a flattened string, rather than a nested object. (Default: *Yes*, eg., `common.action.submit`)
- __Including Update:__ Including updated terms during export different/merged. (Default: *Yes*)
- __Including Empty:__ Keep/delete null keys during export merged/cleaned. (Default: *No*)
- __Including Swapped:__ Including swapped keys during export different. (Default: *No*)

## Notes

- __Same:__ Both previous and current locale files have this key, and have identical values.
- __Updated:__ Both previous and current locale files have this key, but have different values.
- __Added:__ Current locale file has this key, but the previous one does not.
- __Removed:__ Current locale file does not have this key, but the previous one does.
- __Changed:__ Including *Added*, *Updated*, and *Removed*.
- __Total:__ Including *Same* and *Changed*.

## More

- Only need one single HTML to work, dependencies are loaded over CDN.
- Responsive layout adaption ready for tablet/mobile.
- Auto switch to Chinese based on browser setting(`navigator.languages`).
- Exported JSON file is encoded in `UTF-8 with BOM`.
