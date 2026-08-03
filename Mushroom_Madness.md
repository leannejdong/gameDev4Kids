# Mushroom Madness — Game Documentation & Overview

## 1. Overview & Playable Demo

**Mushroom Madness** is an action-packed survival shooter where players control a character navigating a dynamic arena, dodging falling mushrooms, and blasting them away with star projectiles!

* **Playable Game Link:** [Play Mushroom Madness on Code Camp World](https://play.codecampworld.com/play.html?game=UCWBNR6)
* **Objective:** Defend yourself against endlessly multiplying mushrooms and achieve the highest survival score.
* **Controls:**
  * **Mouse / Pointer:** Point left or right to direct movement.
  * **Click / Tap:** Shoot a star projectile in the facing direction.
  * **Touch Screen:** Tap and hold left/right of the player actor to walk in that direction.

---

## 2. Existing System & Architecture (Current Code)

The starter template includes three primary actors with pre-configured event handlers:

```
                  +-------------------+
                  |   Mushroom Madness |
                  +---------+---------+
                            |
       +--------------------+--------------------+
       |                    |                    |
+------v------+      +------v------+      +------v------+
|    Player   |      |   Mushroom  |      |     Star    |
+-------------+      +-------------+      +-------------+
| - Setup     |      | - Setup     |      | - Setup     |
| - Move      |      | - Direction |      | - Explode   |
| - Moveable  |      | - Speed     |      |             |
| - Throw     |      +-------------+      +-------------+
| - Spawn     |
+-------------+
```

### Actor Breakdown

| Actor | Function | Description |
| :--- | :--- | :--- |
| **Player** | `Setup` | Calculates screen bounds for viewability. Defines tracking variables (`player`, `canThrow`, `canMove`, `facingRight`). |
| | `Move` | Determines target orientation based on pointer location relative to the player. |
| | `Moveable` | Prevents position jittering on non-touch screens when pointer X matches player X. |
| | `Throw` | Spawns a Star actor, sets vector trajectory, enforces a 1-second firing cooldown. |
| | `Spawn` | Spawns dropping mushrooms continuously every 0.4 to 3.0 seconds. |
| **Mushroom**| `Direction`| Flips sprite representation depending on horizontal movement vector. |
| | `Speed` | Maintains constant floor traversal speed upon landing. |
| | `Setup` | Disables inter-mushroom collision; sets randomized move speed (100–250). |
| **Star** | `Setup` | Enables sensor collisions; sets auto-destroy timer to 5 seconds. |
| | `Explode` | Triggers firework animation, halts star movement, destroys target mushroom and self. |

---

## 3. Step-by-Step Coding Guide

### Step 1: Character Orientation & Walking
1. Create a `Direction` custom function inside the **Player** actor.
2. Read the `facingRight` variable:
   * If `true`, set animation state to `Right`.
   * If `false`, set animation state to `Left`.
3. Create a `Walk` function to update X positions based on directional speed.
4. Add a `Stop` function to decelerate player movement when no input is active.

### Step 2: World Physics & Star Shooting
1. Update `Setup` to enable global scene gravity (e.g., `Y Gravity = 1000`).
2. Invoke `Spawn` inside `Setup` to kick off the mushroom multiplication loop.
3. Map mouse click/tap events to invoke the `Throw` custom function.

### Step 3: Collisions, Game Over, & Scoring
1. Implement `Poof` on the **Star** actor: when overlapping a Mushroom, trigger `Explode`.
2. Add collision check between **Player** and **Mushroom**: transition to `Game Over` scene.
3. Build `Restart` function in `Game Over` scene with custom background/tilemap layout.
4. Add global variable `score` (initialized to `0`). Increment score on each successful mushroom explosion and display via a UI text block.

---

## 4. Lesson Wrap-Up & Review

### Key Takeaways & Discussion Questions
* **Q: What did we need to add to make the mushrooms fall down properly?**
  * *A:* We configured global Y gravity to `1000`. (X gravity stayed at `0`).
* **Q: What was the purpose of the `facingRight` variable?**
  * *A:* It tracked current player orientation so projectiles and walking animations faced the correct direction.
* **Q: What stops us from constantly spamming stars without waiting?**
  * *A:* The `canThrow` boolean flag and a 1-second delay timer built into the `Throw` function.

---

<div page-break-before="always"></div>

# Pitch & Educational Enhancement Proposal: Mushroom Madness

### Executive Summary
**Mushroom Madness** introduces students to state management (`canThrow`, `facingRight`), collision matrix handling, and physics gravity. We propose extending this game with boss fights, power-up systems, and dynamic difficulty scaling.

---

### Key Game Enhancements

1. **Mushroom Mutation Engine (Enemy Types):**
   * **Speedy Spore (Yellow):** Moves twice as fast with lower gravity.
   * **Giant Shield Mushroom (Red):** Requires 3 star hits to defeat (`hp = 3`).
   * **Splitter Mushroom (Green):** Splits into two smaller, faster mushrooms when hit.

2. **Upgradable Projectiles:**
   * **Spread Shot:** Shoots three stars in an arc pattern.
   * **Piercing Star:** Passes through up to 3 mushrooms before exploding.

3. **Dynamic Score Multipliers & Visual Polish:**
   * Floating hit indicators (+100 PTS), particle effects on impact, and progressive background color shifts as wave survival time increases.

---

### Curriculum & Pedagogical Value

| Concept | Student Learning Outcome |
| :--- | :--- |
| **State Variables** | Understanding how boolean flags control firing rates and character behavior. |
| **Vector Math & Orientation**| Basic introduction to spatial directions and pointer tracking. |
| **Scene Management** | Transitioning state between main gameplay loop and Game Over screens. |
