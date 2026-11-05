# TorresFam Build 18 — shared administrator access

**Superadmin:** `janiscudilla@gmail.com` (verified Google account)

**Admin:** Honey's Firebase Authentication UID `WRbrhEbXAZPKsI3vGhmWaadBosb2`

## Before replacing Build 17

1. Sign into the **existing** TorresFam site as the Superadmin.
2. Open **Data & exports** and download a **full JSON backup**. Keep the backup in a private location.
3. Confirm the backup contains the expected people and households. Do **not** delete the original Firebase record.

## Deploy Build 18 and its rules

1. In Firebase Console, open **Firestore Database → Rules** for project `torresfam`.
2. Replace the existing rules with the **entire** `torres_firestore_build_18.rules` file and click **Publish**. Do not add the rules below an existing permissive wildcard rule; replace the old rules completely.
3. Upload `torres_family_hub_build_18.html` to your existing GitHub Pages repository as **`index.html`**.
4. Open `https://janiscudilla.github.io/TorresFam/` while signed in as the Superadmin.
5. Since the shared workspace does not exist yet, Build 18 reads the original private document at `users/{your-uid}/private/familyHub` and asks whether to **create a copy** in `workspaces/torresFamilyHub`. Confirm **only if the displayed member and household counts are correct**.
6. After the copy, confirm all family members, households and events are present. In the Firestore **Data** tab, check that `workspaces → torresFamilyHub` exists, contains `payload`, and has `version: 1`.
7. Ask Honey to refresh TorresFam and sign in using the Google account whose UID is `WRbrhEbXAZPKsI3vGhmWaadBosb2`. She should see the **same** people and households.
8. Make a minor test edit from Honey's account; verify that it appears after the Superadmin reloads the site.

## Safety notes

- **Do not** try to initialize a blank shared database from Honey's account. Build 18 intentionally blocks this.
- The old owner-only document remains unchanged and readable by the Superadmin for backup/recovery.
- The live app saves the complete family database as **one** Firestore document. It has a size limit and concurrent editing risks. Build 18 adds optimistic version checks: a stale edit is rejected rather than silently replacing newer cloud data. After a conflict, export unsaved changes as JSON before reloading.
- The current Admin role can view and edit **all** shared data, including banking/contact fields. Only share this role with a trusted adult.
- These roles are fixed in Build 18; there is not yet an in-app invitation/role editor.
- Authentication users appear automatically after their first successful Google sign-in; no email/password user needs to be manually created.
