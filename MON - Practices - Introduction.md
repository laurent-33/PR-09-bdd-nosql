# MongoDB - Practices - Introduction

**Version**: 1
**Date** : 06/11/2020
**Auteur** : Arnaud de Mouhy arnaud@admds.net

## Recherches préalables

- Quelle est l'adresse du site contenant la documentation mongo ?
    * docs.mongodb.com
- Quelles sont les 3 variantes serveur fournies par mongo ?
    * community
    * entreprise (payant)
    * cloud (mongo atlas en ligne)
- Quel est le port par défaut sur lequel écoute MongoDB Server ?
    * 27017
- Quelle est le nom de la commande CLI permettant de se connecter à un serveur MongoDB
    * mongo
- Quelle est la syntaxe permettant de spécifier l'hôte sur lequel le client va se connecter ?
    * --host
    * avec une URI : mongodb://<host>(:<port>)(/<database_name>)

## Installation de MongoDB

### Installation

2 méthodes :
- Installer MongoDB Community Server depuis le site officiel (https://docs.mongodb.com/manual/administration/install-community/)
- Lancer le serveur depuis un container Docker "mongo" (https://hub.docker.com/_/mongo)

### Lancer un shell mongo

Se connecter à votre instance MongoDB à l'aide de l'outil CLI. 

#### Avec Docker

Si vous l'utilisez avec Docker, lancez un container avec le serveur puis lancer un autre container mongo avec la commande cli comme argument. Attention à bien mettre les 2 containers dans le même réseau. Bien spéficier explicitement le nom du serveur (`mongo-server`) sur lequel se connecter avec l'argument `<host-uri>` car par défaut il essaye de se connecter au serveur en local.

```
docker network create mongo-net
docker run --name mongo-server --network mongo-net mongo:4.4
docker run --rm -it --network mongo-net mongo:4.4 <commande> <host-uri>
```

### Importation des données du lab

#### Note pour docker
Pour les commandes suivantes d'importation ou de restoration, exécuter le container comme suit: `docker run --rm -i --network mongo-net -v "/<path/to/host/folder>:/<container-folder>" mongo:4.4 <commande>` où :
- pour les importations, `</path/to/host/folder>` pointe vers le dossier `usb_drive`, et `<container-folder>` pointe vers `/import`.
- pour la restoration, `</path/to/host/folder>` pointer vers le dossier `usb_drive/dump4.4` et `<container-folder>` pointe vers `/dump`.

#### Instructions
- Récupérer le fichier `usb_drive.zip`
- Pour chaque fichier `.json` dans cette archive, exécuter les commandes suivantes: `mongoimport -d sample -c <collection> --drop /import/<fichier>.json` avec fichier `twitter.json` => collection `tweets`, `zips.json` => `zips`, `grades.json` => `grades`. Expliquer la commande.  

\# mongoimport -d sample -c tweets --drop import/twitter.json --host mongo-server

- Restorer le dump avec la commande suivante: `mongorestore --drop "mongodb://mongo-server" /path/to/dump4.4`. Expliquer la commande.

\# mongorestore --drop --host mongo-server import/dump-4.4

(pour restaurer la sauvegarde voulue, ici dossier 'dump-4.4')

### Explorer les bases de données
- Trouver et exécuter dans le shell mongo la commande permettant de lister les bases de données disponibles. Astuce, la commande `help` vous permet de lister les commandes disponibles.
- Trouver et exécuter la commande permettant de changer de base de donnée active. Une fois ceci fait, la base de donnée active est associée à la commande `db`.

### Explorer les collections
- Trouver et exécuter la commande permettant de lister les collections disponibles dans la base de donnée active.
- Exécuter les commandes suivantes et indiquer ce qu'elles font
```
db.<COLLECTION>.help()
db.<COLLECTION>.find()
```