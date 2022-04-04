---
title: Installation GLPI
description: 
published: 1
date: 2022-04-04T14:30:20.803Z
tags: 1.1 gérer le patrimoine informatique, 1.5 mettre à disposition des utilisateurs un service informatique, déployer un service, recenser et identifier les ressources numériques
editor: markdown
dateCreated: 2022-04-04T13:16:14.362Z
---

# Compétences
**1.1 Gérer le patrimoine informatique**
- Recenser et identifier les ressources numériques

**1.5 Mettre à disposition des utilisateurs un service informatique**
- Déployer un service
 
## conseils
# Tabs {.tabset}
## Machine RedHat
Pour commencer il faut tout d'abord avoir une machine RedHat de disponible si vous en avez pas référez vous à la documentation pour faire une installation d'une machine RedHat juste [ici](/RedHat).

## PuTTY
Il est vivement recommendé d'utiliser l'outil SSH PuTTY qui est téléchargable ci dessous :
https://www.putty.org/

# Le commencement

## Le repository High Availability
Pour commencer il faut activer la repository High Availability grâce a la commande suivante :

`subscription-manager repos --enable=rhel-8-for-x86_64-highavailability-rpms`

## Installation des paquets et des repository
### tout d'abort il faut être en root
`sudo su` puis votre mot de passe.

![sudo_su.png](/images/glpi/sudo_su.png)
> Attention ! De grands pouvoirs confèrent de grandes responsabilités.
{.is-info}
### les repository
- `yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm`
- `dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm`
### Les paquets pour cockpit
- `dnf install cockpit`
activer cockpit :
- `systemctl enable --now cockpit.socket `

- `dnf module reset php`
- `dnf module install php:remi-7.4`
- `dnf install httpd mariadb-server php php-{curl,fileinfo,gd,json,mbstring,mysqli,session,zlib,simplexml,xml,cli,domxml,imap,ldap,openssl,xmlrpc,pecl-apcu} wget tar zip bzip2`
- `nano /etc/php.ini`
configurer mariadb :
- `systemctl enable --now mariadb `
on peut vérifer son fonctionnement avec cette commande :
- `systemctl status mariadb`
configurer la base de donnée :
- `mysql_secure_installation `
donner vous un mot de passe root puis toujours autoriser les action demander.
une fois cela fait il faut créer une base de donnée et un utilisateur :
- `create database glpidb;`
- `grant all on glpidb.* to glpiadmin@localhost identified by 'myP@ssw0rd';`
- `flush privileges;`
et voilà plus qu'à quitté mariadb
- `bye`
Ensuite nous allons télécharger GLPI et l'installer :
- `wget https://github.com/glpi-project/glpi/releases/download/9.5.1/glpi-9.5.1.tgz`
- `tar xzf glpi-9.5.1.tgz -C /var/www/html/`
- `ls /var/www/html/`
- `chown -R apache:apache  /var/www/html/glpi`
- `chmod -R 755 /var/www/html/glpi`
maintenant nous allons configurer l'acces au GLPI :
- `nano /etc/httpd/conf.d/glpi.conf `

> <VirtualHost *:80>
⠀⠀⠀⠀⠀⠀⠀⠀ServerName [le nom de la machine ex: local.host]
⠀⠀⠀⠀⠀⠀⠀⠀DocumentRoot /var/www/html/glpi
⠀⠀⠀⠀⠀⠀⠀⠀ErrorLog "/var/log/httpd/glpi_error.log"
⠀⠀⠀⠀⠀⠀⠀⠀CustomLog "/var/log/httpd/glpi_access.log" combined
⠀⠀⠀⠀⠀⠀⠀⠀< Directory > /var/www/html/glpi/config>
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀AllowOverride None
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀Require all denied
⠀⠀⠀⠀⠀⠀⠀⠀< /Directory >
⠀⠀⠀⠀⠀⠀⠀⠀< Directory > /var/www/html/glpi/files>
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀AllowOverride None
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀Require all denied
⠀⠀⠀⠀⠀⠀⠀⠀< /Directory >
< /VirtualHost >
>
#### retirer les espaces dans : < Directory >, < /Directory > et < /VirtualHost >.
ensuite nous allons tester si tout cela fonctionne :
- `httpd -t`

![httpd-ok.png](/images/glpi/httpd-ok.png)

une fois cela fait il faut le démarrer automatiquement :
- `systemctl enable --now httpd`
on peut vérifer son fonctionnement avec cette commande :
- `systemctl status httpd`
il ne reste plus qu'à autorisuer le pare-feu et le Se Linux :
pare-feu :
- `firewall-cmd --add-port={80,443}/tcp --permanent`
- `firewall-cmd --reload`
Se Linux :
- `setsebool -P httpd_unified 1`
- `setsebool -P httpd_can_network_connect 1`
- `setsebool -P httpd_graceful_shutdown 1`
- `setsebool -P httpd_can_network_relay 1`
- `setsebool -P nis_enabled 1`
- `setsebool -P httpd_can_network_connect_db 1`
- `setsebool -P httpd_can_sendmail on`

## Accès au GLPI
Pour acceder au GLPI il faut simple entrer l'adresse ip de votre machine dans un navigateur de recherche.

ensuite nous devons installer les paquets manquants :
![installed-error.png](/images/glpi/installed-error.png)
- `dnf --enablerepo=remi install php-pear-CAS`
- `wget http://rpms.remirepo.net/enterprise/8/remi/x86_64/`
- `dnf install php-intl`
Puis si nécessaire un reboot
- `reboot`
Et voilà plus aucune erreur
![installed-noerror.png](/images/glpi/installed-noerror.png)
une fois cela fait il ne reste plus qu'à ce connecter dans la base de donnée mariadb :
![sql.png](/images/glpi/sql.png)
>Serveur SQL : glpidb
Utilisateur : glpiadmin
mot de passe : myP@ssw0rd

## plus qu'à vous connecter

Et voilà il ne reste plus qu'à vous connecter avec les identifiants suivant :
>utilisateur : glpi
mot de passe : glpi

![end.png](/images/glpi/end.png)

# installation de Fusion Inventory

- [Fusion Inventory *1.1-Recenser et identifier les ressources numériques*](/Realisationformation/GestionPatrimoine/GLPI/FusionInv)
{.links-list}