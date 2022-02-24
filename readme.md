# OpenPixl
## Stack DOCKER pour pour la production de site Symfony5 et Symfony6

**Pour du DEV ou du PROD**

Construit à partir de l'image php8:apache et largement inspiré du dépot de [@yoanbernabeu](https://github.com/yoanbernabeu).  
Merci à lui pour son travail.

A venir prochainemement :
- [ ] Ajout du port https,

### AVANT LA PROCEDURE
Cloner le projet dans votre dossier de dev ou de prod
```bash
  git@github.com:yoanbernabeu/symfony6-php8-in-docker-compose.git
```
Le fichier _docker-compose.yaml_ s'appuie sur un fichier _.env_ contenant vos futures variables nécessaire : à la base de donnée, aux differents ports attribués à vos conteneurs, ...
Créez ce fichier avec les commandes suivantes :

```
    cd StackSymfony
    nano .env
```
Puis copier/coller le contenu suivant.

```
# Variable Project
PROJECT="nom_project"

# Variables Mariadb
PMA_HOST=db
MARIA_ROOT_PASSWORD="votre_mot_de_passe"
MARIADB_USER="votre_nom_user"
MARIADB_PASSWORD="votre_password_user"
MARIADB_DBNAME="votre_nom_db"

# Variables Serveur apache php
HTTP_HOST_PORT=80
```

### PROCEDURE DE DEPLOIEMENT

#### I. Docker-compose
Lancer docker-compose avec la commande suivante.  
La commande _build_ va construire l'image de votre serveur www contenant apache, php8, composer, symfony et yarn. Ainsi que l'ensemble des extensions nécessaire à _PHP_ et les _frameworks_ actuels. 

```bash
  docker-compose build
  docker-compose up -d
```
#### II.A dépoiement d'un nouveau projet Symfony
Connectez-vous au terminal du conteneur PHP

```bash
  docker exec -it "nom_conteneur_www" bash
```

Utilisez la commande symfony pour crer votre nouveau projet symfony. **Attention** : donner un nom différent à votre projet sans les guillements.

```bash
  symfony new "nouveau_projet" --full
  cd new-project
  symfony serve -d
```

Create an account (identical to your local session)

```bash
  adduser username
  chown username:username -R .
```

*Your application is available at http://127.0.0.1:9000*

If you need a database, modify the .env file like this example:

```yaml
  DATABASE_URL="postgresql://symfony:ChangeMe@database:5432/app?serverVersion=13&charset=utf8"
```

## Ready to use with

This docker-compose provides you :

- PHP-8.0.13-cli (Debian)
    - Composer
    - Symfony CLI
    - and some other php extentions
    - nodejs, npm, yarn
- postgres:13-alpine
- mailcatcher


## Requirements

Out of the box, this docker-compose is designed for a Linux operating system, provide adaptations for a Mac or Windows environment.

- Linux (Ubuntu 20.04 or other)
- Docker
- Docker-compose
## Author

- 