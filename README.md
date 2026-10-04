# Bindia Admin for Windows

Download the [latest Windows release](https://github.com/satalways/bindia-admin-app/releases/latest).

This repository contains compiled distribution files. The application source is maintained separately in a private repository.

## Downloads

Version **0.1.12**, Windows x64:

- [Windows installer](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.12/Bindia.Admin_0.1.12_x64-setup.exe) — recommended; installs for the current user and sets up WebView2 when needed.
- [Standalone executable](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.12/bindia-admin-desktop.exe) — requires Microsoft Edge WebView2 Runtime already installed.
- [SHA-256 checksums](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.12/SHA256SUMS.txt).

The same files are stored in [builds/windows/v0.1.12](builds/windows/v0.1.12). Previous versions remain in their own directories and releases.

## Using the app

Bindia Admin opens maximized and selects production by default. The left sidebar and top navigation remain visible while the workspace content scrolls. Sign in using your Bindia admin account; production uses two-factor authentication. Your saved server selection is preserved. Staff opens with the newest accounts first; click Name, Email, Role, Status, or Joined to change sorting. Sorting applies across all pages and requires the matching desktop API update on your server.

Staff editing supports the web profile fields and roles, plus Info, Docs, Admin Docs, HR Sheets, Rating and an attendance link. Each field and tab follows your live backend permissions. The popup keeps its tabs and buttons visible, with vertical scrolling and no horizontal scrollbar. Documents are scoped to the selected staff account; downloads go to your Downloads folder without overwriting existing files. HR generation and ratings retain the web rules.

**My profile** is available from the sidebar or your account name, including when you cannot manage Staff. Update personal/contact and bank details, upload or remove your profile photo, or change your email and password. Email/password changes require your current password and sign out existing app sessions. Email sign-in codes then use the new address; your two-factor method is preserved.

Deploy the matching backend **13.46.133** desktop API before using the new staff and My profile features. No migration is needed.

The Edit form also includes a Security tab when your account has staff-view permission plus the backend password-change or two-factor-change permission. Password changes require confirmation and the backend strength rules. Email two-factor can be enabled for accounts without an enabled method; the account holder can switch an enabled method to email after confirming their current password. Enabled methods are preserved for other staff, and disabling two-factor remains prohibited by backend policy. Successful security changes sign the target account out of its existing app sessions. Deploy the matching desktop security API before upgrading production clients.

In **Settings**, turn on **Run application on Windows startup** to open Bindia automatically when you sign in to Windows. Startup is off until you enable it. The option reads the Windows setting, respects Task Manager changes, and can be turned off at any time. Enable it from the installed app so Windows uses a stable executable location. Automatic startup opens the app maximized. No backend change is required.

Staff editing stays open when clicking outside the popup or pressing Escape. Use **Cancel** or the close button to discard edits and dismiss it; these controls are blocked while saving. Both Contact information and Security tabs provide Cancel. Successful contact saves still close the editor.

Staff user IDs appear beside names as small, muted **#ID** text in the staff list and editor title. No backend update is needed for this display change.

Permitted users can change a staff profile photo from **Edit → Contact information**. Choose a JPG, PNG or WebP photo up to 2 MB and 4096 × 4096 pixels, preview it, and click **Upload photo**. A clear human face is required by the backend. Uploads save separately and preserve unsaved contact fields; a local selection can be discarded or retried. Deploy the matching desktop staff-photo API before upgrading production; old servers keep photo controls hidden. No migration is needed.

Closing the window keeps the app running in the background. Click the Bindia icon in the Windows system tray beside the clock to reopen it, or right-click it and choose **Open Bindia Admin**. Choose **Exit** to quit completely. Windows may place the icon inside its hidden-icons menu. Opening the app again restores the existing instance.

From version 0.1.5, click **Update now** in the update notification or Settings to update directly from Bindia. Save any open edits first. The app shows download progress, verifies the signed installer and version, then closes for installation and reopens automatically. Network or verification failures can be retried. It checks for new versions at startup and every six hours; **Settings → Check for updates** checks immediately.

Versions 0.1.4 and earlier need one manual upgrade to the latest version: download this installer, choose **Exit** from the old app's tray menu, then install. Future updates run inside the app.

## Verify a download

Compare the result of this PowerShell command with `SHA256SUMS.txt`:

```powershell
Get-FileHash -LiteralPath '.\Bindia.Admin_0.1.12_x64-setup.exe' -Algorithm SHA256
```

Only installers, compiled executables, updater signatures/manifests, checksums, and distribution documentation belong in this repository. Keep previous releases in their version directories.
