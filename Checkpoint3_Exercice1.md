# EXCERCICE 1

## Partie 1 : Gestion des utilisateurs

Q.1.1.1 Créer l'utilisateur Lionel Lemarchand avec les mêmes attributs de société que Kelly Rhameur.

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/comptelionel.png)

Q.1.1.2 Créer une OU DeactivatedUsers et déplace le compte désactivé de Kelly Rhameur dedans.

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/deactivateduser.png)

Q.1.1.3 Modifier le groupe de l'OU dans laquelle était Kelly Rhameur en conséquence.

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/groupelionel.png)

Q.1.1.4 Créer le dossier Individuel du nouvel utilisateur et archive celui de Kelly Rhameur en le suffixant par -ARCHIVE.

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/dossiersindiv.png)



## Partie 2 : Restriction utilisateurs

Q.1.2.1 Faire en sorte que l'utilisateur Gabriel Ghul ne puisse se connecter que du lundi au vendredi, de 7h à 17h.

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/logon.png)

Q.1.2.2 De même, bloquer sa connexion au seul ordinateur CLIENT01.

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/logonto.png)

Q.1.2.3 Mettre en place une stratégie de mot de passe pour durcir les comptes des utilisateurs de l'OU LabUsers.



## Partie 3 : Lecteurs réseaux

Q.1.3.1 Créer une GPO Drive-Mount qui monte les lecteurs E: et F: sur les clients.


Création du partage des dossiers 

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/drivemape.png)
![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/drivemapf.png)

Création de la GPO pour le montage des disques E et F avec liens de la GPO à l'OU LabUsers

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/linkgpo.png)
