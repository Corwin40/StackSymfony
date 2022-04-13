## Déploiement d'un nouveau projet Symfony.

Connectez-vous au terminal du conteneur PHP, à partir de ce point, toutes les commandes se feront depuis le terminal du conteneur en root.  
**Attention** : utilisez le nom du conteneur approprié selon votre projet.

```bash
docker exec -it "nom_conteneur_www" bash
```

Utilisez la commande du _CLI Symfony_ pour créer votre nouveau projet. 
**Attention** : donner un nom différent à votre projet sans les guillements.

```bash
symfony new "nouveau_projet" --full
```

Droit pour l'utilisateur courant :  
Afin de modifier en local votre projet et de permettre à **Apache** d'afficher correctement le développement et/ou le déploiement du projet, il est nécessaire d'adapter les différents droits d'exécution, de lecture des fichiers et dossiers.

```bash
chown -R $USER:www-data /var/www/html/"dossier_de_votre_projet"
chmod -R a-rwx,u+rwX,g+rX /var/www/html/"dossier_de_votre_projet"
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/public
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/var
```
Enfin , on démarre du serveur de développmement Symfony

```
cd new-project
symfony serve -d
```

L'application devrait être accessible à cette adresse : [http://127.0.0.1:8001](http://127.0.0.1:8001)
