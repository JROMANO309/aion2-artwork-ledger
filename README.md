# Party Artwork Ledger

A shared Aion 2 tracker for the party (Powerful, Lovecd, nottom, mika, Sticky). It lists the 28 Unique and Heroic field and world boss Pantheon artworks, highlights Illusion + Wisdom rows, switches between English and 中文, and syncs check marks live through a free Firebase database.

## One-time setup (about 10 minutes)

### 1. Create the free database
1. Go to https://console.firebase.google.com and click **Create a project** (Analytics not needed).
2. In the left menu open **Build → Firestore Database → Create database**. Pick a location close to the party and start in **production mode**.
3. Open the **Rules** tab, replace everything with the contents of `firestore.rules`, and click **Publish**.
4. Open **Project settings (gear icon) → General → Your apps → Web (</>)**, register an app (no hosting needed), and copy the `firebaseConfig` values.
5. Paste those values into `config.js`.

### 2. Put it on GitHub Pages
1. Create a new **public** repository on GitHub, for example `aion2-artwork-ledger`.
2. Upload `index.html`, `config.js`, `firestore.rules` and this README (drag them onto the repo page → **Commit changes**).
3. Open **Settings → Pages**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, and save.
4. After a minute the site is live at `https://<your-username>.github.io/aion2-artwork-ledger/`.

### 3. Share the party link
Send the party this link, with the party key on the end:

```
https://<your-username>.github.io/aion2-artwork-ledger/#party=YOUR_PARTY_KEY
```

The party key is not stored in the repo. Anyone with the full link can tick boxes; anyone with only the plain site address sees an empty read-only board. Each device remembers the key after the first visit. To lock everyone out, change the key and share a new link (the old check marks stay under the old key).

## Changing the party
Edit the `MEMBERS` list near the top of the script in `index.html` **and** the names in `firestore.rules`, then republish the rules.
