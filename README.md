# Torres Family Hub

**Our family, our story.**

Torres Family Hub is a private, browser-based family directory and annual family-event management application for the descendants of **Jeremias Sahagun Torres Sr. (Daddy Lolo)** and **Estelita Capulong Baluyot Torres (Mama T)**. The application is published as a static website on GitHub Pages, with Google sign-in and private data stored in Firebase Cloud Firestore.

**Website:** https://janiscudilla.github.io/TorresFam/

> **Privacy:** The GitHub Pages site and repository are public, but access to personal records must be enforced with Firebase Authentication **and** Firestore Security Rules. Never add passwords, Firebase service-account private keys, bank details, or real family database exports to this repository.

## Features

- **Family directory:** Structured Filipino birth and current names, nicknames, birthdays, ages, locations, generations, photos, status indicators, and household assignments. Sort by **member name, birthday, age, household, location, or generation**, in ascending or descending order; search and edit records.
- **Family tree:** Visual parent-child and partner relationships rooted in the Torres founding couple; connected descendants, generation calculations, and tree navigation.
- **Households & dues:** Manage independent household memberships, annual payments, and household gift preferences. Philippine, overseas, and unconfirmed locations are distinguished when calculating eligibility.
- **Family Day:** Track annual RSVPs, participants, and gift estimates.
- **Budget & finances:** Budget lines, cash flows, contributions, and expenses.
- **Student recognition:** Record academic and extracurricular achievements and cash incentives by school year.
- **Games & prizes:** Manage activities and prizes for reunions.
- **Data & exports:** Add several names at once, import an existing family spreadsheet as CSV, and export JSON backups or selected data for reports.
- **Google sign-in:** Private administrator workflow using Firebase Authentication; broader family-member access is planned for a later phase.

## Tech stack

- Vanilla **HTML, CSS, and JavaScript** in one `index.html`
- **GitHub Pages** for static hosting
- **Firebase Authentication** for Google sign-in
- **Cloud Firestore** for family records
- No app-specific build process, Node.js installation, or paid AI API required

## Repository contents

| File | Purpose |
| --- | --- |
| `index.html` | Complete TorresFam website (rename the latest Build HTML to this filename) |
| `torres_favicon.png` | Family crest used as the browser tab icon |
| `README.md` | This documentation |

## Deploy or update

1. Download the latest TorresFam Build HTML file and rename it to **`index.html`**.
2. Upload/replace `index.html` in the repository's `main` branch, at its root.
3. Upload **`torres_favicon.png`** to the same location. Keep this exact filename to match the icon link in `index.html`.
4. Upload/replace `README.md` if updating this documentation.
5. Under **Settings → Pages**, select **Deploy from a branch → `main` → `/ (root)`**, if not already enabled.
6. Open https://janiscudilla.github.io/TorresFam/ and refresh after deployment.

GitHub Pages only publishes the **website files**. Family records live in Firebase, not in GitHub.

## Firebase configuration

TorresFam currently expects the Firebase project named `torresfam`. The site's **Firebase web configuration** lives in `index.html`. Those web configuration values are not service-account credentials; do not confuse them with Firestore access rules.

For a new installation:

1. Register a Firebase web app.
2. Enable the **Google** sign-in provider in Firebase Authentication.
3. Add `janiscudilla.github.io` under **Authentication → Settings → Authorized domains**.
4. Create a **Cloud Firestore** database.
5. Configure and publish **owner-only Firestore Security Rules** based on the administrator's Firebase Authentication UID. In the current app, the private family document is stored at `users/{uid}/private/familyHub`; verify your security rules permit the owner and deny everyone else. Do **not** use public `allow read, write: if true` rules.
6. Sign in from the website and test saving a temporary record, reloading, and retrieving it on another device.

**Later phase:** If relatives receive access, implement explicit approval, roles, privacy boundaries, and corresponding Firestore rules before enabling additional accounts.

## Importing family members

Use **Family directory → Import Google Sheets / CSV** to import the existing family sheet, or **Quick add multiple names** to enter several people with just names and surnames. Other details can be added later.

For Google Sheets, use **File → Download → Comma Separated Values (.csv)**. Before a large import, back up existing family data, try a small batch, and review matching or unresolved relationships. Birthdays can be left blank. A family's **genealogical connections** and its **administrative household** are separate concepts.

## Data safety and privacy

- The family database contains personal information (including minors' dates of birth and potentially payment and disability-related details). Only approved administrators should access private records.
- **Do not** upload JSON backups, spreadsheets containing real family records, QR codes, or bank account details to the public GitHub repository.
- Export a **JSON backup** before major imports or deployments. Store backups privately.
- Avoid concurrent editing from multiple devices while the application uses its current single-document Firestore model; newer saves may overwrite other edits.
- Photos and QR images stored inside the database document are size-constrained; a future version may move media to a separate storage system.
- If the site reports missing permissions, verify Firebase sign-in, the administrator UID, and Firestore Security Rules rather than making the database public.

## Design

The interface uses a warm pearl-and-champagne background with burgundy accents and a Torres family crest favicon. It supports desktop and mobile layouts.

## Project status

**Build 14:** Added directory sorting and the family crest favicon. The rest of the application builds on previous TorresFam releases. Real-device and live Firebase tests should be performed after deployment.

---

*A private space for family history, celebrations, and the generations to come.*
