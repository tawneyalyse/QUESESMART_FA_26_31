# QueueSmart — Assignment 2 prototype

Plain HTML, CSS, and JavaScript extend the group's original four HTML pages. No build process or backend is required. This keeps the project compatible with GitHub Pages and makes shared behavior reusable for later API integration.

## Run

Open `index.html`, or run `python -m http.server 8000` from this folder and visit http://localhost:8000. A local server or GitHub Pages is recommended for consistent browser storage behavior.

## Changes in this package

- `history.html`: date joined, service, outcome; empty state; populated by leaving or completing a queue.
- `notifications.html`: queue/status messages, unread count, timestamps, mark-all-read action.
- `app.js`: shared navigation, notification/history state, form validation, and mock queue actions.
- `shared.css`: shared responsive styling and visible keyboard focus.
- Existing four pages: connected to shared behavior, associated labels, input constraints, consistent navigation, corrected underscore filenames, dashboard notification summary.
- `queue_status.html`: temporary integration/demo screen to exercise status updates and history. Coordinate with the teammate assigned Queue Status before replacing their work.

## Demo and limitations

Login accepts any correctly formatted email and nonempty password (maximum 128 characters). Registration requires an email and a password of 8–128 characters; it validates input but creates no account. Email is limited to 254 characters. These are prototype rules, not real authentication. Passwords are never saved.

Queue data uses sessionStorage in the current browser tab. Reloading and navigating preserve it; logout clears it. Data is not shared with other devices or administrators. Storage failure displays a warning. No real queue polling or background notifications occur.

Join a service, open Queue Status, and use the explicitly labeled demo controls to advance position or complete the visit. Position 2 or 1 is "Almost ready." Serving removes the active queue and records a Served history entry; leaving records Left queue. One active queue is allowed at a time. Estimates are mocked from the number ahead and each service's duration.

## Admin validation handoff — still needs integration

The ZIP supplied by the team did not contain administrator screens. This package does not implement the administrator dashboard, service management, or queue management.

Load `app.js` on service-management pages. Give the service form fields these names:

- `serviceName`: required, trimmed, maximum 100 characters
- `description`: required, trimmed
- `duration`: required, positive whole number of minutes
- `priority`: low, medium, or high

In the teammate's service-form submit handler, prevent the default submission and call:

```js
if (!QueueSmartValidation.validateService(form)) return;
// Continue the teammate's mock create/edit operation here.
```

Add administrator navigation once actual filenames are agreed. Do not link to nonexistent pages. The positive whole-minute duration and registration password limits are proposed UI rules; confirm against A1. A1 wireframes were not supplied, so consistency with A1 remains to be reviewed.

## Team integration and GitHub contribution

Review these changes before uploading. The existing four HTML files are modified, so compare against the latest GitHub versions and coordinate with their owners. Avoid overwriting changes made since the original ZIP download.

Create a branch, commit the reviewed files while signed into your own GitHub account, and open a pull request for the team. This package has not been pushed to GitHub. No commits or contribution claims have been fabricated.

Suggested commit message: Add queue history, notifications, validation, and navigation

The group submission still needs labeled screenshots, methodology, technology justification, repository link, and an accurate contribution table. Include History and Notifications screenshots as well as the explicitly listed required screens. This package is only the assigned contribution plus mock integration support, not the full completed team assignment.

## Verification

JavaScript syntax and local file links passed checks. DOM-based interaction tests passed for registration, joining, advancing, serving, leaving, history across page navigation, notifications, read state, and service-form validation. A real browser could not be installed in the test environment; visual layout and browser-native length validation still need manual review.
