# Aion 2 Server Battle Roster

Sign-up sheet for server battles. Players enter their character name, class and CP, and join one of the five forces from the battle plan:

| Force | Job |
|---|---|
| Frontline | Open the path |
| Healers | Sustain the team |
| Killzone | Deal massive damage |
| Peelers | Keep the backline safe |
| Divers | Disrupt and eliminate |

Each force shows its headcount, total CP and average CP. Officers can add players who aren't on claude.ai, edit any entry, mark force leaders and export the roster to CSV.

## Where it runs

`index.html` is the source of a claude.ai artifact. It stores signups through the claude.ai artifact runtime (`claude.use("db")`), so the live sign-up page is the published artifact. Opening this file directly or from GitHub Pages shows the layout but cannot save signups.

## Healer assignment

Healers sign up to the Healers force and are assigned to the other groups automatically:

- Each group (Frontline, Killzone, Peelers, Divers) needs 1 healer per 4 members, rounded up. A group of 9 needs 3.
- Groups are ranked by total CP. The strongest healers go to the strongest group first, then down the ranking.
- When there aren't enough healers, every group gets its first healer before any group gets a second.
- Healers left over after every group is covered are shown as Reserve.

The assignment updates live as people sign up or change their CP, and the CSV export includes a "Healing for" column.
