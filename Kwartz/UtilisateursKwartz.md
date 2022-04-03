---
title: Création des utilisateurs Kwartz
description: 
published: 1
date: 2022-03-25T09:23:43.006Z
tags: 
editor: markdown
dateCreated: 2022-03-24T13:06:07.605Z
---

# Création des utilisateurs Kwartz
 
# Tabs {.tabset}
## Ce connecter sur l'interface du serveur Kwartz
Pour se connecter sur l'interface Kwartz nous choisissons un navigateur internet et dans la barre d'URL nous entrons son adresse et sont port si il en faut un, les adresses par defaut son : 
https://kwartz-server:9999 ou https://192.168.1.254:9999.
 
## Fonctionnement du kwartz avec les utilsateurs
Le serveur Kwartz étant sous Linux il ne peut avoir un Active Directory, c'est pour cela qu'il y a un service LDAP (Lightweight Directory Access Protocol) qui permet de créer un Active Directory avec un Linux.

# Étape 1
 
## S'identifier sur le serveur
Pour s'idendtifier il faut entrer les identifiant définis lors de l'installation du serveur.
![connexion-serveur.png](/images/kwartz/connexion-serveur.png)

# Étape 2
Tout d'abord sélectionner l'onglet " Utilisateurs ",
 
![selection-utilisateurs.png](/images/kwartz/utilisateurs/selection-utilisateurs.png)

Puis vous allez arriver sur une page ou nous devrons sélectionner l'outil " Importer ",
 
![importer.png](/images/kwartz/utilisateurs/importer.png)
 
Pour l'ajout des utilisateur nous devons créer un fichier `.CSV` ou un `.TXT` sous cette forme :
 
## Tabs {.tabset}
### .CSV
![ajout_utilisateur.png](/images/kwartz/utilisateurs/ajout_utilisateur.png)
Ensuite nous pouvons uploader le fichier `.CSV` et l'utiliser pour importer plusieurs utilisateurs en une seul importation
### .TXT
>Nom;Prénom;groupe;login actuel;nouveau login;passe;date de naissance
>LALEU;SULYVAN;2SISR;sulyvan.laleu;sulyvan.laleu;01022002;01/02/2002
{.is-info}

Ensuite nous pouvons uploader le fichier `.TXT` et l'utiliser pour importer plusieurs utilisateurs en une seul importation

## Ajout des utilisateurs fini !
Et voilà vous avez ajouter des utlisateurs sur un serveur Kwartz 🎉.