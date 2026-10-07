# Bindia Admin for Windows

Download the [latest Windows release](https://github.com/satalways/bindia-admin-app/releases/latest).

This repository contains compiled distribution files. The application source is maintained separately in a private repository.

## Downloads

Version **0.1.38**, Windows x64:

- [Windows installer](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.38/Bindia.Admin_0.1.38_x64-setup.exe) — recommended; installs for the current user and sets up WebView2 when needed.
- [Standalone executable](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.38/bindia-admin-desktop.exe) — requires Microsoft Edge WebView2 Runtime already installed.
- [SHA-256 checksums](https://github.com/satalways/bindia-admin-app/releases/download/v0.1.38/SHA256SUMS.txt).

The same files are stored in [builds/windows/v0.1.38](builds/windows/v0.1.38). Only the latest release files are retained in this checkout and GitHub Releases; earlier changes remain in Git history.

Dates default to **dd-mm-YYYY**. In **Settings → Date and time**, choose your preferred date format and a 12-hour or 24-hour clock. Preferences apply immediately and remain saved on this device.

In **Staff**, click **Download Excel** to save all matching staff to Downloads using the current search, status filter and sort order. The workbook follows your date/time settings and requires staff-view permission.

Drag a JPG, PNG or WebP photo into the profile photo area, preview it, then click **Upload photo**. In **Docs** and **Admin Docs**, drop up to ten supported documents (20 MB each) to upload immediately. Uploads preserve unsaved profile details. The backend update also fixes a first photo upload being blocked by earlier profile edits.

## Improvements in 0.1.38

- Remove worked-time displays from My attendance and the Attendance list, details and editor.
- Keep break time, total shift time, shift controls and existing attendance permissions.
- Simplify the My attendance summary layout after removing the worked-time counter.

This display-only update uses the existing backend. No additional backend deployment or migration is required.

Validation on 07-10-2026: 78 frontend tests and 28 native tests passed. Fictional-data previews verified attendance actions, error recovery, the revised summary and the 900-pixel layout. Production frontend and signed Windows builds passed. Executable version, installer signature and signed version verified; altered installer bytes were rejected. SHA-256 checksums accompany the final packaged files. Installer execution was not performed.

## Improvements in 0.1.37

- Add Reservations under Customer with search, date/status/shop filters, booking edits and individual or selected deletion with typed confirmation.
- Follow the backend view, edit and delete permissions on every Reservations request, including revoked access. Preserve Under Review and automatic completion behavior.
- Show unread Reservations and Catering Orders badges beside their sidebar links using the same backend counts. Refresh automatically and after read-status changes; hide zero counts.
- Move Connection details from Settings to About.

Requires backend 13.46.163 with Reservations endpoints, permission profile and sidebar counts deployed together. No migration is required. Production backend deployment is separate.

Validation: 78 frontend tests, 28 native tests and 20 focused backend tests (222 assertions) passed. Existing PHP deprecations remain. Fictional-data previews verified Reservations navigation, editing, read status, deletion cancellation, view-only controls and unread badge updates. Signed installer version, signature and published checksums were verified; altered installer bytes were rejected. Installer execution was not performed.

## Improvements in 0.1.36

- Reduce the left indentation of every sidebar link and section heading.
- Give nested links such as Permission Manager more space for their labels.

This spacing update uses the existing backend. Catering Orders continues to require backend 13.46.162 deployed.

The production frontend and signed Windows builds passed. Executable version, installer signature, signed version and release checksums were verified; altered installer bytes were rejected. Installer execution was not performed.

## Improvements in 0.1.35

- Remember which sidebar sections are open or closed across application restarts.
- Add Catering Orders with filters, summary totals, previews, full details, editing, manual payment confirmation, payment links, PDF receipts and payment settings.
- Follow the backend Catering permissions for navigation and every request, including revoked access.

Requires backend 13.46.162 with the desktop Catering endpoints and permission profile deployed together. No migration is required. Production backend deployment is separate.

Validation: 75 frontend tests, 27 native tests and 11 Catering backend tests (124 assertions) passed. Backend tests report existing PHP deprecations. Fictional-data previews verified listing, detail, editing, payment and settings flows. Installer execution was not performed.

## Improvements in 0.1.34

- The top avatar and username now open an account menu with My profile and Logout. My profile is removed from the sidebar.
- Customer contains Orders. Customer, Control, HR and Manager can be expanded or collapsed.
- My attendance has a clearer shift layout and a live worked-time counter using server timestamps. Breaks are excluded, work time pauses during breaks and stops at checkout.
- Orders has a redesigned list and summary cards for total sales and paid/unpaid orders. Total sales includes only paid orders across every page matching the current filters.

Deploy backend 13.46.161 for Orders sales totals. No migration is required; production backend deployment is separate. Existing permissions remain enforced.

Validation: 62 frontend tests, 25 native tests and five focused backend tests (38 assertions) passed, with existing PHP deprecations. Production frontend and signed Windows builds passed. Executable version, installer signature, signed version and published checksums verified; altered installer bytes rejected. Fictional-data previews verified the account menu/logout, sidebar collapse, shift pause/resume/checkout, and paid-only sales across pages. Installer execution and real attendance/order mutations were not performed.

## Improvements in 0.1.33

- Group sidebar links under **Control** (Attendance), **HR** (Staff List) and **Manager** (Permission Manager).
- Rename Staff to Staff List and move Chat & calls directly after My attendance.
- Hide sections when the signed-in user has no permission to access their links; preserve existing module permissions.
- Backend **13.46.160** runs artisan optimize2 once after successful Permission Manager saves from desktop and web. Failed saves do not run optimization.

Deploy backend **13.46.160**, including the shared PermissionManagerLayers service and web PermissionManagerController, to enable the new cache refresh behavior. No migration is required. Production backend deployment is separate.

Validation on 06-10-2026: 55 frontend tests, 25 native tests and 12 focused backend tests (70 assertions) passed, with existing backend PHP deprecations. Production frontend and signed Windows x64 builds passed. Executable version, installer signature, signed version and published SHA-256 checksums verified; altered installer bytes were rejected. Installer execution and real permission changes were not performed.

## Improvements in 0.1.32

- Search Permission Manager staff by name or staff ID and filter by role.
- Select staff using larger cards, review selected users, remove individuals or clear the selection.
- Select or deselect all shown staff without changing users outside the active filters.
- Preserve all existing backend permission rules and save behavior.

Uses the existing Permission Manager backend **13.46.159**. No additional backend change or migration is required.

Validation on 06-10-2026: 55 frontend tests and 25 native tests passed. Production frontend and signed Windows x64 builds passed. Installer signature, signed version, executable version and SHA-256 checksums verified; altered installer bytes were rejected. UI preview checks used fictional staff and verified search, role filtering, selection, removal and save payloads. Installer execution and real permission changes were not performed.

## Improvements in 0.1.31

- Add **Permission Manager** with the backend's module catalog, staff roles, editable layers and permission groups.
- Enforce the same live **permission.manager** gate for viewing, saving and Security Layer verification. Denied users cannot use the module through navigation or API requests.
- Combine permissions across staff layers, preserve other modules, clear affected permission caches and refresh the signed-in user's access after a save.
- Automatically clear background chat connection warnings when the affected requests recover. Chat and incoming calls are tracked separately; unrelated errors remain visible.

Deploy backend **13.46.159** and refresh route/configuration caches before using Permission Manager. Deploy the shared PermissionManagerLayers service, both PermissionManagerController changes, DesktopAdminAccess and desktop routes together. No migration is required. Production backend deployment is separate.

Validation on 06-10-2026: 52 frontend tests, 25 native tests and 14 focused backend tests (75 assertions) passed, with existing backend PHP deprecations. Production frontend and signed Windows x64 builds passed. Executable version, installer signature, signed version and copied SHA-256 checksums verified; altered installer bytes were rejected. UI preview checks used fictional staff. Installer execution and real permission changes were not performed.

## Improvements in 0.1.30

- Fix My attendance actions returning 404 despite deployed backend endpoints: check-in, check-out, pause and resume now send POST requests from the Windows application. Status continues to use GET.
- Adds native request-method regression checks for attendance actions, JSON bodies and existing read/write operations.

Uses the existing backend **13.46.156**. No further backend change or migration is required if that version is deployed. Install the updated desktop application to receive this fix.

Validation on 05-10-2026: 46 frontend tests and 24 native tests passed. Production frontend and signed Windows x64 builds passed. The executable reports 0.1.30; installer signature, signed version and copied SHA-256 checksums verified. Altered installer bytes were rejected. Installer execution and real attendance mutations were not performed.

## Improvements in 0.1.29

- **My attendance** is available separately from Attendance management to every signed-in user. Check in, check out, pause and resume your own shift, add optional check-in/out notes, and view shift and break details.
- Actions follow current server status, prevent duplicate clicks, preserve notes when a request fails and refresh status automatically. Existing account, location, schedule and checkout rules remain enforced.
- **Application updates** has moved from Settings to About, between application details and the GitHub card. The source-hosting sentence has been removed from the About page.

Deploy backend **13.46.156** and refresh route/configuration caches before using My attendance. No migration is required. Attendance management retains its existing permissions.

Validation on 05-10-2026: 46 frontend tests, 22 native tests and 17 backend attendance tests (273 assertions) passed, with existing backend framework deprecations. UI fixtures verified the complete self-service flow, restricted-account access, duplicate-submit blocking, checkout rejection/retry, notes, About update controls/links and the 900px layout. Installer execution and real attendance mutations were not performed.

## Improvements in 0.1.28

- Open **About** from the sidebar to read a short application description and see the installed version.
- View public GitHub repository information and open the repository or releases in your default browser.
- About is available to every signed-in account, including accounts without staff or order access.

No new backend deployment or migration is required.

Validation on 05-10-2026: 46 frontend and 21 native tests passed. About page fixtures verified restricted-account navigation, content, native link routing and the 900px layout without browser errors. Production frontend and signed Windows x64 builds passed. Executable version, installer signature and signed version verified; altered installer bytes were rejected. Installer execution was not performed.

## Improvements in 0.1.27

- Staff names now show profile photos, with a default icon when unavailable.
- Uploading a photo in the editor updates the staff list avatar.
- Administrator, Active and Contracted switches fit on one row, stacking on small screens.

Deploy backend **13.46.155** for photo access by staff viewers. Photo reads require staff-view permission; uploads still require staff-edit permission as well. No migration is required.

Validation on 05-10-2026: 46 frontend tests, 21 native tests and five backend photo tests (42 assertions) passed, with existing backend framework deprecations. Production frontend and signed Windows x64 builds passed. Executable version, installer signature, signed version and copied SHA-256 checksums verified; altered installer bytes were rejected. Installer execution was not performed.

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

Release packaging: production frontend and signed Windows x64 NSIS builds passed. The executable reports 0.1.29. Installer signature and signed version verify against the embedded updater key, altered installer bytes are rejected, and SHA-256 checksums match the exact final distribution files.
