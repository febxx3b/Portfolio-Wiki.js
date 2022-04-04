---
title: Donner des droits aux utilisateurs
description: 
published: 1
date: 2022-04-03T19:40:12.912Z
tags: 
editor: markdown
dateCreated: 2022-03-28T08:41:44.769Z
---

# Ajout de droits pour les utilisateurs Kwartz
 
## Ce connecter sur l'interface du serveur Kwartz
Pour se connecter sur l'interface Kwartz nous choisissons un navigateur internet et dans la barre d'URL nous entrons son adresse et sont port si il en faut un, les adresses par defaut son :
https://kwartz-server:9999 ou https://192.168.1.254:9999.
 
# Étape 1
 
## S'identifier sur le serveur
Pour s'idendtifier il faut entrer les identifiant définis lors de l'installation du serveur.
![connexion-serveur.png](/images/kwartz/connexion-serveur.png)

# Étape 2
Tout d'abord sélectionner l'onglet " Sécurité ";
 
![selection-securite.png](/images/kwartz/droits/selection-securite.png)
 
Ensuite sélectionner " Nouveau Profil utilisateurs ";
![nouveau-profil.png](/images/kwartz/droits/nouveau-profil.png)
 
Puis donner lui un nom (ex: eleve, profs, winadmin);
![donner-un-nom-de-profil.png](/images/kwartz/droits/donner-un-nom-de-profil.png)
 
Une fois cela fais nous pouvons lui attribuer des règles (exemple sur "eleve");
![regles-pour-eleves.png](/images/kwartz/droits/regles-pour-eleves.png)
 
## Règle autoriser et refuser
# Tabs {.tabset}
## Règle autoriser
![regles-autoriser.png](/images/kwartz/droits/regles-autoriser.png)

## Règle refuser
![regles-refuser.png](/images/kwartz/droits/regles-refuser.png)
 
# Attribution au groupe d'utilisateurs
 
Pour l'attribution de droits il faut tout d'abord créer des groupes et ensuite ajouter les utilisateur les les droits au groupes d'utilisateurs.
Pour commencer sélectionner l'onglet " Utilisateurs ",
 
![selection-utilisateurs.png](/images/kwartz/utilisateurs/selection-utilisateurs.png)

Ensuite nous allons ajouter un groupe et le configurer ;
## Tabs {.tabset}
### Ajouter un groupe
![ajout-groupes-from-user.png](/images/kwartz/droits/ajout-groupes-from-user.png)
### Le configurer
![ajout-groupes.png](/images/kwartz/droits/ajout-groupes.png)
### Exemple
![ajout-groupes-ex-admin.png](/images/kwartz/droits/ajout-groupes-ex-admin.png)
 
## Attribuer les utilisateurs dans les groupes
 
Pour attribuer les utilisateurs dans leur groupes respectif un par un, il faut les ajouter dans la case " Membres ";
![ajout-groupes-users.png](/images/kwartz/droits/ajout-groupes-users.png)

## Ajout des droits sur des utilisateurs fini !
Et voilà vous avez ajouter des droits sur des utlisateurs sur un serveur Kwartz 🎉.