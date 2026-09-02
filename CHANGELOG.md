# Changelog

Every released version of S.A.M Sniper, newest first. Each entry is one line.

Versions are `MAJOR.MINOR.PATCH`. A **patch** release fixes things without
changing how anything is used, a **minor** release adds features, and a
**major** release changes something you would have to relearn.

## [Unreleased]

_Nothing yet._

## [1.3.0] - 2026-09-02

### Added

- **An Overview screen**, and it is where the app now opens. It shows how much
  of today's SAM.gov allowance is left, how much has been used over the last
  seven days, what your last search matched and how much of that was new, when
  the next scheduled run is, and the last five runs including any that failed.
  Nothing on it is estimated; where a figure is a guess, it says so.
- **Every search is now remembered** - what it matched, how much was new, and
  whether it finished. That survives closing the app, which is what lets the
  Overview tell you anything on opening.

### Changed

- **A new look.** Dark or light, rounded cards and buttons, a green accent, and
  a title bar that matches the rest of the window instead of staying white.
- **The menu bar is gone**, replaced by a navigation column down the left with
  everything the File menu held, visible without opening anything. It stays out
  of the way during first-time setup, which is a straight line with one way
  forward.
- Screen headings are no longer in capitals.
- The results table lays its columns out from the width it is actually given,
  so the Deadline column cannot be pushed off the edge at any window size.
- The results table now sits in a card rather than a box inside a box.

### Fixed

- **The window icon and the logo were missing** when running from source, after
  the code was reorganised in 1.2.0. The installed application was never
  affected, but three tests now cover it.

## [1.2.0] - 2026-09-02

### Changed

- **The interface is finished.** Scrollbars, tickboxes, dropdown arrows and the
  ring around a selected box were still being drawn by Windows in its own grey
  and blue; they now match the rest of the application, in both light and dark.
- **Tickboxes show a tick.** They used to show a small cross, which reads as a
  refusal on a box whose job is to turn something on.
- **Dialogs open over the window you opened them from**, centred, instead of
  wherever Windows decided to put them - which on a second monitor was often
  not the screen you were looking at. They are also a consistent size.
- Every page now lines up with every other. The margin was six pixels wider on
  two of the five screens, so headings shifted sideways as you moved through.
- The checks screen numbered its block 4, the same as the last block of Get Set
  Up. It is 5.

### Fixed

- **Email settings was cutting off its last two fields.** The Port box and the
  STARTTLS tickbox were below the bottom of the window with no way to reach
  them. The form scrolls now.
- **The results table stopped clipping.** "Total Small Business" and "DEPT OF
  VETERANS AFFAIRS" were both cut short.
- New notices in the table are marked with a tint rather than filled solid, so
  a result set that is mostly new no longer looks entirely selected, and the
  rows alternate shade to make a wide table easier to follow.
- On an installation you do not have permission to write to, the reports and
  the cache now fall back to your home folder, as the settings file already
  did. The two disagreed, and only one of them coped.

## [1.1.1] - 2026-09-02

### Fixed

- **The line under RESULTS was cut off at the start.** With a long status it
  grew wider than the window and spilled off both edges, so "Retrieval - Fail:
  ..." appeared as "eval - Fail: ...". It now wraps, and re-wraps as you resize.
- **The Deadline column fell off the right of the results table**, with no way
  to scroll to it - the one column the table is sorted by. The columns now fit
  the window, and Title and Agency stretch into any extra width.

## [1.1.0] - 2026-09-02

### Changed

- **The requests-left figure now comes from SAM.gov, not from counting.**
  SAM.gov reports how many requests remain on every single response, and the
  app now reads and shows that. Counting locally could never be right: the same
  key used on another computer, or by anything else, spends the same allowance
  without this app seeing any of it. When the real figure is known the word
  "about" disappears, because it is no longer a guess.
- The real daily limit is taken from SAM.gov too, rather than assumed from the
  account type.

### Fixed

- **A search that ran out of allowance left the counter claiming requests were
  left.** The status line would say the allowance was used up while the corner
  of the screen still offered six - only the startup check reacted to a refusal,
  and searches did not.

## [1.0.9] - 2026-09-02

### Fixed

- **The request counter now agrees with SAM.gov.** Two things were wrong. The
  check made on every launch to verify your key spends a real request, and the
  counter never saw it - so it under-reported by one per launch. And the count
  rolled over at local midnight while SAM.gov's allowance resets at midnight
  UTC, so for the seven hours between the two it reported the previous day's
  usage against an allowance that had already refilled.
- The counter now also says **when the allowance comes back** in your own time,
  because midnight UTC lands mid-afternoon or evening locally and is not the
  midnight anyone would assume.
- When SAM.gov reports the allowance exhausted, the counter shows none left
  rather than whatever this computer happened to have counted - the same key
  used anywhere else spends the same allowance.

## [1.0.8] - 2026-09-01

### Changed

- **One update window, however you get to it.** `File > Check for updates...`
  used to open a different dialog from the one the startup check uses. Both now
  show the same window, with links to the release notes and to skip a version
  you would rather not take.

## [1.0.7] - 2026-09-01

### Added

- **Updates now show a progress window** instead of happening invisibly. It
  carries the S.A.M Sniper mark and name, a percentage, and a line saying what
  is going on - downloading, checking the download, installing. It stays on
  screen through the install and closes itself when the new version takes
  over, so the app is never simply gone for half a minute with nothing to
  explain it. If something fails, the window says so rather than vanishing.

## [1.0.6] - 2026-09-01

### Fixed

- **Updating could leave a setup window stuck open for ever.** Setup found the
  app still closing, asked what to do about it, and waited on a dialog a silent
  update has no way to answer - holding its own file locked. Setup now closes
  the app itself instead of asking.
- **A stuck update blocked every update after it.** The installer was always
  saved to the same filename, so a locked leftover could not be replaced. Each
  download is now named for its version, falls back to a fresh name if that one
  is somehow in use, and older ones are tidied up afterwards.
- The failure was reported as a raw `PermissionError`. The cleanup that runs
  when a download fails could itself fail on the locked file, replacing the
  readable message with its own.

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
[1.3.0]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.3.0
[1.2.0]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.2.0
[1.1.1]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.1.1
[1.1.0]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.1.0
[1.0.9]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.9
[1.0.8]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.8
[1.0.7]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.7
[1.0.6]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.6
[1.0.5]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.5
[1.0.4]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.4
[1.0.3]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.3
[1.0.2]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.2
[1.0.1]: https://github.com/NGSolutions-Projects/SAM-Sniper-Releases/releases/tag/v1.0.1
