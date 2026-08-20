# Duel Draw — Firebase App Check setup

Duel Draw is already protected by Firebase Anonymous Authentication and Firestore rules that bind each room to its host/guest Firebase UID. App Check is an additional anti-abuse layer that helps Firebase distinguish requests coming from the real web app from scripted traffic.

## Provider

Use **reCAPTCHA Enterprise** for this web app.

## One-time console setup

1. In Google Cloud Console, open **reCAPTCHA Enterprise** for the `dueldraw-e67cd` project.
2. Create a **Website** score-based key (do not use a checkbox challenge).
3. Add the production domain: `iphiginea.github.io`.
4. Copy the **site key**. The site key is public and can safely live in `index.html`; do not place private credentials in the repo.
5. In Firebase Console → **App Check**, register the Duel Draw web app with the **reCAPTCHA Enterprise** provider and that site key.
6. Paste the same public site key into `APP_CHECK_SITE_KEY` in `index.html`.
7. Deploy and test creating/joining a room from the GitHub Pages site.
8. In Firebase Console → **App Check**, review request metrics. Once valid requests are showing normally, enable enforcement for **Cloud Firestore**.

## Important

Do **not** enable App Check enforcement before `APP_CHECK_SITE_KEY` is populated and the deployed app is successfully sending valid App Check tokens, or the game can lock itself out of Firestore.

The SDK is configured for automatic token refresh once the site key is present.

Client wiring is prepared in `index.html`; App Check becomes active when the registered public site key is filled in.
