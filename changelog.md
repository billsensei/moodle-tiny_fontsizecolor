# Changelog

All notable changes to `tiny_fontsizecolor`, newest first. Add an entry here with every new version. `CHANGES.md` holds only the latest version.

## 1.3.0

- Font family: a new **Font family** toolbar button and Format menu entry apply a font to the selected text (as a `font-family` style). The current font is ticked, and **Default font** removes it again.
- New admin setting *Font families*: each font has a label and a list of up to 10 font names, such as `Arial, Helvetica, sans-serif`. The row editor (and the plain text fallback, `Label|font names` per line) works like the size and colour lists. The default list has eight web-safe fonts: Arial, Verdana, Tahoma, Trebuchet MS, Times New Roman, Georgia, Courier New and Comic Sans MS.
- The font list is validated on the server when saved and again before it reaches the editor and in the browser: only plain font names (letters, digits, spaces, `.`, `_`, `-`) are accepted, so brackets, semicolons or `url()` cannot be injected into the content. Names with spaces are saved in single quotes, generic families (`serif`, `sans-serif`, ...) are left bare, and a font list can only be used once.
- Fonts are not loaded by the plugin, so they only show for readers who have them installed. End each list with a generic family.
- Largest font size raised from 72pt to 200pt (`fontlist::MAX_FONTSIZE`), for the size list, the admin editor and the **Custom size...** dialog. Existing size lists are kept, and the default list (8 to 12) is unchanged.
- New lang strings: `addfont`, `button_fontfamily`, `fontfamilies`, `fontfamilies_desc`, `fontlabel`, `fontstack`, `menuitem_fontfamily` and `resetfont`; `error_duplicates` now says "entry".
- Tests: new PHPUnit tests for font stacks, font lists and the setting; the size tests use 200; a new Behat scenario for the font menu.
- Release workflow: a GitHub Actions workflow (`moodle-release.yml`) sends each pushed `v*` tag to the Moodle plugins directory, and needs the repository secret `MARKETPLACE_TOKEN`. The Marketplace keeps only the first 128 characters of the release notes, so the workflow sends the one line of `CHANGES.md` that starts with `Marketplace summary: ` (at most 128 characters) and stops with an error if it is missing or too long. Add that line with every version.

## 1.2.5

- Minimum Moodle version: `$plugin->requires` is now 2025100600 (Moodle 5.1), matching `$plugin->supported = [501, 503]`, the marketplace listing and the README (it said Moodle 4.1 before). Moodle 4.1 to 5.0 are no longer declared as supported.
- Release zip: a GitHub Actions workflow (`release-zip.yml`) now builds `tiny_fontsizecolor_<version>.zip` with `git archive --prefix=fontsizecolor/` and attaches it to the release when a `v*` tag is pushed, so the installable zip always has the single root folder Moodle requires. The README says to use that zip, not GitHub's *Download ZIP* or *Source code* archives (root folder rejected with `rootinvalid`).
- `composer.json` homepage and support URLs now use the renamed repository `moodle-tiny_fontsizecolor`.

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
