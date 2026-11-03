# Changes in the latest version

What changed or was added since the previous version of `tiny_fontsizecolor`. The full history is in [changelog.md](changelog.md).

## Unreleased

Marketplace summary: Release workflow now sends a one-line summary, because the Marketplace keeps only 128 characters of the notes.

- Release. The Moodle Marketplace keeps only the first 128 characters of the release notes, so a long entry was shown cut off. `moodle-release.yml` now sends the one line of `CHANGES.md` that starts with `Marketplace summary: ` (at most 128 characters) and stops with an error if it is missing or too long. Add that line with every version.

- Release: a GitHub Actions workflow (`moodle-release.yml`) sends each pushed `v*` tag to the Moodle plugins directory. It needs the repository secret `MARKETPLACE_TOKEN`.

## 1.2.5

- Minimum Moodle version: `$plugin->requires` is now 2025100600 (Moodle 5.1), matching `$plugin->supported = [501, 503]`, the marketplace listing and the README (it said Moodle 4.1 before). Moodle 4.1 to 5.0 are no longer declared as supported.
- Release zip: a GitHub Actions workflow (`release-zip.yml`) now builds `tiny_fontsizecolor_<version>.zip` with `git archive --prefix=fontsizecolor/` and attaches it to the release when a `v*` tag is pushed, so the installable zip always has the single root folder Moodle requires. The README says to use that zip, not GitHub's *Download ZIP* or *Source code* archives (root folder rejected with `rootinvalid`).
- `composer.json` homepage and support URLs now use the renamed repository `moodle-tiny_fontsizecolor`.

