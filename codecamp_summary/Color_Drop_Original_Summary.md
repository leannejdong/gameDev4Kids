# Color Drop — Original Lesson Summary

## Overview & Demo
It's time to show students what they'll be creating this week!
Click [here](https://play.codecampworld.com/play.html?game=KTMSGWV) to play Colour Drop!

## Intro

### How to Play
* Use the left and right arrow keys to move the buckets left and right

### Objectives
* Get the colours in the right buckets
* Try and get the highest score! The middle buckets are the hardest!

When you're done, show them how to log in and where the learn tab is for them to create their game and follow along with the content should they wish to go ahead.

---

## Current Code
What code do we currently have?

### Bucket Actors
* **Setup:** This does a few things! It makes sure our bucket isn't affected by gravity, sets the scene gravity, and the speed the buckets move. It also displays the score labels!
* **VC:** This function is used so that we can use the virtual controller on touch devices.
* **Score:** This function is used to display the current score for each colour.
* **Reset:** If we want our buckets to always be visible, then we need this function! If our bucket goes too far to the left, then it'll appear on the right. If it goes too far to the right, it'll appear on the left!
* **Spawn:** This function is one we'll be adding more code to later! Right now, it just waits a few seconds before calling the Spawn function again (we'll use it to continually spawn colours into our game).
* **Start:** It kickstarts our game! After a random time between 0 and 4 seconds, colours will start falling (once we're done with the code!).

---

## Coding
### The Colours of the Rainbow (or at least 4 of them)
This week, we'll be diving into some more tools we can use in Code Camp World to make our games awesome! Designing levels is important, but that's not all there is! There's also coding! Knowing how to make our game and not have to repeat ourselves is important! Let's get started!

### I Like to Move It Move It
First thing we should do is code up the movement. Let's start with the Red Bucket. We'll look at how to add the same code to the others later!
In order to move using arrows on our keyboard (or the controller on tablets), we need the game to check if we're pressing the left or right key.
If we're pressing right, we should go right! Let's code that up!

1. **Create the Move function** inside the Red Bucket actor.
2. Go to the Move function inside the Red Bucket actor and add the code.
3. *Fix sliding:* We press the right key, we move right. We let go of the key. We still move right!!! Oh no! Let's fix it so the bucket only moves when we're telling it to -> Go to the Move function inside the Red Bucket actor and fix the code.
4. Copy all above functionalities to the **Green**, **Blue**, and **Yellow** bucket actors.
5. **Create the Colour Actor:** Now that we've managed to make our actor move, we can now add the colour actor! We'll be picking any animations we want. But it's important that you name them correctly so that the game will work!
   * Basically, add animation, pick sprite sheets. Pick the right colour sheet and rename it to small letters.
6. Create the **Colour Setup function**.
7. Create a **List** to pick random colours.

### Spawning & Collecting Colours
1. Now we need to actually create our colours in our game! To this end, we'll just need to edit the Red Bucket's `Spawn` code! Go to the Spawn function inside the Red Bucket actor and edit the Spawn code.
2. **Collect the colours:** To this end, we go to the Red Bucket and add a collection function.
3. **Restart:** Edit the collection function to allow restart.
4. Copy all these functionalities we put in the Red Bucket to other bucket actors such as Green, Blue, and Yellow.

---

## Wrap-up

### Take Aways (Questions & Answers)
* **Question:** If I have a function in my Player that I want to copy to a baddie, how would I do that?
  * **Answer:** You just need to copy the function! Go to the function you want to copy, click on the three dots in the top right and copy it to the actor you want (the baddie!).
* **Question:** What's the point of copying a function rather than just redoing it?
  * **Answer:** It saves us time! If our code is working in one actor, it's best not to accidentally make mistakes when copying it block by block in another actor!
* **Question:** How did we use the `New list` block in our code?
  * **Answer:** We used it to pick a random colour when the colour was created!
* **Question:** What does the code we added to the `Spawn` function do?
  * **Answer:** It continually creates colors at intervals to keep the game going!
