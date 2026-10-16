# TP : analyse des accidents de la route avec PySpark

Analyse des accidents de la route en Australie-Méridionale entre 2012 et 2019 avec Apache Spark (PySpark), en utilisant les trois façons de manipuler des données dans Spark : les RDD, les DataFrames et Spark SQL.

On refait l'analyse du notebook *Big data Analysis of Road Crash Data using PySpark* de Rakesh Nain, en corrigeant quelques erreurs (découpage des lignes CSV, index des colonnes, requête sur les conducteurs sans permis).

## Contenu

- `analyse_accidents_spark.ipynb` : chargement des données, requêtes avec les RDD, les DataFrames et Spark SQL, gravité des accidents selon l'alcool et la drogue, comparaison des trois méthodes.

## Données

Les données viennent du Department of Planning, Transport and Infrastructure (DPTI) d'Australie-Méridionale (https://data.sa.gov.au) : un fichier Crash (un accident par ligne) et un fichier Units (un véhicule ou piéton par ligne) par année.

Elles ne sont pas dans le dépôt : le notebook les télécharge depuis le [dépôt GitHub de l'auteur](https://github.com/RakeshNain/Big-data-Analysis-of-Road-Crash-Data-using-PySpark-with-PySpark-Tutorial) dans les dossiers `crash_data/` et `units_data/`.

## Lancer le notebook

Le notebook est prévu pour Linux (Google Colab, ou WSL sous Windows). Il suffit d'exécuter les cellules dans l'ordre : PySpark et Java 17 sont installés automatiquement.
