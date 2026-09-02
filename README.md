# S.A.M Sniper - Releases

Downloads and release notes for **S.A.M Sniper**, a Windows desktop application
that pulls federal contract opportunities from the SAM.gov Get Opportunities
API, filters them, and delivers a formatted Excel + CSV digest by email.

**[Download the latest version](../../releases/latest)**  ·
[What's changed](CHANGELOG.md)

## Installing

Download `SAM_SNIPER_INSTALLER.exe` from the latest release and run it. It
installs for the current user only, so it does not ask for administrator
rights. The installer is not code-signed, so Windows SmartScreen shows a
warning on first run: choose **More info**, then **Run anyway**.

Once installed, the application checks this page about once a day and offers
any newer version to you directly. That check can be turned off in
`File ▸ Settings`.

## Verifying a download

Every release publishes the SHA-256 of its installer in the release notes. To
check a download yourself, in PowerShell:

    Get-FileHash .\SAM_SNIPER_INSTALLER.exe -Algorithm SHA256

The result should match the hash in the release notes. The application performs
this same check automatically and refuses to install anything that does not
match.

## What is in this repository

Nothing but releases. There is no source code here, and there is not meant to
be - this repository exists only so the application can ask, without
credentials, whether a newer version is available.

## Licence

S.A.M Sniper is proprietary software. Copyright (c) Jonathon Ngo and Dana
Winterringer. All rights reserved.

This is **not** open-source software. The binaries published here are licensed
solely under the Terms of Use included with the installer and shown when the
application first runs. No other right or licence is granted, expressly or by
implication. Redistribution is not permitted.

## Support

Report a problem through the channel given to you with your licence. When
reporting, include the application version (`File ▸ About ▸ Summary`) and, if
you can, the log file from the `logs` folder next to the installed
application - credentials are masked in it automatically.
