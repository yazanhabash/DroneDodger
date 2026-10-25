# Game brief: Drone Dodger

**Project:** DroneDodger (separate from the website and from the course materials)
**Version:** brief v6, 2026-10-20

**History:**
- v1: tap to climb, like Flappy Bird.
- v2: added a start screen with last score and top score, and a 2-hit hull.
- v3: steady Up/Down movement with no gravity.
- v4: redesigned as a top-down game with four object types and always a way out.
- v5: each object type falls at its own speed.
- v6: set at sea with a warship, free movement in all four directions, a 3-hit hull, and hand-designed levels instead of random waves.

## Concept

You command a warship at sea. Drones, airplanes, ballistic missiles and the odd flying shoe come at you in hand-designed waves. Steer through the gaps and clear every level before your hull gives out.

## Intended player

Anyone with a laptop or phone. A full run through all three levels takes about 4 minutes.

## Main action

**Steer in any direction.** The ship stays put until you steer, then moves at a steady speed. It leaves a foamy wake behind it.

## Controls

| Device | Steer | New game |
| --- | --- | --- |
| Laptop | Hold the **arrow keys** (W A S D also work). Two keys together move diagonally. | Click the button, or press Enter or Space |
| Phone/tablet | Touch and hold where you want the ship to go | Tap the button |

Let go and the ship stops.

## Objects

| Object | Letter in the level design | Size | Speed |
| --- | --- | --- | --- |
| Drone | D | Medium | 1× (slowest) |
| Shoe | S | Medium | 1× |
| Airplane | PP | Wide (two lanes) | 1.5× |
| Ballistic missile | M | Narrow and tall | 2× (fastest) |

Faster objects start further away, so every object in a wave reaches the ship's starting row together.

## Levels

- The game has **3 levels**, played in order: *Calm Waters*, *Air Patrol* and *Missile Storm*.
- Each level is a fixed list of waves written as 6-letter rows, one letter per lane, for example `D..M.D`. The same level plays the same way every time.
- Each level sets its own **speed** and its own **spacing** between waves. Later levels are faster.
- A **level checker** runs when the game loads. It confirms every wave has a reachable way out and lists any problem waves in the browser console.
- Clearing a level shows "Level N cleared!", then the next level starts. Your score, hull and position carry over.
- Clearing level 3 wins the game.

## A round

1. **Start screen:** title, short instructions, **last score**, **top score**, and **New game**.
2. **Play:** each level opens with its name, then the waves arrive.
3. **Hits:** the hull has **3 points**. Each hit takes one, and the ship flashes for 1.5 seconds with no further damage. The **third hit sinks the ship**, and the game is over.
4. **Edges:** the edges of the sea and the score bar stop the ship and never cause damage.
5. **End:** "Sunk!" or "All levels cleared!", then the start screen with the last score and messages such as "New top score!" or "You cleared all 3 levels!"

## Scoring

- **+1 point** for each wave that gets fully past your ship, counted once. Breather rows don't score.
- A perfect run through all three levels scores **50**.

## Last score and top score

Saved in this browser on this device. They are not shared and not online. If the browser blocks saving, the game still plays.

## Not in this version (later list)

Sound, shooting back, power-ups, hull repair, more levels, a level editor screen, choosing a level from the menu, online leaderboard, and accounts.

## Note on the speed-up rule

The earlier "10% faster every 10 points" rule is replaced by per-level speeds, since each level now has a set speed. It can be brought back on top of the level speeds if wanted.

## Five completion checks

1. **Start and steering:** the start screen shows the last and top scores. After New game, the ship stays still, and the arrow keys move it up, down, left and right. Letting go stops it.
2. **Score once:** after the first wave passes, the score is exactly 1.
3. **Three hits:** the hull goes from 3 to 2 to 1 while play continues. The third hit shows "Sunk!" and returns to the start screen with that score.
4. **Levels:** clearing level 1 shows "Level 1 cleared!" and starts *Air Patrol*. Clearing level 3 shows "All levels cleared!"
5. **Fair levels and replay:** every wave has an opening you can reach. Three replays each start fresh at level 1. Reloading keeps the last and top scores.
