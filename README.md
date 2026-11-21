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
3. In Firestore > Rules, paste the rules below and publish them. They allow
   only the team account's UID (from Authentication > Users).
4. Merge the site changes into `main` for GitHub Pages to publish them.

The rules restrict access to the shared account, including when anonymous
sign-in or other accounts are enabled:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /artifacts/spruce-dog-search/public/data/search_pins/{pin} {
      allow read, write: if request.auth != null
        && request.auth.uid == "Hw9ILGaajIMxxAajeuN3oa2mINi2";
    }
  }
}
```

PIN sign-in requires an internet connection and is required again after a
reload. GitHub Pages and the site's source code remain public; the PIN and
Firestore rules protect the shared pins and notes, not the page itself.

**Live Sync** means the shared map is connected. **Offline** or **Sync Error**
disables saving until the connection or rules are fixed. If shared sync cannot
start after sign-in, **Local Only** saves pins in that browser, not to the team
map; local pins do not automatically move to Firebase. GPS requires HTTPS and
location permission.

## Search dog route

`rocky-route.png` is the search dog's tracked route, cut out of the tracking
app screenshot and georeferenced against OpenStreetMap streets (about 5 m
accuracy). The paw button on the map toggles it.
