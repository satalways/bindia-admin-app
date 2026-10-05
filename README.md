# Bindia Admin for Windows

Download the [latest Windows release](https://github.com/satalways/bindia-admin-app/releases/latest).

This repository contains compiled distribution files. The application source is maintained separately in a private repository.

## Downloads

Version **0.1.26**, Windows x64:

- [Windows installer](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.26/Bindia.Admin_0.1.26_x64-setup.exe) — recommended; installs for the current user and sets up WebView2 when needed.
- [Standalone executable](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.26/bindia-admin-desktop.exe) — requires Microsoft Edge WebView2 Runtime already installed.
- [SHA-256 checksums](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.26/SHA256SUMS.txt).

The same files are stored in [builds/windows/v0.1.26](builds/windows/v0.1.26). Previous versions remain in their own directories and releases.

Dates default to **dd-mm-YYYY**. In **Settings → Date and time**, choose your preferred date format and a 12-hour or 24-hour clock. Preferences apply immediately and remain saved on this device.

In **Staff**, click **Download Excel** to save all matching staff to Downloads using the current search, status filter and sort order. The workbook follows your date/time settings and requires staff-view permission.

Drag a JPG, PNG or WebP photo into the profile photo area, preview it, then click **Upload photo**. In **Docs** and **Admin Docs**, drop up to ten supported documents (20 MB each) to upload immediately. Uploads preserve unsaved profile details. The backend update also fixes a first photo upload being blocked by earlier profile edits.

## Improvements in 0.1.26

- Orders has a date-range picker with Today, Yesterday, Last 7 Days, Last 30 Days, This Month and Last Month presets, plus custom dates.
- Ranges include both selected days, follow your saved date format and reset pagination when changed. Clear dates returns to all orders.
- Search and payment filters work together with the range; existing order permissions remain enforced.

Deploy backend **13.46.152** for date-range filtering before installing this client. No migration is required.

Validation on 05-10-2026: 46 frontend tests, 21 native tests and six focused backend checks (37 assertions) passed. The signed Windows x64 build, executable version, installer signature, signed version and copied SHA-256 checksums verified; altered installer bytes were rejected. Installer execution was not performed.

## Improvements in 0.1.25

- Pairs with backend 13.46.151 to fix legitimate login/API requests rejected because of Cloudflare proxy IPs.
- Genuine server security blocks now include a readable reason. Account restrictions, two-factor authentication and module permissions remain enforced.

Deploy backend **13.46.151** and refresh configuration caches to apply the production fix. Updating the desktop alone does not change server security rules. No migration is required.

## Improvements in 0.1.24

- Pasted, selected and dropped chat images show draft thumbnails, filenames and remove buttons. Click a thumbnail for a larger preview before sending.
- Add attendance shows live work hours below the In/Out times, using the server timezone and supporting overnight dates. An earlier checkout produces a warning.

These features use existing backend APIs and require no additional backend deployment or migration.

Validation on 05-10-2026: 44 frontend and 21 native tests passed. Browser fixtures verified image draft previews, removal, sending with captions and preview URL cleanup, plus live attendance totals and reversed/overnight intervals. Unit tests cover daylight-saving transitions. The production frontend and signed Windows installer built successfully; signature, signed version, executable version and checksums verified, with tampered bytes rejected. Native Windows Ctrl+V and installer execution were not exercised.

## Improvements in 0.1.23

- Chat uses the available window width, with smaller left/right outer margins.
- Paste copied images into the message composer to attach them, then click Send. Your caption stays intact, and normal text paste still works.
- Pasted images share the existing limits of five attachments and 10 MB per file.

These changes use the existing attachment APIs and require no additional backend deployment or migration. The previous release's message edit/delete actions still require backend 13.46.146 and its migration.

Validation on 05-10-2026: 39 frontend and 21 native tests passed; production frontend and signed Windows installer built successfully. Signature/signed version, executable version and checksums verified, with tampered bytes rejected. Clipboard event fixtures checked image attachment, explicit sending/caption preservation, text paste handling and oversized-image rejection. Native Windows Ctrl+V and installer execution were not exercised.

## Improvements in 0.1.22

- Your sent-message menu supports editing text and attachment captions. Saved changes show an Edited label and preserve your unsent draft.
- Delete for everyone follows the backend's existing rule: only your unread normal messages in private chats. A deleted-message placeholder remains for replies; attachments and reactions are removed.
- The page title/subtitle has been removed, giving chat 100 pixels more height. Notification sound controls sit beside Chats.
- Record voice messages from the mic icon beside emoji and attachment icons. The timer, cancel and Stop & preview controls remain available while recording.

Requires backend **13.46.146** and the chat message changes migration before message actions are enabled. Deploy the backend update and refresh route/configuration caches. Sender ownership, conversation scope and current group membership are enforced on the server. Older backends hide unavailable message actions.

Validation: signed Windows x64 installer and production frontend built successfully; 39 frontend tests, 21 native tests and 140 backend chat/preview/Firebase tests passed (945 backend assertions). Installer signature/signed version, executable version and SHA-256 checksums verified; tampered bytes rejected. Local fixtures checked the compact chat layout, synthetic voice recording/cancel/preview, message editing/deletion and draft preservation. Five existing backend framework deprecations remain. Installer execution and live two-user changes were not exercised.

## Improvements in 0.1.21

- Voice messages use a compact waveform player with seek, duration, speed controls and download.
- A searchable emoji picker inserts emojis into the message composer; drag files into the active chat to attach them for review before sending.
- Image messages show thumbnails and open an in-app viewer with zoom, rotation and download.
- Shared links show page titles and descriptions. YouTube video cards open a player inside Bindia, supporting watch links, Shorts, live links and timestamps.
- New messages and incoming calls show Windows notifications while Bindia is minimized, behind another app or closed to the tray. Clicking an alert restores the conversation. The sound switch controls native alert sounds too.

Deploy backend **13.46.143**, refresh route/configuration caches and keep the chat preview queue worker running. No database migration is required. Windows notifications must be enabled for Bindia Admin. Closing to the tray keeps the app connected; choosing **Exit** fully quits and stops alerts.

Validation: the production frontend and signed Windows x64 installer built successfully. 39 frontend tests, 21 native tests and 126 backend chat/preview tests passed. Installer signature, signed version, executable version and SHA-256 checksums verified; tampered installer bytes rejected. Local fixtures checked image viewing/download, page cards, YouTube popup lifecycle/timestamps and emoji selection. Live Windows notification delivery, real YouTube playback and installer execution have not been exercised.

## Improvements in 0.1.20

- Chat keeps the cursor ready after sending and adds clearer message/call alerts, a WhatsApp-style conversation layout, unread filtering and saved drafts.
- Users show online status and profile photos in the chat list, conversation header and incoming/active call screens, with initials as a fallback.
- Audio and video calls include Answer/Decline, mute, camera controls, video tiles and call duration.
- Record, cancel, preview, send and play voice messages through private authenticated attachment access.

Deploy backend **13.46.142** and refresh route/configuration caches for these features. Existing chat and media tables are reused; no new migration is required. The app must be running and connected to receive notifications.

Validation: the production frontend and signed Windows x64 installer built successfully. 30 frontend tests, 17 native tests and 27 backend chat/call tests passed. Installer signature, signed version, executable version and SHA-256 checksums verified; tampered installer bytes were rejected. Local fixtures verified chat/call layout and voice recording/playback with synthetic media. Live two-device calls and installer execution have not been exercised.

## Improvements in 0.1.19

- Chat & calls brings private/group messages, new groups, replies, search, older history, unread counts/read receipts, and file attachments into the desktop app.
- Private and group audio calls use the same backend conversations and LiveKit services as the web panel. Answer/decline incoming private calls, mute/unmute, and end calls while moving between desktop modules. The app must be running and connected to receive calls.
- The top navigation displays your profile photo, with a user avatar fallback. Uploading or removing the photo updates the header automatically.

Deploy backend **13.46.141** and refresh route caches to enable Chat & calls. Access follows the web chat rules: active users may contact active colleagues; groups require membership. No new migration is needed beyond the existing web chat migrations. Older backends keep the new module hidden.

Validation: the frontend and signed Windows installer build passed, along with 23 frontend tests, 17 native tests and 9 backend chat tests. Live Windows-to-web microphone/speaker interoperability and installer execution were not exercised; validate audio against the deployed backend before operational use.

## Using the app

**Attendance** includes payroll-period and employee/shop filters, summaries, shift and break details, manual entries and edits, approval/rejection, notes and history, trash restore, CSV/Excel exports, salary reports and rounding settings. It follows the same backend permissions and staff visibility rules as the web panel; reviewing your own attendance is restricted.

Administrators with permission can select **Staff → Add staff**. The form validates unique account details and a strong initial password. The form includes an **Administrator** checkbox when permitted and a **Profile photo** picker with preview. Photos are saved with the account and require a clear human face (JPG, PNG or WebP, up to 2 MB and 4096 × 4096 pixels). Administrator status, photo uploads and activation each follow their backend permissions. Add staff and Edit staff use the same width, up to 1200 pixels, and adapt to smaller windows.

Deploy backend **13.46.139** and refresh its configuration and route caches before using these additions. No database migration is required.

Bindia Admin opens maximized and selects production by default. The left sidebar and top navigation remain visible while the workspace content scrolls. Sign in using your Bindia admin account; production uses two-factor authentication. Your saved server selection is preserved. Staff opens with the newest accounts first; click Name, Email, Role, Status, or Joined to change sorting. Sorting applies across all pages and requires the matching desktop API update on your server.

Staff editing supports the web profile fields and roles, plus Info, Docs, Admin Docs, HR Sheets, Rating and native attendance. Each field and tab follows your live backend permissions. The popup keeps its tabs and buttons visible, with vertical scrolling and no horizontal scrollbar. Documents are scoped to the selected staff account; downloads go to your Downloads folder without overwriting existing files. HR generation and ratings retain the web rules.

**My profile** is available from the sidebar or your account name, including when you cannot manage Staff. Update personal/contact and bank details, upload or remove your profile photo, or change your email and password. Email/password changes require your current password and sign out existing app sessions. Email sign-in codes then use the new address; your two-factor method is preserved.

Deploy the matching backend **13.46.139** desktop API before using the new staff and My profile features. No migration is needed.

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
Get-FileHash -LiteralPath '.\Bindia.Admin_0.1.19_x64-setup.exe' -Algorithm SHA256
```

Only installers, compiled executables, updater signatures/manifests, checksums, and distribution documentation belong in this repository. Keep previous releases in their version directories.

Validation for 0.1.25 on 05-10-2026: 110 backend tests / 153 assertions, 44 frontend tests and 21 native tests passed. Production frontend and signed Windows installer built successfully. Executable version, signature/signed version and final checksums verified; tampered installer bytes rejected. Five backend deprecation notices remain. Installer execution and production backend deployment were not performed.
