# OpenPixl - Stack Docker
<small>Prete pour la production de site Symfony 5 et 6</small>

**Pour du DEV ou du PROD**

Construit à partir de l'image php8:apache et largement inspiré du dépot de [@yoanbernabeu](https://github.com/yoanbernabeu).  
Merci à lui pour son travail.
La stack se compose de :
- [x] image PHP-8.0.13-cli (Debian) et les extensions php
- [x] composer, sympfony, nodeJS et Yarn
- [x] Mariadb dans sa dernière version
- [x] correction de gd pour php8 (manipulation d'image avec le bundle LiipImagine
- [x] Ajout de la bibliothèque "WKHTMLTOPDF" (génération pdf depuis vos projet)

A corriger prochainemement :
- [ ] Ajout du port https,


### AVANT LA PROCEDURE DE DEPLOIEMENT
#### 1. Cloner le projet dans votre dossier de dev ou de prod

Code :
```bash
https://github.com/Corwin40/StackSymfony.git
```
#### 2. Ajourt du fichier .env
Le fichier _"docker-compose.yaml"_ s'appuie sur un fichier _".env"_ contenant les variables nécessaire au déploiement de la stack et de votyre serveur: la base de donnée, les  differents ports attribués à vos conteneurs, ...

Créez ce fichier avec les commandes suivantes :

```
  cd StackSymfony
  nano .env
```
Puis copier/coller le contenu suivant.

```
# Variable Project
PROJECT=sf5
PROJECT_IP=21
RESTART=no

# Variables Mariadb
PMA_HOST=db
MARIA_ROOT_PASSWORD="mot_de_passe_principale"
MARIADB_USER="utilisateur"
MARIADB_PASSWORD="mot_de_passe_utilisateur"
MARIADB_DBNAME="Nom_de_votre_ bdd"

# Variables Serveur apache php
HTTP_HOST_PORT=80
HTTP_HOST_PORTDEV=8001
HTTPS_HOST_PORT=443
MARIA_HOST_PORT=3307

```
#### 3. Personnalisation du fichier _vhost.conf_
Pour finaliser la configuration de la stack, pensez à adapter le fichier _"vhosts.cnf"_ situé dans le dossier "php". Vous devez modifier les lignes suivantes par votre nom de projet.

Ligne 4
```bash
DocumentRoot /var/www/html/"nom_du_projet"/public
```
Ligne 7
```bash
<Directory /var/www/html/"nom_du_projet"/public>
```
Ligne24
```bash
<Directory /var/www/html/"nom_du_projet"/public/bundles>
```

### PROCEDURE DE DEPLOIEMENT

#### I. Docker-compose
Lancer docker-compose avec la commande suivante.  
La commande _build_ va construire l'image de votre serveur www contenant apache, php8, composer, symfony et yarn. Ainsi que l'ensemble des extensions nécessaire à _PHP_ et les _frameworks_ actuels. 

```bash
docker-compose build
docker-compose up -d
```
#### II. déploiement du projet

##### [II. A déploiement d'un nouveau projet Symfony pour développement.](https://github.com/Corwin40/StackSymfony/blob/master/documentation/newSymfony.md)


##### [II. B déploiement d'un projet Symfony existant depuis votre dépot Git.](https://github.com/Corwin40/StackSymfony/blob/master/documentation/existSymfony.md)

## Author
- xavier Burke - OpenPixl.fr    |     [Email](xavier.burke@openpixl.fr)  /  [Web](ww.openpixl.fr)
