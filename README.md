WORKSHOP Unity 3D : Make your first FPS aim test

Salut à tous, 
Pour ce workshop, nous allons apprendre comment faire un 'aim test' en première personne.
Le joueur ainsi que ses déplacements sont déja fournis. 
Le but de ce workshop sera donc de faire un systeme de tir, de visé et de stand de tir avec
des cibles dynamiques.

# Prérequis :
* Créez votre compte sur unity (vous avez une licence student avec Epitech)
* Télécharger unity hub [https://unity3d.com/fr/get-unity/download]
* Linkez votre licence sur le unity hub
* Dans le hub : Install -> Add -> installez une version LTS 2020+
* Créez un nouveau projet 3D et drag&drop le contenu du dossier préfab du repository
  dans votre éditeur unity 

___________________________________

# Step 1 : Create your own character

* Create a capsule3D gameObject, it will represent your main character.
* Take the gun provide on the repository, and attach it to the character.
* Attach a rigidBody component to your character. It will be usefull later to made your player move.
* Attach a Camera to your player to simulate FPS, try to setup your camera to have the better first person view render.

![alt text](https://github.com/tomasit/Workshop_Unity3D/blob/master/RdmeImg/simpleCharacte.png)

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

![alt text](https://github.com/tomasit/Workshop_Unity3D/blob/master/RdmeImg/shootingRange.png)

# Step 5 : Create target

Last thing to do is to create targets. With everything you have learn, there is a multiple way to achieve that. But you have to follow two rules :
- always have at least one target.
- the spawn position of the target have to be random

