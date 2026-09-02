# Changelog

Every released version of S.A.M Sniper, newest first. Each entry is one line.

Versions are `MAJOR.MINOR.PATCH`. A **patch** release fixes things without
changing how anything is used, a **minor** release adds features, and a
**major** release changes something you would have to relearn.

## [Unreleased]

_Nothing yet._

## [1.0.5] - 2026-09-01

### Added

- **Cancel a running search.** RETRIEVE turns into CANCEL while a search is
  going. It stops between pages, so it can take a moment on a slow reply, and
  nothing is saved or emailed.
- `File > Open exports folder`, so you can get to your reports without running
  a search first.
- `File > Settings > Forget saved settings...`, which clears the stored API
  key, mail password, address, filters and saved searches from this computer.
  Exported reports are left alone.

### Changed

- **The startup key check no longer spends a request on every launch.** It is
  reused for six hours instead. On a non-federal key that is the difference
  between five launches costing five of your ten daily requests and costing
  one. A failed check is never reused, changing your key discards it, and
  TRY AGAIN always asks SAM.gov again.

### Fixed

- The window can now be made small enough for a 1366x768 laptop. Its minimum
  height used to be taller than such a screen, which pushed CONTINUE and
  RETRIEVE below the bottom edge where they could not be clicked. Get Set Up
  scrolls now, as the search screen already did.

## [1.0.4] - 2026-09-01

### Changed

- Updates install silently. The app closes, installs in the background and
  reopens itself - no setup wizard, no pages to click through, and no licence
  page. You still confirm once, in the app, before anything is downloaded.

## [1.0.3] - 2026-09-01

### Fixed

- Updating no longer ends in "Security validation failure: parent process has
  different executable!". The running app was passing its own private
  PyInstaller markers down to the installer, which handed them to the freshly
  installed copy it relaunched; that copy then believed it had been started by
  something it had not. Both sides now clear them.
- Updating no longer asks you to accept the Terms of Use again. The setup
  wizard skips its licence page when you have already accepted the current
  Terms, and the Terms now carry their own version number rather than the
  application's - so a patch release cannot make them look changed when they
  are not. You will be asked again only if the wording actually changes.

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
[1.0.5]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.5
[1.0.4]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.4
[1.0.3]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.3
[1.0.2]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.2
[1.0.1]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.1
