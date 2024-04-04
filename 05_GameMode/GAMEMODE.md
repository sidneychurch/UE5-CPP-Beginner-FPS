# Game Mode
Typically GameMode is used to set the rules for the type of desired play. We're going to use it so that we can randomly spawn enemies on our map.

If we created our project as a blueprint project, our game mode would be a blueprint. Since we created the project as a C++ one, you should see the header and cpp file in Rider as *YourProjectName*GameMode.
Open both the header and cpp file. We'll start in the header.

### GameMode.h
You'll notice that GameMode is pretty sparse. Let's add some functionality by adding the following below the default constructor:
![img.png](img.png)

