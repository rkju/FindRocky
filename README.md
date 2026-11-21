# FindRocky

The site is published with GitHub Pages from the root of `main`:
https://rkju.github.io/FindRocky/

## Shared map setup

The map uses Firebase Authentication and Cloud Firestore. Its public web app
configuration and the shared account email are in `firebase-config.js`.

1. In Firebase Console > Authentication > Sign-in method, enable
   **Email/Password**.
2. In Authentication > Users, add `findrocky-team@example.com` and choose a
   team PIN as its password. Use at least six characters; a random PIN of at
   least 10 digits is recommended. This reserved email is only an account
   identifier and cannot receive password-reset emails. Share the PIN privately
   with the team; do not put it in the repository.
3. In Firestore > Rules, paste the contents of `firestore.rules` and publish
   them. Or, with the Firebase CLI installed and signed in, run
   `firebase deploy --only firestore:rules --project findrocky-d1617`.
4. Merge the site changes into `main` for GitHub Pages to publish them.

These rules make only the search-pins collection publicly readable and
writable. Anyone can bypass the site's sign-in screen and access that data
directly through Firebase, so do not put sensitive information in pins or
notes. The PIN is a convenience gate for the site UI, not database security.

PIN sign-in requires an internet connection and is required again after a
reload. GitHub Pages and the site's source code remain public.

**Live Sync** means the shared map is connected. **Offline** or **Sync Error**
disables saving until the connection or rules are fixed. If shared sync cannot
start after sign-in, **Local Only** saves pins in that browser, not to the team
map; local pins do not automatically move to Firebase. GPS requires HTTPS and
location permission.

## Search dog route

`rocky-route.png` is the search dog's tracked route, cut out of the tracking
app screenshot and georeferenced against OpenStreetMap streets (about 5 m
accuracy). The paw button on the map toggles it.
