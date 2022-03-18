##### Déploiement d'un projet Symfony existant depuis votre dépot Git.

##### Clonage depuis votre dépot git
Pour cette étape, recupérer le lien de clonage de votre projet depuis le dépot Github
```bash
git clone https://github.com/"votre_login_git"/"votreprojet".git
```

Pour assurer votre développement futur depuis un IDE, il vous faut créer un compte _user_ dans votre conteneur. Ce dernier sera identique à votre session Linux et et nous lui donnerons les droits d'accès dans ce conteneur.

```bash
adduser username
chown username:username -R .
```

Droit pour l'utilisateur courant : afin de modifier en local votre projet et de permettrre à apache d'azfficher correctement le développement/le déploiement du projet, il est nécessaire d'adapter les différent droits d'exécution, lecture des ficheires et dossiers.

```bash
chown -R $USER:www-data /var/www/html/"dossier_de_votre_projet"
chmod -R a-rwx,u+rwX,g+rX /var/www/html/"dossier_de_votre_projet"
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/public
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/var
```

##### Connexion de l'application à la basse de données.  

POSTGRES
```yaml
DATABASE_URL="postgresql://symfony:ChangeMe@database:5432/app?serverVersion=13&charset=utf8"
```
MYSQL / MARIADDB
