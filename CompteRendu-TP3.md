# Compte rendu TP3 - Gestion des paquets

## Exercice 1. Commandes de base


1. La commande permettant de visualiser les 5 derniers paquets installer sur la machine est: dpkg -l | tail -n 5. 
On y trouve: xkb-data, xxd, xz-utils, zerofree, zlib1g:amd64.

2. Afin de compter le nombre de paquets installés avec apt, nous utilisons la commande *apt list --installed*. Chaque ligne correspond à un paquet. Afin de compter le nombre de ligne on complete la commande avec *| wc -l*. On trouve 544 lignes avec cette commande.
Afin de compter le nombre de paquets installés avec dpkg, nous utilisons la commande *dpkg -l*. Chaque ligne correspond à un paquet. Afin de compter le nombre de ligne on complete la commande avec *| wc -l*. On trouve 548 lignes avec cette commande.
La différence entre les deux commandes est due au premieres lignes de dpkg qui ne sont pas des paquets mais des informations générales.

3. Il y a 61598 paquets disponibles en téléchargement. Nous obtenons le nombre de paquets grâce à la commande *apt-cache pkgnames  | wc -l*.

4. On crée un alias qui met à jour le système grâce à la commande: *alias maj='sudo apt-get update && sudo apt-get upgrade'*.

5. Le paquet fortunes est un programme affichant aléatoirement des épigrammes, connus sous le nom de cookies fortune. Nous affichons les détails de ce paquet avec la commande *apt show fortunes*.
Nous installons ensuite le paquet grâce à la commande *sudo apt install fortunes*. 

6. Nous utilisons la commande *apt search sudoku* afin d'afficher les paquets proposant de jouer au sudoku. Nous trouvons 11 paquets: fltk1.1-games, fltk1.3-games, gnome-sudoku, hitori, ksudoku, libqqwing-dev, libqqwing2v5, nudoku, qqwing, sudoku, texlive-games.

7. Pour lister les paquets installés explicitement avec la commande *apt install* nous utilisons la commande *cat /var/log/apt/history.log | grep 'apt install'*


## Exercice 2

Afin de connaitre le paquet a partir duquel la commande ls est installée on utilise la commande *dpkg -S $(which -a ls)*. Cette commande nous renvoie deux lignes, une erreur et le paquet dans lequel ls est installé: coreutils.

script : 
> #!/bin/bash

> echo $(dpkg -S $(which -a $1))


## Exercice 3

> if  [ $(dpkg -s $1 | grep 'Status' | cut -d "k" -f 2) = "installed" ] ; 
>then 
>echo "Installé"
>else
>echo "non installé"
>fi

## Exercice 4 

Pour afficher toutes les commandes fournies avec le package coreutils, on utilise la commande : 
> dpkg -L coreutis

La commande '[' est un alias de test et doit se terminer par ']'
