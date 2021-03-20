## Retour sur l’exercice

???

La plateforme d’édition scientifique Persée offre depuis 2017 un accès à ses données sous forme de données liées. Cet entrepôt de données présente l’avantage de proposer une interface (Sparklis) qui ne demande aucune connaissance informatique particulière pour formuler des requêtes et obtenir des listes de résultats.

L’objectif de cet exercice est de construire une requête avec ce service afin de télécharger un jeu de données pour vous familiariser avec l’utilisation des jeux de données liées.

1. Prendre connaissance de la [documentation](http://data.persee.fr/ressources/le-triplestore-de-persee/) et du [schéma de données](http://data.persee.fr/explorer/schemas-de-donnees/)
2. Au besoin, et au fur et à mesure de votre travail, vous pourrez avoir recours aux tutoriaux vidéos http://data.persee.fr/ressources/tutoriels/ ou à leur version textuelle http://data.persee.fr/ressources/tutoriels-texte/
3. Construire les requêtes suivantes et observez les résultats
   - Tous les documents qui ont pour auteur "Lepetit", listés par date d’édition décroissante
   - Chercher ses co-auteurs
   - Faite une liste des auteurs par document
   - Ordonner cette liste de documents par date de publication croissante
   - Lister les auteurs qui ont le plus de co-auteurs
   - Inventer une requête de votre choix
4. Pour chacune des requêtes, visualisez à chaque fois sa version SPARQL (cliquez sur "YASGUI view" en haut de la fenêtre) et essayer de comprendre à quoi celle-ci correspond
5. **Question bonus :** Essayer de modifier la dernière requête en SPARQL pour afficher les titres d’articles.

---

## La plate forme Persée

- http://www.persee.fr
- http://www.persee.fr/entrepot-oai
- http://data.persee.fr

### Autre exemple

- https://co-shs.ca

???

Persée est un programme national de numérisation et de diffusion de collections de documents scientifiques. Par l’intermédiaire de sa plateforme en ligne persée.fr, le site diffuse le texte et les métadonnées de plus de 600 000 documents scientifiques principalement issus de numérisation rétrospectives.

Les interfaces de recherche du service web permet d’explorer plusieurs index et sont munies de fonctionnalités de tri et de facettes qui permettent aux utilisateurs de faire des requêtes avancées dans la base de données. Néanmoins, celles-ci n’offrent que des possibilités de requêtes complexes et ne permettent pas les recherches croisées.

- entrepôt OAI-PMH
- mais phénomène de silos cf. ce qui a été évoqué la dernière fois

Or, l’équipe de Persée explique qu’elle recevait un nombre grandissant de demandes de chercheurs qui considérait le fond non plus comme une bibliothèque de documents mais comme un corpus de recherche à part entière.

- Manière d’envisager le corpus qui supposait donc d’ajouter au corpus des outils de parcours et de requête plus élaborés que ceux disponibles sur le portail
- Diversité de la documentation présente sur le site pour laquelle les technologies du web sémantiques apportait une réponse appropriée

Contexte par rapport à [OpenEdition](https://www.openedition.org) et le consortium [Érudit](https://www.erudit.org/en/). 

Démarche comparable avec la cyberinfrastructure en sciences humaines et sociales [CO-SHS](https://co-shs.ca)

---

## Schéma de données de data.persee.fr

http://data.persee.fr/explorer/schemas-de-donnees/

---

## Alignements de data.persee.fr

http://info.persee.fr/lalignement-des-autorites-persee-au-referentiel-idref/

---

## Questions

Construire les requêtes suivantes et observez les résultats

- Tous les documents qui ont pour auteur "Lepetit", listés par date d’édition décroissante
- Chercher ses co-auteurs
- Faite une liste des auteurs par document
- Ordonner cette liste de documents par date de publication croissante
- Lister les auteurs qui ont le plus de co-auteurs
- Inventer une requête de votre choix

---

background-image: url(images/perseeHackathon2018.jpg)

???

Hackathon de Persée en 2018. Trois défis identifiés pour lesquels les données liées paraissent offrir des opportunités

Expériences de navigation

- Sortir des logiques classiques de navigation par feuilletage et de consultation par liste des résultats de recherche
- Exploiter la richesse de la typologie documentaire des corpus diffusés
- Exploiter la totalité des alignements avec les référentiels extérieurs sélectionnés

Géo-visualisation

- Exploiter graphiquement les informations géographiques présentes dans les données Persée
- Enrichir les contenus de Persée avec des informations géographiques extérieures (GeoNames, ...)

Recherche d’images

- Proposer un dispositif spécifique pour rechercher les illustrations présentes dans les documents mis en ligne sur Persée
- Inventer une nouvelle manière de visualiser et de contextualiser ces illustrations en les couplant avec des ressources extérieures