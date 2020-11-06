# MongoDB - Practices - CRUD

**Version**: 1
**Date** : 06/11/2020
**Auteur** : Arnaud de Mouhy arnaud@admds.net

## Recherches préalables

- Qu'est-ce que veut dire "CRUD" ?

## Lecture de documents

Dans la base de donnée `sample`, combien de documents dans la collection `grades` ont un `student_id` inférieur à 65 ?

Dans la base de donnée `city`, combien de documents dans la collection `inspections` ont un `result` "Pass" ou "Fail" ?

Dans la collection `stories` de la base de donnée `digg`, écrire une requête pour trouver toutes les stories où le nombre de vues est supérieur à 1000.

Trouver les articles d'actualité qui ont le plus de commentaires dans la collection `stories`.

Trouver toutes les stories digg où le nom du topic est "Television" ou que le type de media est "videos". Sautez les 5 premiers résultats et limiter l'ensemble de résultat à 10.

Requêtez pour toutes les stories digg où le type de média est soit "news", soit "images" et que le nom du topic est "Comedy". (Pour aller plus loin, vous pouvez utiliser 2 requêtes en utilisant différents ensembles d'opérateurs pour arriver à vos fins).

## Mie à jour de documents

Imaginons que l'on veut faire un peu de ménage dans la collection `city.inspections`.
Nous avons décidé d'enlever tous les résultats d'inspection le terme "Completed" et n'utiliser seulement que le terme "No Violation Issued".
Mettre à jour toutes les inspections en conséquence.

Pour toutes les inspections qui sont "Fail", définir une propriété "fine" à 100.

Augmenter la propriété "fine" de 150 pour toutes les inspections "Fail" dans la ville de "ROSEDALE"


