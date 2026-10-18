# Noon Academy Multan

Class hub for Noon Academy Multan (Chemistry & Biology): student, teacher and admin logins, class chat rooms with pinned messages, photo and PDF sharing, direct messages, attendance, timetable, homework with submissions, results, fee receipts, notifications, admissions, reviews, Urdu/English and light/dark theme.

The whole site is one file, `index.html`. Host it with GitHub Pages.

## Accounts
- **Admin:** username `admin`. The password is stored only as a salted hash inside `index.html`. Ask whoever set up the site for it, and do not write it in this repository.
- **Teachers:** the admin opens *Admin panel > Teacher codes > Generate teacher code*. The one-time code (valid 48 hours) is entered on the Register page with role Teacher.
- **Students:** register themselves and choose a class, or the admin approves an admission form (a temporary password is shown once).
- Admin can add or remove classes, reset passwords, remove accounts and show or hide reviews.

## Turn on live sync (needed so every phone shares the same chat and accounts)
Without this step data is saved only in each visitor's own browser.
1. Go to https://console.firebase.google.com and create a project.
2. Build > **Realtime Database** > Create database. Choose any location.
3. Open the **Rules** tab and publish:
   `{ "rules": { ".read": true, ".write": true } }`
4. Copy the database URL (looks like `https://your-project-default-rtdb.firebaseio.com`).
5. In `index.html`, find `DB_URL:''` near the top of the script and paste the URL between the quotes. Commit.

Passwords are never stored in plain text (salted PBKDF2 hashes). These open rules suit a small academy prototype, but anyone who finds the database URL could read or edit its data. For stronger protection, move to Firebase Authentication with proper rules.

## Easy edits
In the `CFG` block at the top of the script: `MAP` (Google Maps link for the location button), `PLACE` (address text), `WA` and `PHONE` (WhatsApp number).
