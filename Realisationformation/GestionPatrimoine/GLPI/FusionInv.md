---
title: Fusion Inventory
description: 
published: 1
date: 2022-04-04T15:09:07.667Z
tags: 1.1 gérer le patrimoine informatique, recenser et identifier les ressources numériques
editor: markdown
dateCreated: 2022-04-04T15:09:07.667Z
---

# Compétences
**1.1 Gérer le patrimoine informatique**
- Recenser et identifier les ressources numériques
 
## conseils
# Tabs {.tabset}
## Machine GLPI
Pour commencer il faut tout d'abord avoir une machine GLPI de disponible si vous en avez pas référez vous à la documentation pour faire une installation d'une machine RedHat juste [ici](/Realisationformation/GestionPatrimoine/GLPI/InstallGLPI).

## PuTTY
Il est vivement recommendé d'utiliser l'outil SSH PuTTY qui est téléchargable ci dessous :
https://www.putty.org/

# Le commencement

Pour l'instalation de Fusion Inventory vous pouvez vous referer a la documentation officiel [ici](http://fusioninventory.org/documentation/fi4g/installation.html) mais dans le cadre d'un installation sur une machine [RedHat](/RedHat) les commande sont différente les voici :

Tout d'abord aller dans le répertoire des sources et téléchargez le plugin FusionInventory :
- `cd /usr/src`
- `wget https://github.com/fusioninventory/fusioninventory-for-glpi/releases/download/glpi9.5%2B4.0/fusioninventory-9.5+4.0.tar.bz2`
- `tar -xvf fusioninventory-9.5+4.0.tar.bz2 -C /var/www/html/glpi/plugins`

Puis attribuez les droits d'accès au serveur web
- `chown -R apache /var/www/html/glpi/plugins`

et voilà plus qu'à activer Fusion inventory, pour cela il faut aller dans l'onglet `Configuration` et dans `Plugins` puis cliquer sur le petit icon de puzzle et activer.
![fusioninstalled.png](/images/glpi/fusioninstalled.png)

Ensuite nous allons essayer avec une machine windows 10 et y installer l'agent, voici le lien de [l'agent](https://github.com/fusioninventory/fusioninventory-agent/releases)

Lors de l'installation nous allons entrer les coordonnés du serveur GLPI et sélectionner le lancement automatique de l'agent.
![isntallwin10.png](/images/glpi/isntallwin10.png)

Et voilà le poste apparait dans le GLPI :
![fusion-inv1.png](/images/glpi/fusion-inv1.png)
![fusion-inv2.png](/images/glpi/fusion-inv2.png)
![fusion-inv3.png](/images/glpi/fusion-inv3.png)