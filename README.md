# Locale Tool for JSON

An online inspect/export tool for Vue i18n JSON locale files.

## Features

- View key/value list for a JSON locale file.
- Show differences between two JSON locale files.
- Export added/updated terms from current file as JSON for translator.
- Merge added/updated terms into previous file and export as JSON for developer.
- Delete removed terms from previous file and export as JSON for developer.

## Toturials

### Incremental translation

1. Load LAST_VER baseline `en.json` as previous, and CURR_VER `en.json` as current.
2. Export `Different` as `exported.json`, and submit to translator.
3. Load CURR_VER `zh.json` as previous, and `exported_zh.json` from translator as current.
4. Export `Merged` as `zh.json`, and replace it.
5. Repeat step 3-4 for rest locale files.

### Merge with none key/value datasheet

1. Load baseline `en.json` both as previous and current.
2. __Do check__ `Flat Keys` in settings.
3. Export `Cleaned` as `exported.json`.
4. __Only keep__ the keys(left value null) from datasheet `en.xlsx`, and remove the rest key/value.
5. Save `exported.json` as `exported_en.json` and fill in values from datasheet.
6. Load `en.json` as previous, and `exported_en.json` as current.
7. Export `Merged` as `en.json`, and replace it.
8. Repeat step 5-7 for rest  locale files.

### Margin with baseline

1. Load baseline locale `en.json` as current.
2. __Do check__ `Skip Updated` in settings.
3. Load margin locale `zh.json` as previous.
4. Export `Cleaned` as `zh.json` and replace it.
5. Repeat step 3-4 for rest locale files.

## Settings

### Display

- English UI: Show page in English or Chinese.
- File Info: Show extra info from locale files.
- Label Special: Highlight null value for previous, and plurals/variables for current.
- Terms: show/hide same/added/removed/updated terms.
- List: show/hide key/value for previous/current locales.

### Export

- Flat Keys: Treat JSON key as flatten string(eg., `common.action.submit`).
- Skip Update: Only process added terms for different/merged.
- Delete Empty: Delete null keys for merged/cleaned.

## More

- Single html to work, dependencies load over CDN.
- Responsive layout adaption for tablet/mobile.
- Auto switch to Chinese based on browser(`navigator.languages`).

## CHANGELOG

### 2022-12-01

- #fix delete null keys

### 2022-11-29

- +adapt for mobile

### 2022-11-25

- +delete null keys
- +highlight null values

### 2022-11-24

- +auto show zh ui
- +highlight plurals/variables values
- #rename page
- #minor tweaks

### 2022-11-23

- +initial commit with compare/export
