# TP2 : accidents de la route avec PySpark

**Auteur :** Hugo EXERTIER, cours Big Data 5A (Mohamed Quafafou), rendu du 18/11/2026.

Analyse des accidents de la route en Australie-Méridionale entre 2012 et 2019 avec Apache Spark (PySpark), en utilisant les trois façons de manipuler des données dans Spark : les RDD, les DataFrames et Spark SQL.

On refait l'analyse du notebook *Big data Analysis of Road Crash Data using PySpark* de Rakesh Nain, en corrigeant quelques erreurs (découpage des lignes CSV, index des colonnes, requête sur les conducteurs sans permis).

## Contenu

- `analyse_accidents_spark.ipynb` : chargement des données, requêtes avec les RDD, les DataFrames et Spark SQL, gravité des accidents selon l'alcool et la drogue, comparaison des trois méthodes.

La première cellule du notebook décrit la contribution : le notebook s'exécute-t-il de bout en bout, problèmes trouvés dans le notebook d'origine, modifications apportées. Chaque section est précédée d'une cellule `## [Étape]` (Installation, Data, Prétraitement, Transformation, EDA, Éval, Conclusion).

## Problèmes corrigés dans le notebook d'origine

| Problème | Correction |
|---|---|
| `split(',')` coupe les valeurs entre guillemets (plus de 21 000 lignes d'accident décalées) | module `csv` (RDD), `spark.read.csv` avec `escape` (DataFrames) |
| Index des colonnes décalés de 1 après la jointure de RDD | accès aux colonnes par leur nom |
| La requête « conducteurs sans permis » garde surtout des conducteurs avec permis, et la version DataFrame compte des lignes | filtre sur `Unlicenced` et somme de `Total Cas`, même résultat avec les trois méthodes |
| Colonnes de victimes restées en texte (tri alphabétique) | conversion en entier |
| `groupByKey`, `collect()[0:5]`, UDF Python, code copié 4 fois | `reduceByKey`, `take(5)`, fonctions Spark, une fonction réutilisée |

## Données

Les données viennent du Department of Planning, Transport and Infrastructure (DPTI) d'Australie-Méridionale (https://data.sa.gov.au) : un fichier Crash (un accident par ligne) et un fichier Units (un véhicule ou piéton par ligne) par année.

Elles ne sont pas dans le dépôt : le notebook les télécharge depuis le [dépôt GitHub de l'auteur](https://github.com/RakeshNain/Big-data-Analysis-of-Road-Crash-Data-using-PySpark-with-PySpark-Tutorial) dans les dossiers `crash_data/` et `units_data/`.

## Lancer le notebook

Le notebook est prévu pour Linux (Google Colab, ou WSL sous Windows). Il suffit d'exécuter les cellules dans l'ordre : PySpark et Java 17 sont installés automatiquement.

## Voir aussi

- [TP1](https://github.com/ItaTuTsuki/TP1) : comptage de mots (Python, pseudo-MapReduce, Hadoop, PySpark).
- [TP3_ID06](https://github.com/ItaTuTsuki/TP3_ID06) : deux cas personnels, small data et big data.
