# FindRocky

The site is published with GitHub Pages from the root of `main`:
https://rkju.github.io/FindRocky/

## Shared map setup

The map uses Firebase Authentication and Cloud Firestore. Its public web app
configuration and the shared account email are in `firebase-config.js`.

1. In Firebase Console > Authentication > Sign-in method, enable
   **Email/Password**.
2. In Authentication > Users, use `findrocky@kodawari.com` with the team PIN as
   its password. Use at least six characters; a random PIN of at least 10 digits
   is recommended. Share the PIN privately with the team; do not put it in the
   repository.
3. In Firestore > Rules, paste the contents of `firestore.rules` and publish
   them. Or, with the Firebase CLI installed and signed in, run
   `firebase deploy --only firestore:rules --project findrocky-d1617`.
4. Merge the site changes into `main` for GitHub Pages to publish them.

Search pins remain publicly readable and writable through Firebase, even
without the site's PIN. Do not put sensitive information in pins or notes.
Walked routes require sign-in as the shared team account. If that account is
recreated, update its UID in `firestore.rules`.

PIN sign-in requires an internet connection and is required again after a
reload. GitHub Pages and the site's source code remain public.

**Live Sync** means pins and routes are connected. **Offline** or **Sync
Error** prevents saving the affected data until the connection or rules are
fixed. If shared sync cannot start after sign-in, **Local Only** or **Partial
Sync** indicates that some or all changes stay in that browser; local data
does not automatically move to Firebase. GPS requires HTTPS and location
permission.

## Search dog route

`rocky-route.png` is the search dog's tracked route, cut out of the tracking
app screenshot and georeferenced against OpenStreetMap streets (about 5 m
accuracy). The paw button on the map toggles it.

The map and search-radius rings center on 17326 Spruce Way. Use the house
button to return to that location.

## Walked routes

Set your name and choose a team color in your profile. Tap **Walked**, drag a
line over the route, choose the date searched, and save it. Tap a saved line to
change its date or delete it. Routes are stored separately from existing pins.
Nelly's imported route is an approximate trace; its date is not recorded.
