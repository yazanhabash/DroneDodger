# Game rules: Drone Dodger

**Version:** rules v6, 2026-10-24 (matches brief v7 / game version 1.1: endless mode)

## Goal (one sentence)

Steer your ship through endless, ever-faster waves for as long as you can, and beat your top score before the third hit sinks you.

## How to play (shown on the start screen)

1. Press **New game**.
2. Steer with the **arrow keys**. On a phone, touch and hold where you want to go.
3. Slip through the gaps. Each wave you pass is worth 1 point.
4. Your hull takes 2 hits. The 3rd sinks you.

## What the player can do

| Action | Laptop | Phone/tablet | Effect |
| --- | --- | --- | --- |
| Steer | Hold ↑ ↓ ← → (or W A S D); two keys move diagonally | Touch and hold a spot | Moves at a steady speed |
| Nothing held | — | — | The ship stays where it is |
| New game | Button, Enter or Space | Tap the button | Starts a fresh round |
| Resume after a pause | Space, an arrow key, or click | Tap | Continues from where it stopped |

## Waves

- The sea is split into 6 lanes. A new wave arrives every 280 pixels of travel.
- Each wave has an **open lane** that is at most 2 lanes from the previous wave's open lane, and every lane in between is also kept empty. This guarantees a reachable route.
- Other lanes are filled at random. Waves are about 45% full at the start and 85% full from 60 points onward.
- Object mix: drones and shoes from the start, airplanes (two lanes wide) from 10 points, missiles from 25 points.

## Speed

- Starts at 140. Every 10 points it rises 8%, and "Faster!" shows for a second.
- The top speed is 280, reached at 90 points. After that, the waves stay crowded but don't get faster.
- Drones and shoes move at 1× this speed, airplanes at 1.5× and missiles at 2×. Each wave is timed to reach the ship's starting row together.

## Collisions and hull

- A hit happens when the ship's body overlaps an object. Hit boxes are slightly smaller than the drawings.
- Each hit takes 1 of 3 hull points and makes the ship flash for 1.5 seconds. It can't be hit while flashing.
- The third hit sinks the ship.
- The sea edges and the score bar stop the ship without damage.

## Score

+1 when every object in a wave is below the ship, once per wave. There is no limit.

## Screens (states)

| State | What you see | Moving? |
| --- | --- | --- |
| **Start screen** | "Version 1.1", instructions, last score, top score, New game | No |
| **Playing** | Ship, wake, waves, score, hull (3 boxes), TOP score. "How far can you go?" shows for the first 2.5 seconds | Yes |
| **Paused** (tab or window switched) | "Paused. Tap or press Space to continue." | No |
| **Sunk** (about 1 second) | "Sunk!" and the score | Sea only |

## Transition table

| From | Event | Result |
| --- | --- | --- |
| Start screen | New game | Score 0, hull 3, starting speed, ship centred near the bottom |
| Playing | A wave passes the ship | +1; at every 10 points, faster (until the top speed) |
| Playing | Hit, hull above 1, not flashing | Hull −1, flashing, play continues |
| Playing | Hit, hull 1, not flashing | Sunk |
| Sunk | After about 1 second | Start screen. Last and top scores are updated and saved |
| Playing | Tab or window switched | Paused |
| Paused | Space, arrow key or tap | Playing |

## Kept vs reset

| Kept between games | Reset each new game |
| --- | --- |
| Last score, top score | Score, hull, speed, crowding, ship position, waves, wake |

## Partner test cases

Record Passed, Failed, or Not tested.

1. Does the start screen show "Version 1.1" and the last and top scores?
2. Do all four arrow keys move the ship, and does letting go stop it?
3. Does the ship stop at the edges and at the score bar without damage?
4. After the first wave, is the score exactly 1?
5. At 10 points, does "Faster!" appear? Do planes start appearing after 10, and missiles after 25?
6. Does the hull drop with each hit, and does the third hit show "Sunk!"?
7. Is there always a reachable opening, even after 50+ points?
8. Does the game keep going with no end screen as long as you survive?
9. Does the TOP score in the corner match your best?
10. Switch tabs and come back. Is it paused, and does it resume safely?
11. Play three games in a row. Does each start fresh and slow?
12. On a phone: does the ship head toward your finger?
