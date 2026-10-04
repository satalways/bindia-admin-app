# Bindia Admin for Windows

Download the [latest Windows release](https://github.com/satalways/bindia-admin-app/releases/latest).

This repository contains compiled distribution files. The application source is maintained separately in a private repository.

## Downloads

Version **0.1.7**, Windows x64:

- [Windows installer](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.7/Bindia.Admin_0.1.7_x64-setup.exe) — recommended; installs for the current user and sets up WebView2 when needed.
- [Standalone executable](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.7/bindia-admin-desktop.exe) — requires Microsoft Edge WebView2 Runtime already installed.
- [SHA-256 checksums](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.7/SHA256SUMS.txt).

The same files are stored in [builds/windows/v0.1.7](builds/windows/v0.1.7). Previous versions remain in their own directories and releases.

## Using the app

Bindia Admin opens maximized and selects production by default. The left sidebar and top navigation remain visible while the workspace content scrolls. Sign in using your Bindia admin account; production uses two-factor authentication. Your saved server selection is preserved. Staff opens with the newest accounts first; click Name, Email, Role, Status, or Joined to change sorting. Sorting applies across all pages and requires the matching desktop API update on your server.

Staff contact information can be edited when your account has both staff-view and staff-edit permission in the web admin panel. The Edit form supports names, username, email, phone/WhatsApp, and address details. Country is a searchable dropdown using the same country names as the web admin panel. The matching backend country-list update must be deployed on your server. The server rechecks permission on each save. This requires the matching desktop staff-edit API deployed on your server.

The Edit form also includes a Security tab when your account has staff-view permission plus the backend password-change or two-factor-change permission. Password changes require confirmation and the backend strength rules. Email two-factor can be enabled for accounts without an enabled method; the account holder can switch an enabled method to email after confirming their current password. Enabled methods are preserved for other staff, and disabling two-factor remains prohibited by backend policy. Successful security changes sign the target account out of its existing app sessions. Deploy the matching desktop security API before upgrading production clients.

Closing the window keeps the app running in the background. Click the Bindia icon in the Windows system tray beside the clock to reopen it, or right-click it and choose **Open Bindia Admin**. Choose **Exit** to quit completely. Windows may place the icon inside its hidden-icons menu. Opening the app again restores the existing instance.

From version 0.1.5, click **Update now** in the update notification or Settings to update directly from Bindia. Save any open edits first. The app shows download progress, verifies the signed installer and version, then closes for installation and reopens automatically. Network or verification failures can be retried. It checks for new versions at startup and every six hours; **Settings → Check for updates** checks immediately.

Versions 0.1.4 and earlier need one manual upgrade to the latest version: download this installer, choose **Exit** from the old app's tray menu, then install. Future updates run inside the app.

## Verify a download

Compare the result of this PowerShell command with `SHA256SUMS.txt`:

```powershell
Get-FileHash -LiteralPath '.\Bindia.Admin_0.1.7_x64-setup.exe' -Algorithm SHA256
```

Only installers, compiled executables, updater signatures/manifests, checksums, and distribution documentation belong in this repository. Keep previous releases in their version directories.
