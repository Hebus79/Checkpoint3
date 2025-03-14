# Exercice 2 : Manipulations pratiques sur VM Linux (temps estimé : 2h30)


## Partie 1 : Gestion des utilisateurs

Q.2.1.1 Sur le serveur, créer un compte pour ton usage personnel.

Il est possible de créer un compte "fred" avec la commande : sudo adduser -m fred
l'option -m va créer en même temp que le compte le repertoire utilisateur dans /home

Q.2.1.2 Quelles préconisations proposes-tu concernant ce compte ?

Il est préconiser de créer un compte standard avec un mot de passe robuste, ne faisant pas parti du groupe administrateur mais faisant parti d'un autre groupe
Pour configurer un mot de passe pour l'utilisateur fred, utiliser la commande : sudo passwd fred
Pour mettre l'utilisateur fred dans le groupe utilisateurs : sudo usermod -aG users fred


## Partie 2 : Configuration de SSH

Un serveur SSH est lancé sur le port par défaut.
Il est possible de s'y connecter avec n'importe quel compte, y compris le compte root.

Q.2.2.1 Désactiver complètement l'accès à distance de l'utilisateur root.

Il est possible de désactiver complètement l'accès à distance de l'utilisateur root en modifiant le fichier de configuration "sshd_config" dans le repertoire /etc/ssh/
Il faut ensuite ajouter ou decommenter la ligne : PermitRootLogin prohibit-password
A noter qu'il est préférable de mettre les nouvelles lignes ou decommenter dans un nouveau fichier .conf dans le repertoire sshd_config.d
Pour éviter de perdre la config au reboot du serveur.

Q.2.2.2 Autoriser l'accès à distance à ton compte personnel uniquement.

Toujours dans le fichier "sshd_config", il faut ajouter la ligne : AllowUsers fred


Q.2.2.3 Mettre en place une authentification par clé valide et désactiver l'authentification par mot de passe


a) Toujours dans le fichier "sshd_config", il faut ajouter la ligne : PubkeyAuthentication yes
et : PasswordAuthentication no

b) Générer une clé en 4096 bits sur le client : ssh-keygen -b 4096

c) Copier la clé sur le serveur SSH : login en SSH depuis le client sur le serveur puis "ssh-copy-id root@adresse IP serveur"

d) Depuis le client, vérification de la configuration du serveur après Redémarrage (ou systemctl restart sshd.service) :

ssh fredr@adresse IP serveur

S'assurer que la connection par clef fonctionne avant de désactiver l'authentification par mot de passe.


## Partie 3 : Analyse du stockage

Q.2.3.1 Quels sont les systèmes de fichiers actuellement montés ?

Nous pouvons voir quels sont les systèmes de fichiers montés grâce à la commande df-k ou lsblk

![Checkpoint3](https://github.com/Hebus79/Checkpoint3/blob/main/images/lsblk.png)

Donc : sur un disque /dev/sda nous pouvons voir une partition primaire md0 en raid 1 et des partitions secondaires md0p1,md0p2 et md0p5
Le système à été installé en utilisant lvm


Q.2.3.2 Quel type de système de stockage ils utilisent ?

Q.2.3.3 Ajouter un nouveau disque de 8,00 Gio au serveur et réparer le volume RAID

Q.2.3.4 Ajouter un nouveau volume logique LVM de 2 Gio qui servira à héberger des sauvegardes. Ce volume doit être monté automatiquement à chaque démarrage dans l'emplacement par défaut : /var/lib/bareos/storage.

Q.2.3.5 Combien d'espace disponible reste-t-il dans le groupe de volume ?

## Partie 4 : Sauvegardes

Le logiciel bareos est installé sur le serveur.
Les composants bareos-dir, bareos-sd et bareos-fd sont installés avec une configuration par défaut.

Q.2.4.1 Expliquer succinctement les rôles respectifs des 3 composants bareos installés sur la VM.

## Partie 5 : Filtrage et analyse réseau

Q.2.5.1 Quelles sont actuellement les règles appliquées sur Netfilter ?

Q.2.5.2 Quels types de communications sont autorisées ?

Q.2.5.3 Quels types sont interdit ?

Q.2.5.4 Sur nftables, ajouter les règles nécessaires pour autoriser bareos à communiquer avec les clients bareos potentiellement présents sur l'ensemble des machines du réseau local sur lequel se trouve le serveur.


## Partie 6 : Analyse de logs

Q.2.6.1 Lister les 10 derniers échecs de connexion ayant eu lieu sur le serveur en indiquant pour chacun :

  La date et l'heure de la tentative
  L'adresse IP de la machine ayant fait la tentative


