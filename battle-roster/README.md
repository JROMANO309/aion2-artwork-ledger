# Aura Legion Battle Roster

Sign-up page for Aion 2 server battles. Players enter their character name, class and CP, and the page organizes everyone into four forces:

- **Beso's Force**
- **Powerful's Force**
- **Pope's Force**
- **BBCwielder's Force** (Templars)

Each force is split into parties, and every party gets one Cleric and one Chanter. Parties missing either are outlined in red, and the summary line shows how many more Clerics or Chanters are needed. Everything updates live for everyone. Signups are stored in the same Firebase project as the artwork ledger (`../config.js`).

## How players are placed

- Powerful's Force is filled first, by CP, up to its party slots, including a Cleric and a Chanter for each of its parties.
- Every Templar goes to BBCwielder's Force, which also gets a Cleric and a Chanter for each of its parties.
- Everyone else is split evenly between Beso's and Pope's, with Clerics and Chanters spread across both and total CP kept even.
- Inside a force, the remaining players fill the parties so party CP stays even.
- Officers can lock any player to Beso's, Powerful's or Pope's with **Lock to** (a locked Templar stays in that force). Locked players stay put and the sorting works around them.

Officers can change the party size (default 4) and the number of parties in Powerful's Force (default 2) in **Organizer settings**.

## Setup

1. Open the Firebase console for the project, go to **Firestore Database → Rules**, replace everything with the contents of `../firestore.rules`, and click **Publish**. The roster rules changed for the three-force version, so the page won't save until this is done.
2. Open the page with `#roster=YOUR_KEY&officer` on the end. The key can be any 16 to 64 letters, digits, `-` or `_`. Opening the page with no key shows a **Start a new roster** button that makes one for you.

## Links

- **Player link:** `.../battle-roster/#roster=YOUR_KEY`. Share this with the legion.
- **Officer link:** the same with `&officer` on the end. It shows tools to add players, edit or remove any entry, lock players to a force, change the organizer settings and copy both links. Keep it to officers.

The key is not stored in the repo, so the plain page address shows nothing. Each device remembers the key and its own signup after the first visit, so players can come back and change their entry. For a new battle, start a new roster and share the new link.
