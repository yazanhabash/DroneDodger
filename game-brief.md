# Game brief: Drone Dodger

**Project:** DroneDodger (separate from the website and from the course materials)
**Version:** brief v4, 2026-10-19

**History:**
- v1: tap to climb, like Flappy Bird.
- v2: added a start screen with last score and top score, and a 2-hit hull.
- v3: steady Up/Down movement with no gravity.
- v4: redesigned as a top-down game. Objects fall from the top, you steer left and right, there are four object types, and there is always a way out.

## Concept

Your destroyer is at the bottom of the screen. Waves of drones, airplanes, ballistic missiles and the odd flying shoe fall toward you. Steer left and right through the openings, survive one hit, and see how far you get before everything speeds up.

## Intended player

Anyone with a laptop or phone. Rounds last from under a minute to a few minutes.

## Main action

**Steer left or right.** The destroyer stays put until you hold a direction, then moves at a steady speed. It can't move up or down.

## Controls

| Device | Steer | New game |
| --- | --- | --- |
| Laptop | Hold **← / →** (A / D also work) | Click the button, or press Enter or Space |
| Phone/tablet | Hold the left or right half of the game area | Tap the button |

Let go and the destroyer stops.

## Falling objects

| Object | Look | Size |
| --- | --- | --- |
| Drone | Four-rotor drone with a red eye | Medium |
| Airplane | Plane seen from above | Wide (two lanes) |
| Ballistic missile | Thin missile with a flame trail | Narrow and tall |
| Shoe | A tumbling sneaker, just for fun | Medium |

All objects in a wave fall at the same speed. They only look different. They are not separate game rules.

## Waves and the way out

- The screen is split into 6 invisible lanes.
- Each wave is a row of mixed objects, slightly staggered.
- **Every wave has an open lane**, and the route to it from the previous wave's opening is kept clear. That means there is always a path you can reach in time, even at top speed.

## A round

1. **Start screen** (shown when the page opens and after every round): title, short instructions, **last score**, **top score**, and a **New game** button. Nothing moves until you press New game.
2. **Play:** waves fall from the top. Steer through the openings.
3. **Hits:** the destroyer has **2 hull points**, shown on screen.
   - **First hit:** you survive. The hull drops to 1, and the destroyer flashes. For about 1.5 seconds you can't be hit again.
   - **Second hit:** "Destroyed!", then back to the start screen.
4. **Side edges** stop the destroyer like walls and don't damage it.
5. **Round over:** the start screen shows this round's score as the last score, and "New top score!" if you beat it.
6. **New game:** a completely fresh round. Score 0, hull 2, starting speed, no objects on screen, destroyer in the middle.

## Scoring and speed

- **+1 point** for each wave that gets completely past you, counted once, even if it hit you.
- At **10, 20, 30… points**, everything falls about 10% faster, up to a maximum. "Faster!" flashes when this happens.

## Last score and top score

- Saved in this browser on this device. They are still there after you close and reopen the page.
- They are not shared with other people or devices. This is not an online leaderboard.
- If the browser blocks saving (for example, in a private window), the game still works. The scores just won't be remembered.

## Look (first version)

Simple shapes drawn by the game itself: a starfield, a grey destroyer seen from above, and the four object types. No sound, no downloaded images, no external libraries.

## Not in the first version (later list)

Sound, shooting back, power-ups, hull repair, objects with different speeds or zig-zag paths, levels, online leaderboard, accounts, multiplayer, and purchases.

## Five completion checks

Record each one as Passed, Failed, or Not tested.

1. **Start screen and controls:** Open the page. You see the last score, top score and New game, and nothing moves. After New game, the destroyer stays still with no keys pressed. Holding ← or → moves it, and letting go stops it.
2. **Score once:** Let one wave get past you. The score goes from 0 to exactly 1.
3. **Two hits:** Steer into an object. The hull drops to 1, the destroyer flashes, and the game continues. Get hit again after the flashing stops. "Destroyed!" appears, then the start screen shows that score as the last score.
4. **Speed-up:** Reach 10 points. "Faster!" appears, and objects visibly fall faster.
5. **Replay, saved scores and variety:** Play three rounds in a row. Each starts fresh and at normal speed. You see all four object types. There is always an opening you can reach. Reload the page, and the last and top scores are still there.
