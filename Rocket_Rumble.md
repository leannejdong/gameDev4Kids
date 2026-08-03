# Rocket Rumble — Game Documentation & Overview

## 1. Overview & Playable Demo

**Rocket Rumble** is a level-based action game where players pilot a rocket/character through custom tilemap levels, avoiding obstacles, handling tile collision mechanics, and collecting items to progress!

* **Playable Game Link:** [Play Rocket Rumble on Code Camp World](https://play.codecampworld.com/play.html?game=LBMMWVZ)
* **Objective:** Navigate through Level 1 and Level 2, collect all coins, avoid hazard tiles, and trigger the level progression loop.
* **Controls:**
  * **Arrow Keys / WASD:** Move player left, right, up, and down.
* **Goals:**
  * Collect every coin placed in the level.
  * Avoid solid walls and hazard tiles that reset player position.

---

## 2. Existing System & Week 1 Lesson Plan Breakdown

```
                             +------------------------+
                             |     Rocket Rumble      |
                             +-----------+------------+
                                         |
         +-------------------------------+-------------------------------+
         |                               |                               |
+--------v--------+             +--------v--------+             +--------v--------+
|   Tilemap & Map |             |  Player Actor   |             |  Collectibles   |
+-----------------+             +-----------------+             +-----------------+
| - Background    |             | - hitTile()     |             | - Coin Actors   |
| - Tile Grid     |             | - collect()     |             | - Value/Points  |
| - Collisions    |             | - nextLevel()   |             +-----------------+
+-----------------+             +-----------------+
```

### Stage-by-Stage Curriculum Outline

| Stage | Activity | Key Engine Mechanic |
| :--- | :--- | :--- |
| **1. World Setup** | Select background, build tilemap layer | Tiles default to solid collision (`collides = true`). Disable collision on passable tiles. |
| **2. Actor Setup** | Create Player & Assign animations | Place Player onto initial starting position grid. |
| **3. Event Logic** | Implement `hitTile`, `collect`, `nextLevel` | Scoped player callbacks handling hazard resets, score updates, and scene transitions. |
| **4. Expansion** | Construct Level 2 scene | Manual coin placement, level design customization, and player movement tuning. |

---

## 3. Detailed Step-by-Step Implementation Guide

### Step 1: Tilemaps & Collision Toggling
1. Load Level 1 background and select tile sprites.
2. Paint structural wall tiles and passable floor tiles onto the matrix grid.
3. **Collision Rule:** All tiles default to solid. Toggle collision state to *off* for floor/pathway tiles so the player can pass through.

### Step 2: Player Logic (`hitTile`, `collect`, `nextLevel`)
1. **`hitTile` Function:** Detect tile collisions. If the player hits a hazard tile, trigger position reset or health penalty.
2. **`collect` Function:** Check overlaps with collectible coin actors. On collision, destroy the coin actor and increment global score.
3. **`nextLevel` Function:** Count remaining collectibles. When 0 coins remain or player reaches portal, trigger scene transition to Level 2.

### Step 3: Level 2 Design & Tuning
1. Create Level 2 scene with unique background and custom tile placement.
2. Manually spawn coins and collectibles across the scene.
3. Fine-tune player movement speed and acceleration.

---

## 4. Lesson Wrap-Up & Discussion Questions

### Key Takeaways
* **Q: How do tile collisions work by default in Code Camp World?**
  * *A:* Tiles are solid by default. To make a tile passable, you must manually remove its collision setting.
* **Q: Why do we manually place coins in Level 2 instead of relying on auto-generation?**
  * *A:* It gives students direct control over level design and difficulty balancing.
* **Q: What triggers the `nextLevel` function?**
  * *A:* Collecting all coins or reaching a designated trigger area in the active scene.

---

<div page-break-before="always"></div>

# Pitch & Educational Enhancement Proposal: Rocket Rumble

### Executive Summary
**Rocket Rumble** provides students with foundational knowledge of level design, tile collision masking, and scene management. We propose expanding this core structure into a feature-packed arcade experience with dynamic hazards, power-ups, and custom level sharing.

---

### Key Game Enhancements

```
+---------------------------------------------------------------------------------+
|                           Rocket Rumble Engine Upgrades                         |
+---------------------------------------------------------------------------------+
|  [ Dynamic Hazards ]  --->  [ Power-Up Mechanics ] ---->  [ Custom Level Editor]|
|   - Moving Lasers           - Speed Boosts                 - Student Code-Sharing|
|   - Crumbling Tiles         - Invincibility Shields        - Community Leaderboard|
+---------------------------------------------------------------------------------+
```

1. **Dynamic Tile Hazards:**
   * **Crumbling Tiles:** Platform tiles that disappear 1 second after player steps on them.
   * **Laser Traps:** Timed energy beams that switch between solid/hazardous states.
2. **Collectible Power-Ups:**
   * **Magnet Pickup:** Attracts nearby coins automatically within a 5-tile radius.
   * **Dash Thruster:** Grants temporary invincibility and speed boost to break through fragile wall tiles.
3. **Level Sharing & Community Showcase:**
   * Allow students to export level matrix data to feature their custom Level 2 creations on the main Code Camp World platform.

---

### Curriculum & Pedagogical Value

| Concept | Student Learning Outcome |
| :--- | :--- |
| **Grid Matrix & Collision Flags** | Understanding 2D grid coordinates and boolean collision properties. |
| **Event-Driven Mechanics** | Linking actor lifecycle events (`hitTile`, `collect`) to scene states. |
| **UX & Level Balancing** | Designing challenging yet fair level layouts for peers. |
