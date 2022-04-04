---
title: Installation du Wiki.js
description: 
published: 1
date: 2022-04-04T22:06:09.529Z
tags: 1.5 mettre à disposition des utilisateurs un service informatique, déployer un service
editor: markdown
dateCreated: 2022-03-24T14:29:48.115Z
---

# Compétences
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

## Création d'un groupe d'utilisateurs
La 1^ère^ chose est de créé un groupe et un utilisateur pour notre serveur wiki :

`sudo groupadd --system wiki`
> Création du groupe "wiki".
{.is-info}

`sudo useradd -s /sbin/nologin --system -g wiki wiki`
> Création d'un utilisateur "wiki" dans le groupe "wiki".
{.is-info}

## Le repository EPEL (non géré par Red Hat)
Pour installer cette repository on utilise la commande suivant :

`yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm`

## Installation des paquets nécessaires

`yum install -y git vim wget curl unzip socat mariadb-server`
> Installation et confirmation d'installation des paquets :
	- vim
	- wget
	- curl
	- unzip
	- socat
	- mariadb-server
{.is-info}

## Installation de Node.js et Nginx
`curl -sL https://rpm.nodesource.com/setup_12.x | sudo bash -`

`sudo yum install -y nodejs nginx`
> Installation et confirmation d'installation des paquets :
	- Node.js
	- Nginx
{.is-info}

## Démmarer MySQL
`systemctl start mariadb`
> Démmarage du service MariaDB.
{.is-info}

`systemctl enable mariadb`
> Démmarage du service MariaDB à chaque démmarage de la machine grâce au `enable` .
{.is-info}

`mysql_secure_installation`
> Configuration de MariaDB.
{.is-info}

Puis lors de l'installation on confirme l'emssemble des questions et on ajouter un mot de passe root.

![yes_only_mysql.png](/images/install_wikijs/yes_only_mysql.png)

## Connexion à MariaDB
`mysql -u root -p`

![connexion_mariadb.png](/images/install_wikijs/connexion_mariadb.png)

> -u = utilisateur 
-p = connexion avec mot de passe.
{.is-info}

## Configuration de la base de données
`CREATE USER 'wiki'@'localhost' IDENTIFIED BY 'Def@ultP@ssword';`

![create_user.png](/images/install_wikijs/create_user.png)

> Création d'un utilisateur "wiki" sur la machine actuelle(localhost) avec comme mot de pase Def@ultP@ssword .
{.is-info}

`CREATE DATABASE database_name;`

![create_database.png](/images/install_wikijs/create_database.png)

> Création d'une base de données au nom de " database_name ".
{.is-info}

`GRANT ALL PRIVILEGES ON database_name.* TO 'wiki'@'localhost';`

![grant_all_privi.png](/images/install_wikijs/grant_all_privi.png)

> Donne un accès total à la base données "database_name" à l'utilisateur "wiki".
{.is-info}

`FLUSH PRIVILEGES;`

![flush_privi.png](/images/install_wikijs/flush_privi.png)

> La commande `FLUSH PRIVILEGES;` permet d'actualiser les privilèges des bases de données.
{.is-info}

### Pour savoir si la base données et les droits sont actif
#### Savoir les bases de données
On utilise la commande `SHOW DATABASES;` pour voir toutes les bases de données.

![show_databases.png](/images/install_wikijs/show_databases.png)

   
#### Savoir les droits actif

On utilise la commande `SHOW GRANTS FOR 'wiki'@'localhost';` pour connaître les droits de l'utilisateur "wiki"

![show_privi.png](/images/install_wikijs/show_privi.png)

Puis on utilise la commande `exit` pour quité la configuration de MariaDB.

![exit.png](/images/install_wikijs/exit.png)

## Installation de Redis
`sudo yum -y install redis`
> Installation et confirmation d'installation du paquet de Redis.
{.is-info}

`sudo systemctl enable --now redis`
> Activation instantané grâce au `--now` et démmarage automatique du service Redis a chaque démmarage de la machine grâce au `enable` .
{.is-info}

### Vérification de l'état du service Redis
`systemctl status redis`
> Cette commande permet de savoir le status du service de Redis.
{.is-info}

## Récupréation des sources de la solution Wiki.js
`curl -s https://api.github.com/repos/Requarks/wiki/releases/latest | grep browser_download_url | grep -v windows | cut -d '"' -f 4 | wget -qi -`

> cette commande permet d'aller récuperer un fichier sur le site de GitHub.
{.is-info}

## Création d'un répertoire pour Wiki.js et le décompreser dedans
`sudo mkdir /srv/wiki`
> Cette commande permet de créer un fichier dans `/srv/wiki` grâce a la commande `mkdir` .
{.is-info}

`sudo tar zxf wiki-js.tar.gz -C /srv/wiki`
> Cette commande sert a décompreser le fichier `wiki-js.tar.gz` dans le fichier `/srv/wiki` .
{.is-info}

## Se déplacer dans le fichier wiki et faire la copie et la config du fichier config
`cd /srv/wiki`
> la commande `cd` pour ce délplacer dans le fichier `/srv/wiki` .
{.is-info}

`sudo cp config.sample.yml config.yml`
> cette commade permet de copier le fichier `config.sample.yml` et de le renomer en `config.yml` .
{.is-info}

Config du fichier `nano config.yml` .

![fichier_config.png](/images/install_wikijs/fichier_config.png)

## Test du Wiki.js et ajout des ports aux firewall
### Test de lancement du Wiki.js
`sudo node server`
> Lancement du server Wiki.js avec Node.js
{.is-info}

### Ajouter des ports au firewall
`firewall-cmd --add-port=3000/tcp --permanent`
> Cette commande permet d'ajouter tout de suite et de manière permanent le port 3000 en TCP grâce au `--permanent` .
{.is-info}

`firewall-cmd --reload`
> Cette commande permet de redémmarer le firewall de la machine grâce au `--reload`. 
{.is-info}

## Configuration pour que tout ce lance au démmarage
Avant de continuer il faut arret le server node, il suffit bde faire un CTRL+C, puis nous allons le transformer en service.

`nano /etc/systemd/system/wiki.service`
> Cette commande créer un fichier et de le modifier grâce à la commande `nano` dans le systeme de services de la machine.
{.is-info}

> Dans ce fichier wiki.service nous allons écrire :
>
> [Unit]
Description=Wiki.js
After=network.target
>
>[Service]
Type=simple
ExecStart=/usr/bin/node server
Restart=always
User=wiki
Environment=NODE_ENV=production
WorkingDirectory=/srv/wiki
>
>[Install]
WantedBy=multi-user.target

Puis on donne les droits au fichier avec cette commande :

`sudo chown -R wiki:wiki /srv/wiki`

Et on relance :

`sudo systemctl daemon-reload`
> Cette command recharge toute la configuration du gestionnaire systemd.
{.is-info}

`sudo systemctl enable --now wiki.service`
> Activation instantané grâce au `--now` et démmarage automatique du service wiki.service a chaque démmarage de la machine grâce au `enable` . 
{.is-info}

Puis on vérifie si le service est lancer avec la commande suivante :

`systemctl status wiki`

Ensuite nous devons ajouter les entrées pour SeLinux :

`sudo semanage port -a -t http_port_t -p tcp 3000`

`sudo setsebool -P httpd_can_network_connect 1`

# Installation fini
il ne reste plus qu'à vous connecter sur l'adresse IP de la machine suivit du port 3000.
> X.X.X.X:3000
{.is-info}
 
# Ajout d'utilisateurs et de ces droits
- [Ajouter un utilisateur et lui attribuier des droits](/RedHat/Wikijs/droits)
{.links-list}

 
> Documentation faite par Sulyvan Laleu.