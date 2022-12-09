# Locale Tool for JSON

An online inspect/export tool for [Vue i18n](https://github.com/intlify/vue-i18n-next) JSON locale file.
Auto merge incremental translations, and more. [CHANGELOG](CHANGELOG.md) [中文文档](README-zh.md)

## Features

- __View:__ Display key/value in table for a JSON locale file.
- __Compare:__ Show term changes between two JSON locale files.
- __Differ:__ Export added/updated terms from current file as JSON for translator.
- __Merge:__ Merge added/updated terms into previous file and export as JSON for developer.
- __Clean:__ Delete removed terms from previous file and export as JSON for developer.
- __Reset:__ Clear previous/current data on the page, settings remain.

## Notes

- __Same:__ Both previous and current locale files have this key, and have identical value.
- __Updated:__ Both previous and current locale files have this key, but have diffrent value.
- __Added:__ Current locale file has this key, but previous does not.
- __Removed:__ Current locale file does not has this key, but previous does.
- __Changed:__ Including `Added`, `Updated`, and `Removed`.
- __Total:__ Including `Same` and `Changed`

## Toturials

### Incremental translation

1. Load LAST_VER baseline `en.json` as previous, and CURR_VER `en.json` as current.
2. Export `Different` as `exported.json`, and submit to translator.
3. Load CURR_VER `zh.json` as previous, and `exported_zh.json` from translator as current.
4. Export `Merged` as `zh.json`, and replace it.
5. Repeat step 3-4 for rest locale files.

### Margin with baseline

1. Load baseline locale `en.json` as current.
2. __Do check__ `Skip Updated` in settings.
3. Load margin locale `zh.json` as previous.
4. Export `Cleaned` as `zh.json` and replace it.
5. Repeat step 3-4 for rest locale files.

### Merge with none key/value datasheet

1. Load baseline `en.json` both as previous and current.
2. __Do check__ `Flat Keys` in settings.
3. Export `Cleaned` as `exported.json`.
4. __Only keep__ the keys(left value null) from datasheet `en.xlsx`, and remove the rest key/value.
5. Save filtered `exported.json` as `exported_en.json` and fill in values from datasheet.
6. Load `en.json` as previous, and `exported_en.json` as current.
7. Export `Merged` as `en.json`, and replace it.
8. Repeat step 5-7 for rest  locale files.

## Settings

### Display

- __English UI:__ Show page in English or Chinese.
- __File Info:__ Show extra info from locale files.
- __Label Special:__ Highlight null value for previous, and plurals/variables for current.
- __Terms Checks:__ show/hide same/added/removed/updated terms.
- __Table Checks:__ show/hide key/value for previous/current locales.

### Export

- __Flat Keys:__ Treat JSON key as flatten string, rather than nested object. (eg., `common.action.submit`)
- __Skip Update:__ Only process added terms for different/merged.
- __Delete Empty:__ Delete null keys for merged/cleaned.

## More

- Only need single HTML to work, dependencies are loaded over CDN.
- Responsive layout adaption ready for tablet/mobile.
- Auto switch to Chinese based on browser setting(`navigator.languages`).
