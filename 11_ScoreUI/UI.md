# Score UI
It doesn't look great outputting our score through debug message, so let's build a simple UI to display that for us.

### Unreal Engine
In the engine, we want to create a new C++ class. When choosing the parent class, choose the All Classes option at the top. Then search for UserWidget.

![img.png](img.png)

Then I chose to call mine ScoreWidget and created the class.

![img_1.png](img_1.png)

### ScoreWidget.h
Inside our widget class header, we only need to add a few things. We need to make a public section, a variable that will store the text for our widget, and a function to update that text.

Since the function is a single line, we can declare it inline and not in the cpp file.

![img_10.png](img_10.png)

### *YourProjectName*GameMode.h
Inside of our GameMode's protected section, we want to create a reference to the widget class that we want to use so that we can spawn it into the game.
We also want to store the widget when it's created so that we can update its text.

![img_3.png](img_3.png)

### *YourProjectName*GameMode.cpp
Inside of our GameMode's BeginPlay function, we want to spawn a widget of the select widget class. Then will store that into a variable and add it to the view port.

![img_4.png](img_4.png)

In the IncreaseScore function, we can comment out the debug message that we were using, and add the following line to pass the current value of score to our widget.

![img_5.png](img_5.png)

Build and reload. Then we'll head to the engine.

### Unreal Engine
Now we need to create a blueprint based on our widget class.

Create a new blueprint class. For the parent class, goto all classes and search for our ScoreWidget

![img_6.png](img_6.png)

I named min BP_ScoreWidget and then opened it.

Inside, choose the Text option from the left. Then drag and drop it into the workspace.

![img_7.png](img_7.png)

In the Details tab on the right, find the Content > Text option. Click on the Bind dropdown beside it. You should see our ScoreText variable.

![img_8.png](img_8.png)

Select it. Compile and Save the widget.

Now we want to open the blueprint for our game mode. You should see the category we made called UMG Score and a dropdown to select a widget class.
In the dropdown, select the blueprint for our score widget.

![img_9.png](img_9.png)

Compile and Save the game mode. You should be able to play the game and have the score UI update as enemies are destroyed.

![img_11.png](img_11.png)