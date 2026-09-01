# Sumo

This week we'll be making a sumo game! Who are we? We're the sumo champion! But some challengers have come to take our throne. Oh no! We'll make use of angular movements to make the physics more interesting. Challengers will wandering around the level randomly, and the champion needs to push them off the screen while the challengers push back!

## Intro

https://play.codecampworld.com/play.html?game=MVWZJWM

### How to Play

- Press on the level to move the champion to where you're pressing

- Collide with the challengers to push them out of the level

### Objectives
Push all the challengers outside of the level before the time is up!

## Current Code

### Champion

- Setup

We want to make sure we don't accidentally fly outside of the level!


- Move

Since the function type is when this actor is updated, our actor will constantly try move towards wherever we click in our game. We can hold down or not. Since there's not an else block to stop the champion, we'll keep moving to wherever we pointed to in our level even if we let go of the mouse!

Since we've set the speed to 600, our champion will move quite fast!

### Challenger

- Stalled 

This function is just here to make sure our pandas don't get themselves suck! It'll make sure if they're near a tile, they'll bounce off it!

## Coding

Who are we? We're the sumo champion!

But what's that? Some pandas have challenged us to a sumo match!

We'll make use of angular movements to make the physics more interesting. Challengers will wandering around the level randomly, and the champion needs to push them off the screen while the challengers push back!

## The countdown begins

Under actor Champion, create a function.`Timer`. (don't forget create the variable `timer`)

**New function in:**: Champion

**Type:** When this actor is created

**Name:** Time


* Create the timer variable

### Variable Setup

**Location:** `Code Deck → VARIABLES → Owner Variables`

**Owner:** `this actor`

**Add Variable**

| Field | Value |
|---|---|
| Name | `timer` |
| Default | `20` |

### Steps

1. Click **VARIABLES** in the Code Deck.
2. Under **Owner Variables**, click **+ Add**.
3. Set **Owner** to `this actor`.
4. Set **Name** to `timer`.
5. Set **Default** to `20`.
6. Click **Add / Save**.

> **CHECKPOINT**

Under actor Champion, create a function `Countdown`.


**New function in:**: Champion

**Type:** Every x seconds 

**Name:** Countdown

### Logic

```
Every 1 seconds

Set time to timer -1

if timer < 1 then do the following

Restart the current scene

```

Under actor Champion, create a function `Labels`.


**New function in:**: Champion

**Type:** When this actor is updated

**Name:** Labels

