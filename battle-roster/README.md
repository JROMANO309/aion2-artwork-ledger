# Aion 2 Server Battle Roster

Sign-up page for server battles. Players enter their character name, class and CP, and join one of the five forces from the battle plan:

| Force | Job |
|---|---|
| Frontline | Open the path |
| Healers | Sustain the team |
| Killzone | Deal massive damage |
| Peelers | Keep the backline safe |
| Divers | Disrupt and eliminate |

Each force shows its headcount, total CP and average CP, and updates live for everyone. Signups are stored in the same Firebase project as the artwork ledger (`../config.js`).

## Setup

1. Open the Firebase console for the project, go to **Firestore Database → Rules**, replace everything with the contents of `../firestore.rules`, and click **Publish**. The new `rosters` block is what lets the roster save; the party ledger rules are unchanged.
2. Open the page with `#roster=YOUR_KEY&officer` on the end. The key can be any 16 to 64 letters, digits, `-` or `_`. Opening the page with no key shows a **Start a new roster** button that makes one for you.

## Links

- **Player link:** `.../battle-roster/#roster=YOUR_KEY`. Share this with the server.
- **Officer link:** the same with `&officer` on the end. It shows tools to add players, edit any entry, mark force leaders and copy both links. Keep it to officers.

The key is not stored in the repo, so the plain page address shows nothing. Each device remembers the key and its own signup after the first visit, so players can come back and change their entry. For a new battle, start a new roster and share the new link.

Anyone with the player link can add or change entries, and the officer switch hides tools rather than locking them, the same trust model as the party ledger. Export the CSV before a battle if you want a record.

## How the formation is built

- **Sections:** Frontline, Killzone, Peelers and Divers. Healers sign up to the Healers section and are placed into groups automatically.
- **Forces:** each section splits into as many forces as it needs. A force holds up to 4 groups of 5 (4 members + 1 healer), so 20 people.
- **Force leaders:** officers tick Force leader on a player. Each force leader starts their own force, and the strongest leader leads Force 1. A section opens more forces once it passes 16 members per force; those forces show "No force leader yet" until an officer sets one.
- **Who goes where:** the strongest players fill Force 1 first, and forces are kept even in size. Inside a force, members are snake-drafted into groups so each group's CP is balanced.
- **Healers:** 1 per group. When there aren't enough, every force's Group 1 is covered before any Group 2, starting with the strongest force. The strongest healers then go to the strongest groups. Extra healers show as Reserve.

Everything updates live as people sign up or change their CP. The CSV export lists every section, force, group and role.
