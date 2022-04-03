---
title: Ajout d'une imprimante
description: 
published: 1
date: 2022-03-25T09:37:41.745Z
tags: 
editor: markdown
dateCreated: 2022-03-24T13:57:15.182Z
---

# Ajout d'une imprimante sur le réseau Kwartz
# Tabs {.tabset}
## Ce connecter sur l'interface du serveur Kwartz
Pour se connecter sur l'interface Kwartz nous choisissons un navigateur internet et dans la barre d'URL nous entrons son adresse et sont port si il en faut un, les adresses par defaut son :
https://kwartz-server:9999 ou https://192.168.1.254:9999.

## Avant de commencer
Avant d'ajouter sur le serveur Kwartz une imprimante il faut tout d'abord la configurer avec une adresse IpV4 et par la suite il faut récupérer son adresse MAC, sont adresse IP doit être noter de la façon suivante :
### Exemple de notation
`172`.`16`. `le numéro de la salle` . `l'adresse suivant la dernière` 
### Exemple d'utilisation
`172`.`16`.`203`.`12` 
 
# Étape 1
 
## S'identifier sur le serveur
Pour s'idendtifier il faut entrer les identifiant définis lors de l'installation du serveur.
![connexion-serveur.png](/images/kwartz/connexion-serveur.png)

# Étape 2
Tout d'abord sélectionner l'onglet " Services ",
 
![selection-services.png](/images/kwartz/imprimante/selection-services.png)
 
Puis on sélectionne " Ajouter une imprimante "
 
![selection-addimp.png](/images/kwartz/imprimante/selection-addimp.png)
 
# Étape 3
En suite nous devons enregistrer l'imprimante dans le réseau, il faut lui donner un nom et noté son adresse IP.
 
![ajout_d'une_imprimante.png](/images/kwartz/imprimante/ajout_d'une_imprimante.png)
 
# Étape 4
Afin de l'ajouter correctement et de savoir ou elle se situe nous allons l'ajouter dans un groupe, pour cela il faut aller dans l'onglet " Réseau " et ajouter un nouveau poste en sélectionant sont emplacement.

![addgroupe.png](/images/kwartz/imprimante/addgroupe.png)
 
Et pour finir il ne reste plus qu'à entrer la configuration en sélectionnant bien la catégorie " Imprimante " et sélectionner le groupe de son appartenance.
 
![config-imprimante.png](/images/kwartz/imprimante/config-imprimante.png)

## Ajout d'une imprimante sur le réseau Kwartz fini !
Et voilà vous avez ajouté d'une imprimante sur le réseau Kwartz 🎉.