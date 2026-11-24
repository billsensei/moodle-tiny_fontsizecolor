# Changes in the latest version

What changed or was added since the previous version of `tiny_fontsizecolor`. The full history is in [changelog.md](changelog.md).

## 1.3.0

Marketplace summary: Adds a font family picker with an editable font list, and allows font sizes up to 200pt (was 72pt).

- Font family: a new **Font family** toolbar button and Format menu entry apply a font to the selected text (as a `font-family` style). The current font is ticked, and **Default font** removes it again.
- New admin setting *Font families*: each font has a label and a list of up to 10 font names, such as `Arial, Helvetica, sans-serif`. The row editor (and the plain text fallback, `Label|font names` per line) works like the size and colour lists. The default list has eight web-safe fonts: Arial, Verdana, Tahoma, Trebuchet MS, Times New Roman, Georgia, Courier New and Comic Sans MS.
- The font list is validated on the server when saved and again before it reaches the editor and in the browser: only plain font names (letters, digits, spaces, `.`, `_`, `-`) are accepted, so brackets, semicolons or `url()` cannot be injected into the content. Names with spaces are saved in single quotes, generic families (`serif`, `sans-serif`, ...) are left bare, and a font list can only be used once.
- Fonts are not loaded by the plugin, so they only show for readers who have them installed. End each list with a generic family.
- Largest font size raised from 72pt to 200pt (`fontlist::MAX_FONTSIZE`), for the size list, the admin editor and the **Custom size...** dialog. Existing size lists are kept, and the default list (8 to 12) is unchanged.
- New lang strings: `addfont`, `button_fontfamily`, `fontfamilies`, `fontfamilies_desc`, `fontlabel`, `fontstack`, `menuitem_fontfamily` and `resetfont`; `error_duplicates` now says "entry".
- Tests: new PHPUnit tests for font stacks, font lists and the setting; the size tests use 200; a new Behat scenario for the font menu.
- Release workflow: a GitHub Actions workflow (`moodle-release.yml`) sends each pushed `v*` tag to the Moodle plugins directory, and needs the repository secret `MARKETPLACE_TOKEN`. The Marketplace keeps only the first 128 characters of the release notes, so the workflow sends the one line of `CHANGES.md` that starts with `Marketplace summary: ` (at most 128 characters) and stops with an error if it is missing or too long. Add that line with every version.
