# Changelog

Every released version of S.A.M Sniper, newest first. Each entry is one line.

Versions are `MAJOR.MINOR.PATCH`. A **patch** release fixes things without
changing how anything is used, a **minor** release adds features, and a
**major** release changes something you would have to relearn.

## [Unreleased]

_Nothing yet._

## [1.0.2] - 2026-09-01

### Fixed

- Switching between light and dark mode no longer clears the Get Set Up form.
  The API key, results address and app password you had typed are kept.
- Switching theme no longer resets your search. Keywords, codes, states, the
  date window and the new-since-last-run tick all survive, and a search you had
  edited is no longer reverted to the last saved version.
- Switching theme while looking at your results no longer closes them with an
  unexpected-error message.
- The VALID / FAILED marks on the Running checks screen now repaint when you
  change theme, instead of staying in the previous theme's colours.

## [1.0.1] - 2026-09-01

First public release. Version 1.0.0 was built and tested but never published,
so its changes are folded in here.

### Added

- Automatic update checking. The Running checks screen gains a **Checking for
  updates** row; a newer release is downloaded, checksum-verified, and offered
  for install. Turn it off in `File > Settings`, or check on demand with
  `File > Check for updates...`.
- **Only notices new since the last run** tick box on the search screen, which
  narrows a report to opportunities that have not been emailed before.

### Fixed

- Yahoo mail delivery. The encryption mode is now taken from the port rather
  than a separate setting, so port 465 correctly uses SSL instead of hanging on
  a STARTTLS attempt. Also fixes any account whose port and encryption setting
  had drifted apart.
- The Query Summary sheet reported a "Searched in" scope built from settings
  the search never applied, so a report could claim to have searched attachment
  names when nothing does. It now states what was actually searched.
- The diagnostic logged when a query hits the 60-page limit printed the page
  offset where it said the record total.

### Internal

- Update feed moved to this public repository, so the app can check for new
  versions without shipping a credential.
- `python tests/test_core.py` ran only 79 of the test suite and still reported
  success; it now runs all of it.
- `build_installer.bat` failed to find Inno Setup when it was installed
  per-user rather than into Program Files.
- Removed the superseded PowerShell installer and two stale module docstrings.

[Unreleased]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases
[1.0.2]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.2
[1.0.1]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.1
