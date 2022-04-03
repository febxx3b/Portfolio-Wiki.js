---
title: Active Directory
description: 
published: 1
date: 2022-03-24T14:56:22.088Z
tags: 
editor: markdown
dateCreated: 2022-02-07T09:24:26.467Z
---

# Installation d'un Active directory

## conseils

### Machine Windows Server
Pour commencer il faut tout d'abord avoir une machine Windows Server de disponible si vous en avez pas référez vous à la documentation pour faire une installation d'une machine Windows Server juste [ici](/WindowsServer2019).

### Server physique
Il est recommendé d'utiliser l'outil RDP ou Gestionnaire de Serveur de windows pour manager plus facilement votre serveur surtout si c'est un serveur physque, cela va vous permettre de le configuerer a distance sa avoir besoin de vous déplacer.


# Le commencement
 
## Étape 1
Une fois l'installation fini vous devrez faire la manipulation suivante celon votre type de machine :

![installation_fin.png](/images/install_winsrv2019/installation_fin.png)

Machine virtuelle
`CTRL + ALT + INSER`

Machine physique
`CTRL + ALT + SUPPR`

Ensuite vous dervez vous connecter avec le mot de passe que vous avez mis à l'étape 4 de l'installation de [WindowsServer2019](/WindowsServer2019)

## Étape 2

Une fois connecter a votre windows .erver, il vous faudra changer son nom et lui attribuer une IP fixe.
Pour cela il vous faudra aller dans l'onglet `Serveur local` du gestionnaire de serveur

![name.png](/images/install_winsrv2019/name.png)

Puis on selectionne le nom de l'ordinateur pour pouvoir le renommer.

![name2.png](/images/install_winsrv2019/name2.png)

## Étape 3

Après avoir renommer le nom du serveur, nous pouvons installer un nouveau rôle au serveur qui est le `services AD DS`
![config4.png](/images/install_winsrv2019/config4.png)
![config5.png](/images/install_winsrv2019/config5.png)
![config6.png](/images/install_winsrv2019/config6.png)
![config7.png](/images/install_winsrv2019/config7.png)
![config8.png](/images/install_winsrv2019/config8.png)

Après l'installation et le redémarrage vous pouvez configurer votre AD. 

## Étape 4

Maintenant vous pouvez créer vos OU, vos groupes, vos utilisateurs, etc... 

![confad1.png](/images/install_winsrv2019/confad1.png)

## Étape 5

Et voilà maintenant votre Active Directory est en place il ne reste plus qu'à l'installer sur vos machines.

> *Documentation faite par Sulyvan Laleu.*

