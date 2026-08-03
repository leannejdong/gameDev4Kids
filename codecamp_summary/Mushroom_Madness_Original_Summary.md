# Mushroom Madness — Original Lesson Summary

## Intro & Demo
It's time to show students what they'll be creating this week!
Click [here](https://play.codecampworld.com/play.html?game=UCWBNR6) to play Mushroom Madness!

### How to Play
* Move left and right by pointing where to go.
* Tap on the screen to shoot a star.
* On a touch device, tapping & holding to the left or right of the player will make the player move in that direction.

### Objectives
* Stay away from those mushrooms by moving out of their way and feeding them stars!

---

## Current Code
What code is currently in our game?
We have three actors: the **Player**, the **Mushroom**, and the **Star**.

### Player
* **Setup Function:** This function makes sure that no matter how small or large our device is, we will always be able to see our player. In addition, it creates some variables that we'll need to make our game work properly!
  * `player`: used so that we can make sure the mushrooms will follow our actor.
  * `canThrow`: used to decide if we're allowed to shoot a star.
  * `canMove`: used to decide if our player can move towards our mouse.
  * `facingRight`: used for when we want to do different things depending on if our player is facing left or right.
* **Move Function:** Right now, all this function does is tell the game if we should be facing right depending on where the mouse is.
* **Moveable Function:** This function is just to check if our player can move. We need it for when we aren't playing on touch devices. It'll prevent the player from looking like it's "glitching" when the mouse is at the same x position as the player.
* **Throw Function:** This function tells the game what to do when we want to throw a star! First, it'll make sure we can't immediately throw anything else. Then it creates a new star for us to throw. If we're facing right, it'll be thrown right (and vice versa). Then, after 1 second, we'll be allowed to throw another star.
* **Spawn Function:** This is what creates the mushrooms that fall from the sky! After it creates one, it waits between 0.4 and 3 seconds and then creates another.

### Mushroom
* **Direction:** This is a fairly simple function. If the mushroom is moving right, it faces right. Otherwise, it faces left!
* **Speed:** This function just makes sure the mushroom keeps moving once it hits the ground.
* **Setup:** Our code in the Mushroom's setup function ensures that the mushrooms don't hit each other and start rolling around as well as set up the random speed our mushroom will move at. The code says each mushroom will move at a random speed between 100 and 250.

### Star
* **Setup:** This function makes sure our star doesn't start falling into the ground or collide with anything with `Set sensor`. After 5 seconds, we remove the star from the game because we can no longer see it.
* **Explode:** This is what happens when a mushroom goes poof! It'll remove the mushroom, tell the star to stop moving, play the firework animation, and then remove itself from the game 0.5 seconds later.

### Game Over
* **Restart:** This handy dandy function takes us back to the game again. That's it!

---

## Coding
Today, we'll be helping our player do all kinds of things by using **Custom** functions!

### No. THAT Way!
1. First thing we'll do is make sure our player can face the right (or the left) way!
2. Create a `Direction` function inside the player actor.
3. Call the `Direction` function in the `Move` function, test if it works.
4. Create `Walk` function inside the player.
5. Update `Move` function to make it walk. (Oh it doesn't do anything, update the move function and make it move right, then update move function again to move left).
6. **Slow down:** implement `Stop` function.
7. Call the `Spawn` function in `Setup` function to generate mushrooms so they self-produce more mushrooms.

### Physics & Shooting
* **Gravity:** Our two newly added blocks spawn the mushrooms and make sure gravity is in our game. The value of `1000` means that our mushrooms will fall with a speed of 1000. Want them to fall slower or faster? Change gravity!
* **Shooting Stars:** Implement `Shoot Star` function by calling the `Throw` function in player.
* **Making Mushrooms Go POOF:** Create the `Poof` function inside the Star actor using the existing `explode` custom function block in the Star.
* **Game Over:** Program player hit by mushroom leading to `Restart` function to move to the game over scene. Add background and tiles in the game over scene.
* **Scoring:** Create a new game variable `score`, set it to 0. Implement the `Score` function of the player.
* **Extra:** Students add score variable, display score in Player and Game Over scene.

---

## Wrap-up

### Take Aways (Questions & Answers)
* **Question:** What did we need to add to make the mushrooms fall down properly?
  * **Answer:** We added gravity! We set it to 0 for x gravity and 1000 for y gravity.
* **Question:** What was the purpose of the `facingRight` variable?
  * **Answer:** This variable was used to decide the direction we would face and walk.
* **Question:** What stops us from being able to shoot without having to wait?
  * **Answer:** The `canThrow` variable and the 1-second delay in the `Throw` function.
