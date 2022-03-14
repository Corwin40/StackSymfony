##### Déploiement d'un projet Symfony existant depuis votre dépot Git.

##### Clonage depuis votre dépot git
Pour cette étape, recupérer votre lien de clone depuis votre dépot Github
```bash
git clone https://github.com/"votre_login_git"/"votreprojet".git
```
Dorit pour l'utilisateur courant
```bash
chown -R $USER:www-data /var/www/html/"dossier_de_votre_projet"
chmod -R a-rwx,u+rwX,g+rX /var/www/html/"dossier_de_votre_projet"
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/public
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/var
```

Pour assurer votre développement futur depuis un IDE, il vous faut créer un compte _user_ dans votre conteneur. Ce dernier sera identique à votre session Linux et et nous lui donnerons les droits d'accès dans ce conteneur.

```bash
adduser username
chown username:username -R .
```
##### Connexion de l'application à la basse de données.  
POSTGRES
```yaml
DATABASE_URL="postgresql://symfony:ChangeMe@database:5432/app?serverVersion=13&charset=utf8"
```
