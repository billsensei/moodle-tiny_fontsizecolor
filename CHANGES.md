# Changes in the latest version

What changed or was added since the previous version of `tiny_fontsizecolor`. The full history is in [changelog.md](changelog.md).

## 1.2.3

- Fixed the colour list editor in the admin settings: a new colour row with a label but no colour was saved as `|Label` and rejected with an "invalid entries" error. Such a row is now ignored, like an empty size row.
