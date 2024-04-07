# Enemy AI - Some Tweaks
Right now our enemies are more annoying than challenging. Instead of just moving towards us, what if they chased the player?

The good news is, we've already written the code to accomplish this. We just need to put it in a different spot.

Currently we tell the enemy which direction to go based on the player's current location, but we only do that when we spawn in the enemy. 

Let's take that same logic and update it as long as the enemy is alove.

### EnemyController.h
<img height="33%" src="img.png" width="33%"/>

In the public section of our class, add the function SetDirection. Have Rider generate the definition, and move to the cpp file.

### EnemyController.cpp
In SetDirection, we'll use the same logic as we did when we spawned the enemy in our GameMode. Note the only difference is that we don't need to get our Enemy because, in this file, we are the enemy.

![img_1.png](img_1.png)

Now we can go into the Tick function. We just need to call SetDirection before we update the enemy location.

<img height="50%" src="img_2.png" width="50%"/>

Build and reload the project. When you play the game, now the enemies should chase the player around the level.

---
>Prev: [Super Basic Enemy AI](/06_EnemyAI/AI.md) |  Next: [Enemy Lifespan](/08_Enemy_Lifespan/LIFESPAN.md)
