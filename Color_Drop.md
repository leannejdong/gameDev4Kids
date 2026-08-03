# Color Drop — Game Documentation & Overview

## 1. Overview & Playable Demo

Welcome to **Color Drop**! In this game project, students build an engaging arcade-style color-matching game while learning fundamental programming principles such as function reuse, list management, actor movement, and continuous spawning logic.

* **Playable Game Link:** [Play Color Drop on Code Camp World](https://play.codecampworld.com/play.html?game=KTMSGWV)
* **Objective:** Catch falling color drops in their matching color buckets to earn points!
* **Controls:** 
  * **Desktop:** Use the Left and Right Arrow keys on your keyboard.
  * **Mobile / Touch Devices:** Use the interactive Virtual Controller on screen.
* **Goals:** 
  * Direct falling colors into the correct colored bucket (Red, Green, Blue, Yellow).
  * Aim for the highest score! Center buckets are harder to reach and require quick reaction times.

---

## 2. Existing System & Architecture (Current Code)

The base project includes pre-built structures for **Bucket Actors** handling setup, layout, movement wrapping, and spawning loops.

### Bucket Actors Breakdown

| Function | Description |
| :--- | :--- |
| **`Setup`** | Configures scene parameters: disables gravity for buckets, sets default movement speed, sets global scene gravity, and initializes score label displays. |
| **`VC`** | Enables the Virtual Controller overlay for seamless playability on touch devices. |
| **`Score`** | Dynamically updates and displays score labels corresponding to each bucket/color. |
| **`Reset`** | Implements continuous screen wrapping. If a bucket moves beyond the left edge, it teleports to the right edge, and vice-versa. |
| **`Spawn`** | Handles item spawning cycles. It waits a preset delay and recursively invokes itself to continuously drop items. |
| **`Start`** | Kickstarts game execution. Triggers initial color spawn sequences after a randomized delay (0 to 4 seconds). |

---

## 3. Step-by-Step Coding Guide

### Step 1: Bucket Movement Logic
1. Open the **Red Bucket** actor and create a new custom function named `Move`.
2. Implement key checks:
   * When **Right Arrow / Right Touch** is pressed: apply positive X velocity.
   * When key/touch is released: reset velocity to zero (prevents endless sliding).
3. Copy and apply the verified movement code from the **Red Bucket** to the **Green**, **Blue**, and **Yellow** bucket actors.

### Step 2: Creating Color Actors & Animations
1. Add a new Actor for **Color**.
2. Upload/select sprite sheets for 4 distinct colors (Red, Green, Blue, Yellow).
3. Ensure animation states are named using lowercase conventions matching code definitions (`red`, `green`, `blue`, `yellow`).
4. Implement a `Setup` function on the Color actor.
5. Create a **List** containing available color names to enable randomized picking.

### Step 3: Spawning & Collection Logic
1. **Spawning Drops:** Update the `Spawn` function in the **Red Bucket** to create a Color actor, select a random animation from the color list, and position it at top coordinates.
2. **Collection & Scoring:** Add a `Collect` function on the Red Bucket actor to check collision with falling Color actors. If colors match, increment score; otherwise, trigger reset/penalty.
3. **Replicating Across Buckets:** Copy the completed `Spawn` and `Collect` logic across all bucket actors (Green, Blue, Yellow).

---

## 4. Lesson Wrap-Up & Review

### Key Takeaways & Discussion Questions
* **Q: If I have a function in my Player that I want to copy to a baddie, how would I do that?**
  * *A:* Click the three dots on the top-right of the function block and select "Copy to Actor", choosing your target baddie actor.
* **Q: What is the point of copying a function rather than rebuilding it block by block?**
  * *A:* It saves development time and prevents bugs or accidental discrepancies between actors.
* **Q: How did we use the `New List` block in our code?**
  * *A:* It allowed us to store color options and randomly select one whenever a new drop spawned.
* **Q: What does the code added to the `Spawn` function do?**
  * *A:* It continuously instantiates new color drops at randomized intervals and locations.

---

<div page-break-before="always"></div>

# Pitch & Educational Enhancement Proposal: Color Drop

### Executive Summary
**Color Drop** offers a clean, visually vibrant mechanic ideal for introducing lower-to-mid primary students to list operations and code modularity. To increase student engagement and technical rigor, we propose expanding this core game loop with key enhancements.

---

### Key Game Enhancements

```
+-----------------------------------------------------------------------+
|                       Color Drop Expansion Loop                      |
+-----------------------------------------------------------------------+
|  [ Power-Ups ] --------> [ Dynamic Physics ] -------> [ Combo System] |
|   - Rainbow Bucket        - Gravity Acceleration       - Multipliers  |
|   - Time Freeze           - Wind Effects               - Streaks      |
+-----------------------------------------------------------------------+
```

1. **Power-Up Drops (Special Items):**
   * **Rainbow Drops:** Can be caught by *any* bucket for bonus points.
   * **Freeze Drops:** Temporarily slows down overall gravity for 5 seconds.
2. **Dynamic Physics & Environmental Hazards:**
   * Introduce randomized "Wind gusts" pushing falling drops sideways, requiring players to utilize the screen-wrapping mechanic strategically.
3. **Multiplier & Combo System:**
   * Catching 5 correct colors consecutively triggers a **2x / 3x Point Streak**.

---

### Curriculum & Pedagogical Value

* **Algorithmic Thinking:** Teaches students how list indices work when selecting random items (`List[random_index]`).
* **Code Refactoring & DRY Principle:** Emphasizes *Don't Repeat Yourself* by creating generic functions on one actor and copying/extending them across others.
* **UX & Accessibility Design:** Hands-on experience designing controls for dual platforms (Desktop Keyboard vs. Touch / Virtual Controllers).
