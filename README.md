# YnovTag

## Contexte

Dans notre société actuelle, **sécuriser ses données** est désormais primordial. Grâce à **YnovTag**, il est désormais possible de **transformer vos données sensibles en image sécurisée !**

Nous utilisons un procédé de **stéganographie**, c'est-à-dire **la dissimulation d'une information** dans un autre fichier pour la rendre **indétectable** à autrui.
Notre objectif est de réaliser une interface **simple** et **intuitive** pour permettre à quiconque, sans nécessairement de connaissances en cybersécurité de **protéger ses données en les transformant en image**.

## Besoin

**YnovTag** a été conçu pour répondre à deux niveaux d'utilisation :

### Niveau 1 : Les utilisateurs simples avec un accès libre ne souhaitant pas créer de compte

- **Chiffrement** : Transformer sa donnée en image contenant le message caché
- **Déchiffrement** : Révéler la donnée cachée de son image

### Niveau 2 : Les utilisateurs ayant un compte

- **Mêmes droits que les utilisateurs de niveau 1**
- **Authentification** : Inscription ou Connexion sécurisée
- **Sauvegardes** : Sauvegarder l'ensemble des données chiffrées pour les retrouver

## Résultat

Désormais, il est possible de chiffrer ses données en les transformant en image.

### Pour ce faire une fois arrivé sur **YnovTag**, plusieurs actions sont possibles : 

- **Si l'on souhaite encoder une donnée** : 

Il vous suffit de cliquer sur le bouton **Encoder mon texte**, cela vous emmène sur la page correspondante, vous entrez votre texte à protéger, vous choisissez ensuite l'image de couverture souhaitée, vous cliquez sur le bouton pour encoder, enfin, votre image est affichée.

- **Si l'on souhaite décoder une image** : 

Cliquez sur le bouton **Décoder mon image**, ensuite vous serez dirigé sur une autre page, vous pourrez importez votre image, enfin, le contenu dissimulé s’affiche.

- **Si l'on souhaite accéder à notre compte** : 

Il faut cliquer sur le bouton **Mon compte**, cela vous emmènera sur votre profil, vous pourrez ensuite modifier vos informations personnelles, et/ou accéder à l'historique.


## Justification des patrons

Pour l'architecture globale on va utiliser le modèle **MVC** pour séparer les responsabilités des classes.

**Patrons utilisés**

- **Patron Singleton**

Nous avons choisi ce patron pour centraliser l'accès aux fichiers. Chaque utilisateur aura son propre fichier JSON (pseudo.json). Ce patron va donc être le gestionnaire d'utilisateurs car c'est lui qui va assurer que chaque utilisateur soit connecté et puisse modifier son repository.

- **Patron Fabrique**

Ce patron va servir à la création des utilisateurs. Au lieu de répéter toutes les étapes de création (hachage mot de passe, historique vide). Il va permettre que tous les utilisateurs soient créés de la même façon et sans risque d'erreur.

- **Patron Façade**

L'algorithme de génération d'image est assez complexe. Nous avons donc choisi de faire une classe qui va faire en sorte que le code web reste propre et lisible. Comme ça en appuyant sur le bouton "Générer mon image cryptée" le contrôleur appellera facilement la méthode.