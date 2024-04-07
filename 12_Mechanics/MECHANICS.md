# Additional Game Mechanics
Here we'll look at some additional mechanics that we could add to the game and how to implement them using C++.

## Reloading: TP_WeaponComponent.h

To add in a reload mechanic we're going to start off in TP_WeaponComponent.h. If you look through the provided classes, you'll notice inputs are split between weapon and character.
*YourProjectName*Character handles character movement and camera controls, while TP_WeaponComponent applies only if the weapon has been picked up.

Inside the WeaponComponent class, you'll find other examples for mapping inputs to actions. We're going to copy this format and add a ReloadAction:

![img.png](img.png)

Let's also add the variables MaxAmmo and CurrentAmmo, as well as a function named Reload. You should see how Reload() mimics Fire().

![img_1.png](img_1.png)

Have Rider generate the definition for Reload, and we'll move in the the character TP_WeaponComponent cpp file.

## Reloading: TP_WeaponComponent.cpp
In the UTP_WeaponComponent constructor, we're going to set our CurrentAmmo to our MaxAmmo amount.

![img_2.png](img_2.png)


We can also do the same for our Reload Function:

![img_3.png](img_3.png)

Now let's go to the Fire function and encapsulate the last three if statements with another if statement. The condition for our if statement makes sure that the firing of a projectile, the firing sound, and the character animation doesn't happen if we're out of ammo. If we do have ammo, we want to remove one everytime the weapon is fired.

![img_4.png](img_4.png)

Now we want to head down to the AttachWeapon function. This is where inputs relating to the weapon are added to the player character when the player picks up the weapon.
At the bottom, you should see where FireAction is being bound as an input component. We want to copy that and change it to also add in our ReloadAction and Reload function.

![img_5.png](img_5.png)

## Reloading: Rider - Build and Reload
Build and Reload. Then go to Unreal.

## Reloading: Unreal Engine - Input Mapping
In the Unreal Content Drawer and inside All > Content > FirstPerson > Input, you'll see two IMC files ( Input Mapping Context ). Default is for character movement and camera controls. Weapons is for when the player picks up the weapon. We want to open up IMC_Weapons.

<img height="50%" src="img_6.png" width="50%"/>

Inside we want to add a new mapping by click on the '+' icon.

![img_7.png](img_7.png)

Then choose to create a new Input Action. For consistency, place it in FirstPerson > Input > Actions, and save it as IA_Reload.

<img height="50%" src="img_8.png" width="50%"/>

Head to that folder and open IA_Reload. Under Action, you should see Triggers. Click the '+' button to add one array element. Set that element to Pressed. Then save IA_Reload.

![img_10.png](img_10.png)

Back in IMC_Weapons, click the arrow beside our new IA_Reload mapping, and map it to the 'R' key on the keyboard. Save IMC_Weapons.

![img_9.png](img_9.png)

Now let's head into FirstPerson > Blueprints and open BP_PickUp_Rifle. Once open, select TP_Weapon from the component list.
![img_11.png](img_11.png)

Then in the Details pane on the right, search for input, and you should see our unmapped Reload Action. Click on "None" and choose our IA_Reload action. 

## Reloading: Unreal Engine - Compile, Save, and Play
Compile and save.

Now when you play the game, you'll see that after you shoot MaxAmmo number of times, you can no longer fire the weapon until you reload.

---
>Prev: [UI for Displaying Player Score](/11_ScoreUI/UI.md)
