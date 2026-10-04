# Bindia Admin for Windows

Download the [latest Windows release](https://github.com/satalways/bindia-admin-app/releases/latest).

This repository contains compiled distribution files. The application source is maintained separately in a private repository.

## Downloads

Version **0.1.1**, Windows x64:

- [Windows installer](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.1/Bindia.Admin_0.1.1_x64-setup.exe) — recommended; installs for the current user and sets up WebView2 when needed.
- [Standalone executable](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.1/bindia-admin-desktop.exe) — requires Microsoft Edge WebView2 Runtime already installed.
- [SHA-256 checksums](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.1/SHA256SUMS.txt).

The same files are stored in [builds/windows/v0.1.1](builds/windows/v0.1.1). Previous versions remain in their own directories and releases.

## Using the app

Bindia Admin opens maximized and selects production by default. Sign in using your Bindia admin account; production uses two-factor authentication. Your saved server selection is preserved.

Closing the window keeps the app running in the background. Click the Bindia icon in the Windows system tray beside the clock to reopen it, or right-click it and choose **Open Bindia Admin**. Choose **Exit** to quit completely. Windows may place the icon inside its hidden-icons menu. Opening the app again restores the existing instance.

From version 0.1.1, the app checks this repository's latest release at startup and every six hours. It announces a newer stable Windows version with a download button. You can also use **Settings → Check for updates**. Download the installer, exit the running app using the tray menu, and run the installer. Existing 0.1.0 installations need this first upgrade manually.

## Verify a download

Compare the result of this PowerShell command with `SHA256SUMS.txt`:

```powershell
Get-FileHash -LiteralPath '.\Bindia.Admin_0.1.1_x64-setup.exe' -Algorithm SHA256
```

Only installers, compiled executables, checksums, and distribution documentation belong in this repository. Keep previous releases in their version directories.
