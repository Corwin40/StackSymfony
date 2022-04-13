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

Droit pour l'utilisateur courant : afin de modifier en local votre projet et de permettrre à apache d'azfficher correctement le développement/le déploiement du projet, il est nécessaire d'adapter les différent droits d'exécution, lecture des ficheires et dossiers.

```bash
chown -R $USER:www-data /var/www/html/"dossier_de_votre_projet"
chmod -R a-rwx,u+rwX,g+rX /var/www/html/"dossier_de_votre_projet"
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/public
chmod -R g+w /var/www/html/"dossier_de_votre_projet"/var
```
Démarrage du serveur de développmement Symfony

```
cd new-project
symfony serve -d
```

L'application devrait être accessible à cette adresse : [http://127.0.0.1:8001](http://127.0.0.1:8001)
