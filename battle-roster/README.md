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

## Healer assignment

Healers sign up to the Healers force and are assigned to the other groups automatically:

- Each group (Frontline, Killzone, Peelers, Divers) needs 1 healer per 4 members, rounded up. A group of 9 needs 3.
- Groups are ranked by total CP. The strongest healers go to the strongest group first, then down the ranking.
- When there aren't enough healers, every group gets its first healer before any group gets a second.
- Healers left over after every group is covered are shown as Reserve.

The assignment updates live as people sign up or change their CP, and the CSV export includes a "Healing for" column.
