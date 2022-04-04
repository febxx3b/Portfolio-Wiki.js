---
title: Image Pulse
description: 
published: 1
date: 2022-03-25T09:43:01.924Z
tags: 
editor: markdown
dateCreated: 2022-03-24T11:29:45.566Z
---

# Création d'une image avec Pulse
 
# Tabs {.tabset}
## Ce connecter sur l'interface du serveur Kwartz
Pour se connecter sur l'interface Kwartz nous choisissons un navigateur internet et dans la barre d'URL nous entrons son adresse et sont port si il en faut un, les adresses par defaut son :
https://kwartz-server:9999 ou https://192.168.1.254:9999.

## Plus d'informaions sur Pulse
Sur Kwartz le service Pulse permet de créer et de gérer des images pour des postes sous Windows 10 uniquement.
 
## Avant de commencer
Avant de faire une images nous devons installer toutes les mise a jours des logiciels pouvent en avoir une.
Pour les postes dont il faut faire une nouvelle installation il faut suivre le documentation de l'académie de Lille.

Sur les navigateur de recherche (Chrome,Firefox,Edge,etc...) nous devons désactiver l'enregistrement automatique des mots de passes, des adresses et des informations banquaires puis il faut supprimer l'historique, les cookies et les données de navigations à chaque fermeture des navigateurs.

## Documentation de l'Académie de Lille
Pour la création ou une mise a niveau d'une image Windows 10 il faut suivre la documention donner par l'Académie de Lille voici le lien : https://www.ac-lille.fr/daip/pole-pedagogie/fiches-techniques/poste-client-windows/creation-dimages-pulse/preparation-du-poste-sous-windows-10 
 
# Étape 1
 
## S'identifier sur le serveur
Pour s'idendtifier il faut entrer les identifiant définis lors de l'installation du serveur.
![connexion-serveur.png](/images/kwartz/connexion-serveur.png)

# Étape 2
Tout d'abord sélectionner l'onglet " Réseau ",
 
![selection-réseau.png](/images/kwartz/images/selection-réseau.png)
 
Ensuite sélectionner l'outil " Images Pulse ",
![selection_rembo.png](/images/kwartz/images/pulse/selection_pulse.png)
 
Puis vous allez arriver sur une page où l'on doit choisir le nom de l'image à créer puis nous devons choisir le poste qui servira à créer l'image, puis cliquer sur OK.
![rembo.png](/images/kwartz/images/pulse/pulse.png)
 
Une fois cela fait il faut simplement redémarrer le poste en question et lancer le poste en PXE avec la touche <kbd>F12</kbd> puis sélectionner " IpV4 " et le poste va automatiquement lancer la création de l'image.
 
# Étape 3
 
## Le déploiement d'images sur une salle
Pour le déploiement d'une image dans une salle nous allons sélectionner le groupe dans l'onglet réseau puis nous allons choisir qu'elle image lui donner.
![selection_groupe.png](/images/kwartz/images/pulse/selection_groupe.png)
 
Une fois cela fait il faut simplement redémarrer tous les postes de la salle et lancer les postes en PXE avec la touche <kbd>F12</kbd> puis sélectionner " IpV4 " et les postes vont automatiquement lancer l'installation de l'image,il est conseiler de les faire deux par deux voir même un par un si le réseau local est lent.
 
## Déploiement d'une image Pulse fini !
Et voilà vous avez déployer une image dans une salle 🎉.