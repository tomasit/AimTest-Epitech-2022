WORKSHOP Unity 3D : Créer ton propre aim test en Fps

Salut à tous, 
Pour ce workshop, nous allons apprendre comment faire un 'aim test' en première personne.
Le joueur ainsi que ses déplacements sont déja fournis. 
Le but de ce workshop sera donc de faire un systeme de tir, et de stand de tir avec des cibles dynamiques.

# Prérequis :
* Créez votre compte sur unity (vous avez une licence student avec Epitech)
* Télécharger unity hub [https://unity3d.com/fr/get-unity/download]
* Linkez votre licence sur le unity hub
* Dans le hub : Install -> Add -> installez une version LTS 2020+
* Créez un nouveau projet 3D et drag&drop le contenu du repository dans unity
  dans votre éditeur unity 

# Step 1 : Setup votre arme et vos balles

Nous allons ici découvrir la scène sur laquelle vous allez travailler et setup la balle que nous allons utiliser :
* Cliquez sur 'Scenes/MainScene' pour ouvrir la scene principale.
* Celle-ci est composée d'un stand de tir, d'un joueur déjà setup pour se déplacer avec une vue fps.
* Dans 'Prefab/Bullet/Prefabs/', drag & drop le prefab que vous voulez dans le projet,
  celui-ci est simplement composé d'une balle, et vous allez maintenant le setup pour simuler une vraie balle :
  * clique droit sur l'objet -> prefab -> unpack, pour pouvoir modifier le prefab
  * nous voulons qu'il detecte les collisions, pour se faire, cliquez sur l'objet et dans l'inspector cliquez sur
    'Add component' et tapez collider. Vous devez maintenant choisir le collider le plus adapté pour la balle.
  * Nous voulons maintenant faire en sorte que la balle soit soumise à la physique de l'environnement (poid, gravité...)
    Cliquez sur 'Add Component' et cherchez 'Rigidbody'. Vous pouvez jouer avec les paramêtres du module, mais pour notre
    workshop, les paramêtres de bases sont suffisants.
    
Votre balle est maintenant setup, vous n'avez plus qu'à supprimer l'ancien prefab de balle dans la fenêtre 'project' et
drag & drop votre nouvelle balle dans 'project'.

# Step 2 : Système de tir

Maintenant que nous avons finis le setup global, nous allons créer le script permettant de tirer avec notre arme :
* Dans la fenêtre 'project' -> click droit -> create -> c# script -> l'appeler 'ShootManager'
* drag & drop ce script sur votre arme.
* L'utilité de ce script sera de détecter un input et tirer une balle des que vous appuyez sur celui-ci.
  Pour ce faire, vous devrez suivre ces 3 étapes :
  * Déclarer un 'public GameObject bullet', cela vous permettra de référencer votre préfab de balle directement dans l'éditeur.
  * Détecter quand vous appuyer sur une touche [https://docs.unity3d.com/ScriptReference/Input.html].
  * Ajouter cette ligne pour faire l'animation de tir : "GetComponent<Animator>().SetTrigger("shoot")"
  * Instantier votre balle (a.k.a le GameObject bullet de tout à l'heure) [https://docs.unity3d.com/ScriptReference/Object.Instantiate.html]
  * Donner une force à notre balle pour tirer dans la direction de notre arme (transform.forward ^^). [https://docs.unity3d.com/ScriptReference/Rigidbody.AddForce.html]
  * Sécuriser la destruction de notre balle. En effet, on a pas envie que notre balle reste sur la scene à vie.
    Pour régler ce problème, vous devrez détruire l'objet des que celui-ci touche un autre objet. Mais que se passe t-il
    si l'objet tombe dans le vide ? Vous devrez donc aussi gérer ce cas en donnant par exemple une durée de vie à votre objet.

Vous avez une arme qui tir dans la bonne direction, bien joué!

Etapes Bonus : 
* Créer un système de particule pour le tir / l'impact de la balle quand elle touche quelque chose
* Mettre un sond de tir / impact de la balle
* Faire de l'UI :
  * Nombre de balle qui te reste + système de rechargement

# Step 3 : Créez vos cibles

Vous avez presque finis! Un prefab de cible est disponible dans 'Prefab/Object' mais libre à vous de créer votre propre cible,
le principe reste le même, qui est de créer un script qui va détecter une collision avec un objet spécifique.
Pour ce faire vous aurez besoin de créer un script et de le drag & drop dans votre cible puis de :
* Détecter une collision [https://docs.unity3d.com/ScriptReference/Collider.OnCollisionEnter.html]
* Détecter quel objet est entré en collision en regardant le tag, le layer ou encore le nom de l'objet (c'est la pire méthode)
* Incrémenter un compteur pour le score (Pour l'afficher dans de l'UI par exemple) et détruire la cible.

Faite de cet objet un prefab comme expliqué plus haut.
Nous allons maintenant faire un spawner de cible :
* Dans votre scene : GameObject -> 3D object -> Plane, ce sera votre rectangle sur lequel vos cibles vont spawn
* Faire un objet vide et lui coller le script de spawn
* faire une variable 'public Transform spawnZone' qui referencera le plane que vous venez de faire
* Nous pouvons imaginer plusieurs systèmes de spawn, pour ce workshop nous ferons un système très simple,
  mais si vous voulez faire autrement, vous n'êtes pas obligé de suivre la prochaine partie du tuto :
  * faire un 'private GameObject _cibleReference'
  * Dans Start() faire -> '_cibleReference = Instantiate(...)' pour toujours avoir une référence sur notre cible.
  * Etant donné que la cible s'auto détruit, cela nous permet de respawn notre cible des que la référence est égale à null.

Spawn sur la zone de spawn :
* grâce au mesh collider du plane que vous avez créer, vous pourrez retrouver sa taille (mesh.bounds.size).
* Vous avez remarqués que Instantiate peut prendre en argument une position et une rotation.
  Nous avons donc la position de notre zone de spawn ('spawnZone.transform') ainsi que sa taille. Avec ceci, vous pourez faire spawn vos cibles
  aléatoirement entre la position - (taille / 2) et la position + (taille / 2) sur chaque axes.
  /!\ n'oubliez pas de multiplier la taille par la scale de 'spawnPos'

Vous avez maintenant un spawn aléatoire dans une zone et un système de spawn.
Bien joué à vous, vous avez maintenant une base à améliorer, si vous avez encore du temps, regardez les étapes
bonus, qui rendront votre jeu plus agréable à jouer et plus réaliste.
