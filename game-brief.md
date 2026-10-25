# Game brief: Drone Dodger

**Project:** DroneDodger (separate from the website and from the course materials)
**Version:** brief v7 (game version 1.1), 2026-10-24

**History:**
- v1: tap to climb, like Flappy Bird.
- v2: added a start screen with last score and top score, and a 2-hit hull.
- v3: steady Up/Down movement with no gravity.
- v4: redesigned as a top-down game with four object types and always a way out.
- v5: each object type falls at its own speed.
- v6: set at sea with a warship, free movement in all four directions, a 3-hit hull, and 3 hand-designed levels.
- v7 (game version 1.1): **endless mode** (no levels, play as long as you survive), sunlit sea surface with wave crests, a long, thin minimal cargo ship (soft cream hull, dark bridge block), a wide, short V-shaped wake, airplanes 10% smaller, drones 10% bigger, and "Version 1.1" on the start screen.

## Concept

You steer a long cargo ship across open water while drones, airplanes, ballistic missiles and the odd flying shoe come at you. There are no levels and no finish line. It keeps getting harder until your hull gives out, and the goal is to beat your top score.

## Intended player

Anyone with a laptop or phone. Early rounds last under a minute. Good runs last several minutes.

## Main action

**Steer in any direction.** The ship stays put until you steer, then moves at a steady speed. It leaves a wide, short V-shaped wake that drifts away with the water.

## Controls

| Device | Steer | New game |
| --- | --- | --- |
| Laptop | Hold the **arrow keys** (W A S D also work). Two keys together move diagonally. | Click the button, or press Enter or Space |
| Phone/tablet | Touch and hold where you want the ship to go | Tap the button |

## Objects

| Object | Size | Speed | Appears from |
| --- | --- | --- | --- |
| Drone | Medium (10% bigger since 1.1) | 1× (slowest) | Start |
| Shoe | Medium | 1× | Start |
| Airplane | Wide, about two lanes (10% smaller since 1.1) | 1.5× | 10 points |
| Ballistic missile | Narrow and tall | 2× (fastest) | 25 points |

Faster objects start further away, so every object in a wave reaches the ship's starting row together.

## How it gets harder

- **Speed:** 8% faster every 10 points, with "Faster!" flashing, up to a top speed of twice the starting speed (reached at 90 points).
- **Crowding:** waves start about half full and fill up steadily until 60 points.
- **New objects:** airplanes join at 10 points and missiles at 25.
- **Always a way out:** the game builds each wave as 6 lanes. The open lane moves at most 2 lanes from the last wave's opening, and every lane in between is kept clear.

All of these numbers sit together at the top of `index.html` under **ENDLESS MODE**, so they're easy to tune.

## A round

1. **Start screen:** title, "Version 1.1", instructions, **last score**, **top score**, **New game**.
2. **Play:** "How far can you go?" shows for a moment, then the waves begin. The top score is shown in the corner during play.
3. **Hits:** the hull has **3 points**. Each hit takes one and gives 1.5 seconds of flashing with no further damage. The **third hit sinks the ship**.
4. **End:** "Sunk!" and the score, then the start screen. It shows "New top score!" if you beat it.

## Scoring

**+1 point** for each wave that gets fully past your ship, counted once. There is no maximum.

## Last score and top score

Saved in this browser on this device. They are not shared and not online. If the browser blocks saving, the game still plays.

## Not in this version (later list, possibly for Drone Dodger 2)

Sound, shooting back, power-ups, hull repair, hand-designed levels, online leaderboard, and accounts.

## Five completion checks

1. **Start and steering:** the start screen shows "Version 1.1" and both scores. After New game, the ship stays still until you steer, and it moves in all four directions.
2. **Score once:** after the first wave passes, the score is exactly 1.
3. **Getting harder:** "Faster!" appears at 10 points, planes appear after 10, and missiles after 25.
4. **Three hits:** the hull goes from 3 to 2 to 1. The third hit shows "Sunk!" and returns to the start screen with that score.
5. **Endless and fair:** the game never ends on its own, every wave has a reachable opening, replays start fresh, and reloading keeps the scores.
