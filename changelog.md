# Changelog

All notable changes to `tiny_fontsizecolor`, newest first. Add an entry here with every new version. `CHANGES.md` holds only the latest version.

## 1.2.4

- Added `composer.json` (package `billsensei/moodle-tiny_fontsizecolor`, type `moodle-tiny`) so the plugin can be installed with Composer from Packagist, and a README section on it, including the `public/` path needed on Moodle 5.1 and later. No code changes.

## 1.2.3

- Fixed the colour list editor in the admin settings: a new colour row with a label but no colour was saved as `|Label` and rejected with an "invalid entries" error. Such a row is now ignored, like an empty size row.

## 1.2.2

- Credited the original author, Mikko Haiku, in the file headers and the README. No code changes.

## 1.2.1

- Declared support for Moodle 5.1 to 5.3 and added GitHub CI. Font labels now strip tags (`PARAM_NOTAGS`). Clearer capability name. Rebuilt the AMD module, which was stale.

## 1.2.0

- Added **Default size** and **Remove colour** entries, and ticks showing the current size and colour in the menus. The Cancel and Save buttons of the custom dialogs now use Moodle's translated strings. Added PHPUnit tests for the plugin info, upgrade step and privacy provider, and a Behat test for the menus. PHPUnit tests use attributes instead of `@covers` doc-comments.

## 1.1.0

- Default size list changed from 8-18pt to 8-12pt; custom size and colour dialogs; list editors in the admin settings.
