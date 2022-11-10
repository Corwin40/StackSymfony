## Déploiement d'un projet Symfony existant depuis votre dépot Git.

### Se connecter au conteneurs www

Pour communiquer en SSH depuis votre IDE :
```bash
docker exec -it votre_projet bash
```

##### Clonage depuis votre dépot git
Pour cette étape, recupérer le lien de clonage de votre projet depuis le dépot Github
```bash
git clone https://github.com/"votre_login_git"/"votreprojet".git
```

Pour assurer votre développement futur depuis un IDE, il vous faut créer un compte _user_ dans votre conteneur. Ce dernier sera identique à votre session Linux et nous lui donnerons les droits d'accès dans ce conteneur.

```bash
adduser username
chown username:username -R .
```

Droit pour l'utilisateur courant :
Afin de modifier en local votre projet et de permettre à Apache d'afficher correctement le développement et/ou le déploiement du projet, il est nécessaire d'adapter les différents droits d'exécution, de lecture des fichiers et dossiers.

```bash
chown -R $USER:www-data /var/www/html/"dossier_de_votre_projet"
chmod -R a-rwx,u+rwX,g+rX /var/www/html/"dossier_de_votre_projet"
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/public
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/var
```

##### Connexion de l'application à la basse de données.  

Pour POSTGRES
```yaml
DATABASE_URL="postgresql://symfony:ChangeMe@db/app?serverVersion=13&charset=utf8"
```
MYSQL / MARIADDB
