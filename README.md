WORKSHOP Unity 3D : Make your first FPS aim train

Hello ! 
We are going to create a basic 3D fps in few steps. 
Each step will contain bonus step to make your game funier and beautiful, but if you never touch Unity, do not feel like
you have to achieve them, and focus on the basic step.
Have fun :)

# Prerequieres :
* Download UNITY HUB
* Add an account or create one
* Add a licence to your unity hub
* Download UNITY 2020 (lts)
* Create a new 3D project

___________________________________

# Step 1 : Create your own character

* Create a capsule3D gameObject, it will represent your main character.
* Take the gun provide on the repository, and attach it to the character.
* Attach a rigidBody component to your character. It will be usefull later to made your player move.
* Attach a Camera to your player to simulate FPS, try to setup your camera to have the better first person view render.

# Step 2 : Made your player move

* Create a c# script, and attach it to the character. This script will handle your character movement (take a look at Input documentation).
* Create another script, attach it to the camera, and made the camera follow the mouse mouvement (horizontaly and vertically).
* For a more realistic FPS change your movement script and try to always walk in direction of where you look.

# Step 3 : Make your player shoot

This step will learn you how to instantiate new object in the scene (Object.Instantiate unity documentation) 

* first thing to do is to create your bullet. Create sphere gameObject, change the size to fit to the gun size.
* Attach a rigidbody component to the bullet
* Now your bullet is create. You just need to grab the bullet in the hierarchie and drop it in your project. It will create a prefab that you will use when shooting.
* Create a new script and attach it to your gun. Now your job is to Instantiate a bullet each time you shoot and made it go to the right direction.
* Pay attention to destroy your bullet each time it touch something or when its too far from your player.

# Step 4 : Create a shooting range

In order to create an aim test, you need to create your shooting range. Take some cube and create your own shooting range. In my case it look like that :

![Alt text](https://github.com/tomasit/Workshop_Unity3D/RdmeImg/shootingRange.png)

