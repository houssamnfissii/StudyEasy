# StudyEasy 🎓

A clean, single-file study dashboard for organizing modules, resources, notes, and your study schedule — with automatic Google Drive sync so your data follows you across devices.

No build step, no backend, no database to host. It's one `index.html` file you can open locally or deploy anywhere static files are served.

## Features

- **Modules** — group your resources, notes, and progress by subject or course
- **Resources** — save links, YouTube videos, and PDFs with automatic progress tracking as you view them
- **Notes** — quick notes per module, pin the important ones
- **Schedule** — plan study sessions with start/end times and completion tracking
- **Command palette** — press `Cmd/Ctrl + K` to jump to any module, resource, or note instantly
- **Google Drive sync** — sign in once and your data backs up to a `StudyEasy` folder in your Drive, syncing automatically as you work
- **Light / dark / system themes**
- **Responsive** — works as a desktop-style window or a mobile app with bottom navigation

## Getting started

1. Download `index.html`
2. Open it in any modern browser — that's it, no installation required

To use Google Drive sync, you'll need your own Google OAuth Client ID (see below).

## Setting up Google Drive sync

The app uses [Google Identity Services](https://developers.google.com/identity/gsi/web) for sign-in and the Drive API (`drive.file` scope) to store your data as a private JSON file in your own Drive.

1. Create a project in the [Google Cloud Console](https://console.cloud.google.com/)
2. Enable the **Google Drive API**
3. Configure the **OAuth consent screen**
4. Create an **OAuth 2.0 Client ID** (type: Web application) and add your domain(s) to *Authorized JavaScript origins*
5. Paste your Client ID into `index.html`:

   ```js
   const GOOGLE_CLIENT_ID = "YOUR_CLIENT_ID.apps.googleusercontent.com";
   ```

The app only ever requests access to files it creates itself (`drive.file` scope) — it can't see or touch the rest of your Drive.

## How data works

- Everything is saved to `localStorage` immediately as you use the app, so it works fully offline
- When signed in, changes sync to a `StudyEasy/infra2026-data.json` file in your Drive in the background
- On sign-in, the newer copy (local vs. Drive) wins, so you always resume where you left off — even on a different device
- If a background sync can't complete (e.g. your session needs refreshing), the app never interrupts you — it keeps working locally and quietly retries, with a small status indicator next to your account name

## Tech stack

- HTML 
- CSS 
- Vanilla JavaScript 
- [Lucide](https://lucide.dev/) for icons
- Google Identity Services + Drive API v3 for authentication and sync

## Browser support

Works in current versions of Chrome, Edge, Firefox, and Safari. Google Drive sync relies on third-party cookies/session support in your browser being allowed for `accounts.google.com`.

## License

This project is licensed under the [MIT License](LICENSE).

## Author

Developed by [HOUSSAM NFISSI](https://github.com/houssamnfissii)
