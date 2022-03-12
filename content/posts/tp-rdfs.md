+++
author = "Emmanuel"
title = "TP RDFs"
date = "2022-03-10T11:00:00-04:00"
description = "Découverte de RDF et de la manipulation de ces fichiers"
weight = 3
seance = 1
+++
Téléchargez (clic droit puis "Enregistrer la cible du lien sous" ou équivalent) le fichier suivant [exercices/CBWC-RDF-S.ttl](/exercices/CBWC-RDF-S.ttl).

Modifier le fichier localement avec un éditeur de texte pour y ajouter les informations du tableau suivant associées à des vins qui sont déjà dans le fichier mais sans autre information.

Il faut aussi indiquer que le `rdf:type` de ces éléments est `cb:Wine`.

| uri   | wc:C00871996       | wc:C00042101   | wc:C00043125             |
| ----- | ------------------ | -------------- | ------------------------ |
| nom   | Château Montguérêt | Riesling Hügel | Domaine de l’Île Margaux |
| prix  | 14.65              | 7.95           | 22.80                    |
| année | 2011               | 2002           | 2004                     |

Comment faudrait-il procéder pour :

1. Lister les vins (noms, prix et année) en ordre croissant d’année.
2. Lister les vins (noms, prix et année) en ordre croissant de prix.
3. Indiquez les types pour les prix (xsd:decimal) et les années (xsd:gYear).
4. Lister les vins (noms, prix et année) en ordre croissant de prix.
5. Lister les vins (noms, prix et année) en ordre croissant de prix en n’affichant pas les indications de type.

Solutions SPARQL http://www.iro.umontreal.ca/~lapalme/ift6281/RDF/ExerciceRDF.pdf
