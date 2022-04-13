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

> Cette partie n'a pas encore été testée concernant le serveur interne à symfony.  

```
cd new-project
symfony serve -d
```

*L'application devrait être accessible à cette adresse : [http://127.0.0.1](http://127.0.0.1)*
