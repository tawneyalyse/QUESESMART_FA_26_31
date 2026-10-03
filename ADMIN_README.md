# QueueSmart admin contribution

## Files
Created: admin_dashboard.html, service_management.html, queue_management.html, admin_queue_status.html, admin.js, ADMIN_README.md.
Modified: app.js only.
Unchanged: every original student HTML page and shared.css (verified byte for byte).

app.js adds admin/student navigation, loads/saves service edits in the existing queuesmart-demo sessionStorage object, keeps the service people-ahead count synchronized with the current student, and gives removed students the correct notification text. admin.js runs after app.js on admin pages and reuses services, state, save, notify, render, completeQueue, and QueueSmartValidation.validateService. It has no separate storage or queue system.

## Run locally
Open the project folder in VS Code and use Live Server on index.html. Alternatively, run `python -m http.server 8000` in this folder and open http://localhost:8000/index.html. Use the same browser tab throughout the test: sessionStorage is per tab. Login with a valid email and any password, then use Admin View in the navigation. This remains a front-end demo, without real admin permissions or backend authentication.

## Test each feature
1. Admin Dashboard: follow Admin View after login. Confirm five services initially and counts of the mock students. Follow each of the three admin links and confirm the current-page highlight.
2. Service Management: create Career Services with a description, duration 12, and high priority. Required fields, a whole-number duration of at least 1, and low/medium/high priority are validated. Blank or whitespace-only names/descriptions should fail; duplicate names should show feedback. Edit the new service, save, and refresh to confirm persistence. Cancel an edit to return to create mode. Priority is saved/displayed metadata; it does not automatically reorder students.
3. Student integration: switch to Student View, then Join Queue. Confirm the new service appears and join it. It starts empty, so the student is position 1. Leave it; confirm History and Notifications work as before.
4. Queue Management: join Academic Advising in Student View, then return to admin. It initially has three mock students ahead, plus the current student. Move the current student up one position; check Student View for the new position and notification. Remove a mock student; confirm the current student advances. Use Serve Next Student until the current student is served; verify that their active queue clears and History says Served. Serve Next is disabled for an empty queue.
5. Admin removal: join another service, return to Queue Management, and remove the current student. Verify that History says Removed by admin and Notifications explains the removal. Counts should update.
6. Active service edit: join a service, then edit its name or duration through Service Management. Confirm the student queue uses the new name/duration, wait time changes, and a notification is added.
7. Admin Queue Status: confirm all services appear, with waiting counts, estimated wait for a NEW arrival, current student's position if present, and Waiting/Empty status. Dashboard totals should agree.
8. Regression: test registration validation, login, student Join/Leave, Queue Status demo controls, notification Mark all as read, History, and Logout. Logout clears the existing demo session, including service edits. Logging in with a different email also resets that session, as the original project already did.

## Mock-data model
The original project tracks one current student and a numeric people-ahead count per service. Admin pages represent those counts as labeled mock students. Move Up swaps the current student with a mock student ahead by decreasing the count; this prototype does not keep named students behind the current student. Removing/serving a mock student changes the count but creates no personal history for that anonymous mock student. Student history remains the current student's history. This deliberately follows the existing model rather than adding an independent multi-user queue database.

## Validation completed
Both JavaScript files passed Node syntax checks. Automated JavaScript tests with a simulated DOM verified shared-session joining, admin serving/reordering, service creation/editing, active wait updates, student demo advancement, history, notifications/read, removal, and status counts. Original student HTML and shared.css were verified unchanged. A real browser was unavailable in the execution environment, so complete the manual checks above with Live Server before merging.

## Add to your shared repository
Create your own branch from the teammate's latest branch/version. Copy the five new code files, this README, and the updated app.js into the repository root. Do not replace the original student HTML or CSS. Review the app.js diff, test locally, then commit and push your branch and open a pull request. The upload contains no Git history and has not been pushed or merged.
