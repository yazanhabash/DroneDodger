# Game rules: Drone Dodger

**Version:** rules v5, 2026-10-20 (matches brief v6: sea, 4-way movement, 3-hit hull, preset levels)

## Goal (one sentence)

Steer your warship through every wave of all three levels before your hull takes its third hit.

## How to play (shown on the start screen)

1. Press **New game**.
2. Steer with the **arrow keys**. On a phone, touch and hold where you want to go.
3. Slip through the gaps. Each wave you pass is worth 1 point.
4. Your hull takes 2 hits. The 3rd sinks you. Clear every level to win.

## What the player can do

| Action | Laptop | Phone/tablet | Effect |
| --- | --- | --- | --- |
| Steer | Hold ↑ ↓ ← → (or W A S D); two keys move diagonally | Touch and hold a spot | Moves at a steady speed toward that direction or spot |
| Nothing held | — | — | The ship stays where it is |
| New game | Button, Enter or Space | Tap the button | Starts at level 1 |
| Resume after a pause | Space, an arrow key, or click | Tap | Continues from where it stopped |

## Level design (how levels are written)

Levels live at the top of `index.html`, under the heading **LEVELS — edit these to design the game**.

```
{
  name: "Calm Waters",
  speed: 140,      // bigger = faster
  spacing: 300,    // distance between waves; bigger = more reaction time
  waves: [
    "D....D",
    ".D..D.",
    "......",      // a breather row
    ...
  ]
}
```

Each wave is exactly 6 characters, one per lane from left to right:

| Letter | Meaning |
| --- | --- |
| `D` | Drone (1×) |
| `S` | Shoe (1×) |
| `PP` | Airplane, always two letters side by side (1.5×) |
| `M` | Missile (2×) |
| `.` | Open water |

**Way-out rule (checked automatically):** you must be able to get from an open lane in one wave to an open lane in the next. The lanes you cross must be open in the next wave, and the ship must have time to cross them. The checker prints any wave that breaks this rule in the browser console.

## Collisions and hull

- A hit happens when the ship's body overlaps an object. Hit boxes are slightly smaller than the drawings.
- Each hit takes 1 hull point and makes the ship flash for 1.5 seconds. While it flashes, it can't be hit again.
- The **third hit** sinks the ship and ends the game.
- The sea edges and the score bar stop the ship and never cause damage.

## Score

- +1 when every object in a wave is below the ship, once per wave. Breather rows don't score.
- The maximum score with the current three levels is 50.

## Screens (states)

| State | What you see | Moving? |
| --- | --- | --- |
| **Start screen** | Instructions, last score, top score, New game | No |
| **Playing** | Ship, wake, waves, score, hull (3 boxes), level number. The level name shows for 2 seconds at the start | Yes |
| **Paused** (tab or window switched) | "Paused. Tap or press Space to continue." | No |
| **Level cleared** (about 2 seconds) | "Level N cleared!" and the next level's name | Sea only |
| **Sunk** / **All levels cleared** (about 1 second) | Banner and score | Sea only |

## Transition table

| From | Event | Result |
| --- | --- | --- |
| Start screen | New game | Level 1. Score 0, hull 3, ship centred near the bottom |
| Playing | Steer | Ship moves; stops when released |
| Playing | A wave passes the ship | +1 |
| Playing | Hit, hull above 1, not flashing | Hull −1, flashing, play continues |
| Playing | Hit, hull 1, not flashing | Sunk |
| Playing | Last wave of a level has left the screen | Level cleared, or All levels cleared after level 3 |
| Level cleared | After about 2 seconds | Next level starts. Score, hull and position carry over |
| Sunk / All cleared | After about 1 second | Start screen. Last and top scores are updated and saved |
| Playing | Tab or window switched | Paused |
| Paused | Space, arrow key or tap | Playing |

## Kept vs reset

| Kept between games | Reset each new game |
| --- | --- |
| Last score, top score | Level, score, hull, ship position, waves, flashing, wake |

## Partner test cases

Record Passed, Failed, or Not tested.

1. Start screen shows the last and top scores. Does New game start *Calm Waters*, with 3 green hull boxes?
2. Do all four arrow keys move the ship, and does letting go stop it? Do two keys together move it diagonally?
3. Does the ship stop at every edge and at the score bar without damage?
4. After the first wave passes, is the score exactly 1?
5. Get hit once and then twice. Does the hull drop each time, with flashing and play continuing?
6. Does the third hit show "Sunk!" and then the start screen with your score?
7. Clear level 1. Does "Level 1 cleared!" show, followed by *Air Patrol*?
8. Is there always a reachable opening in every level?
9. Clear all three levels. Does "All levels cleared!" show, and does the start screen say "You cleared all 3 levels!"?
10. Switch tabs mid-level and come back. Is it paused, and does it resume safely?
11. Play three games in a row. Does each start fresh at level 1?
12. On a phone: does the ship head toward your finger and stop when you let go?
