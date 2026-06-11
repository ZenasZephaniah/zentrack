# ZenTrack - Open Source Email Tracker for Firefox

ZenTrack is a lightweight, privacy-focused Firefox extension that seamlessly integrates into Gmail to provide real-time read receipts. 

## Features
- **Real-Time Tracking:** Injects a 1x1 transparent tracking pixel to detect when an email is opened.
- **Gmail DOM Integration:** Uses `MutationObserver` to natively blend into the Gmail Compose window.
- **Custom Dashboard:** A built-in extension popup to view the status and timestamps of all tracked emails.
- **Cloud-Hosted Backend:** Communicates with a custom Node.js REST API and MongoDB database.

## Tech Stack
- **Frontend:** HTML, CSS, Vanilla JavaScript (Manifest V3 Firefox Extension API)
- **Backend:** Node.js, Express.js (Hosted on Render)
- **Database:** MongoDB Atlas (Mongoose ODM)

## Technical Challenges Conquered
1. **Bypassing SPA Limitations:** Gmail is a Single Page Application. Standard DOM loading events don't fire when opening a compose window. Implemented `MutationObserver` to watch for real-time DOM injections.
2. **Cache Busting:** To ensure Gmail's proxy servers don't cache the tracking pixel (which would result in only one hit ever registering), the backend serves the `.gif` with strict HTTP headers: `Cache-Control: no-store, no-cache, must-revalidate, private`.
