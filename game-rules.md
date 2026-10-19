# Game rules: Drone Dodger

**Version:** rules v4, 2026-10-19 (matches brief v5: per-object speeds)

## Goal (one sentence)

Steer your destroyer through the openings in each falling wave for as long as you can. The second hit ends the round.

## How to play (shown on the start screen)

1. Press **New game**.
2. Hold **←** or **→** to steer. On a phone, hold the left or right side of the screen.
3. Let each wave pass through an opening. Each wave is worth 1 point.
4. You can survive one hit. The second ends the round.

## What the player can do

| Action | Laptop | Phone/tablet | Effect |
| --- | --- | --- | --- |
| Steer left | Hold ← (or A) | Hold the left half of the game area | Moves left at a steady speed while held |
| Steer right | Hold → (or D) | Hold the right half of the game area | Moves right at a steady speed while held |
| Nothing held | — | — | The destroyer stays where it is |
| New game | Click the button, or press Enter or Space | Tap the button | Starts a fresh round |
| Resume after a pause | Space, ← / →, or click | Tap | Continues the paused round |

The game only listens to ← → A D, Space and Enter. Switching tabs or windows releases any held key.

## Waves

- The screen has 6 lanes. A new wave appears at a fixed distance behind the last one.
- Each wave has one **open lane**. The open lane moves at most 2 lanes from the previous one, and every lane in between is also left empty in the new wave. This guarantees a reachable route.
- The other lanes are usually filled with a random mix: drones, missiles, shoes, and airplanes (an airplane takes two neighbouring lanes).
- Every wave has at least one object.
- **Speeds:** drones and shoes fall at 1×, airplanes at 1.5× and missiles at 2×. Faster objects start higher up, off-screen, so all of a wave's objects reach the destroyer's row at the same moment. That keeps the open route reachable.

## Collisions

- A hit happens when the destroyer's body overlaps an object. Hit boxes are a little smaller than the drawings so near-misses feel fair.
- **First hit:** the hull goes 2 → 1 and the destroyer flashes for about 1.5 seconds. It can't be hit while flashing.
- **Second hit** (after the flashing stops): the round ends.
- The left and right edges stop the destroyer and never cause damage.

## Score and speed

- A wave scores **+1** once every object in it is fully below the destroyer. Each wave scores exactly once.
- At 10, 20, 30… points, falling speed rises about 10%, up to a maximum (about double the starting speed). "Faster!" shows for about a second.

## Screens (states)

| State | What you see | Moving? | Score advancing? |
| --- | --- | --- | --- |
| **Start screen** | Title, instructions, last score, top score, New game | No | No |
| **Playing** | Destroyer, falling waves, score, hull | Yes | Yes |
| **Paused** (you switched tabs or windows) | "Paused. Tap or press Space to continue." | No | No |
| **Destroyed** (about 1 second) | "Destroyed!" and the score | No | No |

## Transition table

| From | Action / event | Result |
| --- | --- | --- |
| Page opens | — | Start screen with saved last and top scores (0 if none) |
| Start screen | New game | Playing. Score 0, hull 2, starting speed, destroyer centred and still, first wave after a short calm moment |
| Playing | Hold ← / → (or touch) | Destroyer moves; it stops when released |
| Playing | A wave passes fully below the destroyer | Score +1 |
| Playing | Score reaches 10, 20, 30… | Faster (until the maximum), "Faster!" |
| Playing | Hit, hull 2, not flashing | Hull 1, flashing starts, play continues |
| Playing | Touch while flashing | Nothing happens |
| Playing | Hit, hull 1, not flashing | Destroyed |
| Playing | Tab hidden or window switched | Paused |
| Paused | Space, arrow or tap | Playing again from exactly where it stopped |
| Destroyed | After about 1 second | Start screen. The last score is updated; the top score is updated if beaten, and "New top score!" shows |

## What's kept vs reset between rounds

| Kept | Reset |
| --- | --- |
| Last score, top score (saved on this device) | Score, hull, speed, all falling objects, destroyer position, flashing, pause, messages |

## Partner test cases

Record Passed, Failed, or Not tested for each.

1. Open the page. Are the last and top scores shown, and is nothing moving? Press New game. Is the destroyer centred and still?
2. Hold ←, then →. Does it move each way and stop when you let go? Does it stop at the side edges without losing hull?
3. Let one wave pass. Does the score show exactly 1?
4. Steer into an object. Is the hull 1, does the destroyer flash, and does the game continue?
5. Get hit again after the flashing stops. Does "Destroyed!" appear, then the start screen with that score?
6. Reach 10 points. Does "Faster!" appear, and do objects fall faster?
7. Over a couple of rounds, do you see drones, airplanes, missiles and shoes? Do missiles look fastest, planes faster than drones, and drones and shoes slowest?
8. Is there always an opening you can reach, including after 20+ points?
9. Switch to another tab for 10 seconds and come back. Is it paused, and does it continue safely?
10. Play three rounds in a row. Does each start fresh and at normal speed?
11. Reload the page. Are the last and top scores still there?
12. On a phone: does holding the left or right side steer, and does letting go stop it?
