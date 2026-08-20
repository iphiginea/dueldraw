# Duel Draw — Firebase App Check setup

Duel Draw is protected by Firebase Anonymous Authentication and Firestore rules that bind each room to its host/guest Firebase UID. Firebase App Check with reCAPTCHA Enterprise is now also wired into the web client as an additional anti-abuse layer.

## Provider

Use **reCAPTCHA Enterprise** for this web app.

## Current status

- Production domain: `iphiginea.github.io`
- reCAPTCHA Enterprise site key: configured in `index.html`
- Firebase App Check SDK: loaded and activated
- Automatic App Check token refresh: enabled
- Firestore App Check enforcement: **leave off until valid-request metrics are confirmed**

## Console checklist

1. In Firebase Console → **App Check**, make sure the Duel Draw web app is registered with the **reCAPTCHA Enterprise** provider using the same site key configured in `index.html`.
2. Open the live GitHub Pages app and test creating a room and joining it from a second browser/device.
3. Return to Firebase Console → **App Check** and review Cloud Firestore request metrics.
4. Confirm legitimate traffic appears as **valid** App Check requests.
5. Only after valid traffic is showing normally, enable App Check enforcement for **Cloud Firestore**.

## Important

Do **not** enable App Check enforcement before the deployed app is successfully sending valid App Check tokens, or the game can lock itself out of Firestore.

The reCAPTCHA Enterprise site key is a public client-side identifier. Private credentials should never be committed to this repository.
