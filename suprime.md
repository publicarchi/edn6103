## .red[SKOS] Simple Knowledge Organisation System

http://www.w3.org/2004/02/skos/

- SKOS (W3C) 1ère version en 2003
- extensibilité
- modèle de graphe (application de RDF)
- fournit des propriétés pour le mapping sémantique entre plusieurs vocabulaires contrôlés

famille de langage formels conçus pour la représentation des thesauri, des taxonomies ou tout autre type de vocabulaire contrôlé

- faciliter la publication et la connexion entre des vocabulaires contrôlés pour le web sémantique
- fournit seulement la structure

???

But de SKOS de pouvoir récupérer des données produites dans différents contextes, et de les unifier pour pouvoir les réemployer dans le contexte du web sémantique.

Le langage respecte de formalisme des ontologies avec choses développées dans d’autres contextes.

Il s’agit d’un standard de W3C.

On y trouve :

- des concepts identifiés par des URI
- des étiquettes avec des chaînes dans plusieurs langues
- des relations informelles entre les concepts
- ...

Cela s’exprime sous forme de triplets. Il existe donc une notation Turtle ou RDF.

On va ainsi faire des liens entre différentes ressources. Simplement, un certain nombre de propriétés et de termes auront ici un sens particulier et permettront d’unifier des ressources hétéroclites.

Plusieurs espaces de noms sont utilisés, celui spécifique de SKOS, mais également rdf, rdfs, etc.

Plutôt que de parler de classe, on parle ici de concepts. Ce qu’on appelle un concept est ce qu’on appelle une classe ailleurs, mais le terme est plus général. Il peut s’agir d’unité de sens, de choses, etc. qui existent indépendamment de leur étiquette.

On peut ensuite associer à un concept, une manière d’y référer dans différentes langues naturelles.

skos:prefLabel un seul

skos:altLabel synonyme ou abréviation

skos:hiddenLabel pour la machine seulement.

Pas quelque chose qui va permettre de faire des preuves mais plutôt quelque chose pour fédérer des ressources. C’est la raison pour laquelle beaucoup de soin a été mis sur les différentes manières de de désigner un même concept.

### Relation

#### Liens hiérarchiques

skos:broader

- du particulier au général
- de la partie vers le tout

Exemple des mammifères en relation avec un autre concept plus général. Pourrait dire que ceci est une sous-classe de cela, mais ici ne parle pas de sous-classe car pas les mêmes contraintes. On sait tout de même que certains concepts sont plus précis que d’autres.

skos:narrower

#### Liens associatifs

Il existe aussi des liens associatifs. Mais les liens seront relativement flou.

skos:related

#### Documentation

De nombreux éléments définis par SKOS concernent la documentation.

skos:scopeNote

skos:definition

skos:example

skos:historyNote

------

## Thesaurus

> « vocabulaire contrôlé et structuré dans lequel les concepts sont représentés par des termes, et organisés de manière à rendre explicite les relations entre les concepts les termes préférentiels sont accompagnés de synonymes ou quasi-synonymes »
>
> norme ISO 25964

- on distingue les thésaurus des autres types de vocabulaires contrôlés
- une norme adaptée aux évolutions des systèmes d’information
- une norme en phase avec le web sémantique et ses standards

???

### Vocabulaires contrôlés

lexique, ensemble fermé de termes de description (motset expression) soigneusement choisis pour un domaine accompagnés de leurs définitions précises

utilisés pour étiqueter des documents de manière à ce qu'ils soient plus facilement repérables lors d'une recherche

Résoudre des problèmes : 

- d'homographie  | de polysémie | de synonymie
- réduire l'ambiguïté inhérente au langage naturel
- différents noms peuvent être attribués à un même concept

### Thesaurus

norme ISO 25964

- partie 1 : thésaurus pour la recherche documentaire (2011)
- partie 2 : interopérabilité avec des vocabulaires (2013)

souvent utilisés pour les documents techniques ou dans des domaines spécialisés (vocabulaires métiers)

> « vocabulaire contrôlé et structuré dans lequel les concepts sont représentés par des termes, et organisés de manière à rendre explicite les relations entre les concepts les termes préférentiels sont accompagnés de synonymes ou quasi-synonymes »
>
> norme ISO 25964

- on distingue les thésaurus des autres types de vocabulaires contrôlés
- une norme adaptée aux évolutions des systèmes d’information
- une norme en phase avec le web sémantique et ses standards

------

## Exemples

### Autorités

- Répertoire de Vedettes Matières (RVM)

  https://rvmweb.bibl.ulaval.ca

- IdRef, Référentiel des autorités Sudoc

  http://www.abes.fr/IdRef/IdRef-Referentiel-d-autorites

  http://www.idref.fr/

### Thesaurus

- Icon Class (iconographic description)

  http://www.iconclass.org/

- Getty Arts and Architecture thesaurus (AAT)

  http://www.getty.edu/research/conducting_research/voca-bularies/aat/

- Getty Union List of Artist (ULAN)

  http://www.getty.edu/research/conducting_research/voca-bularies/ulan/

- Getty Thesaurus of Geographical Names (TGN)

  http://www.getty.edu/research/conducting_research/voca-bularies/tgn/

------

## Les ontologies

une description formelle explicite des concepts partagés dans un domaine donné et des relations entre ces concepts

- contient des définitions lisibles en machine des concepts (classes) et de leurs relations
- caractéristiques et attributs du concepts (rôles ou propriétés)
- restrictions sur les attributs (facettes ou restrictions de rôles)
- permet de formuler des raisonnements

une ontologie définit **une conceptualisation commune** pour une communauté qui a besoin de partager l’information dans un certain domaine

???

en sciences de l’informatique, une ontologie est unespécification formelle d'un modèle conceptuel lisiblepar la machine dans laquelle les concepts, propriétés,relations, fonctions, contraintes et axiomes sontexplicitement définis

- pas un vocabulaire contrôlé proprement dit
- mais peut en employer un ou plusieurs

une description formelle explicite des concepts partagés dans un domaine donné et des relations entre ces concepts

- contient des définitions lisibles en machine des concepts (classes) et de leurs relations
- caractéristiques et attributs du concepts (rôles ou propriétés)
- restrictions sur les attributs (facettes ou restrictions de rôles)
- permet de formuler des raisonnements

une ontologie définit une conceptualisation communepour une communauté qui a besoin de partager l’information dans un certain domaine

------

## Exemple de .red[CIDOC-CRM]

http://www.cidoc-crm.org

- **Exprime la sémantique sous-jascente des structures de la documentation sur le patrimoine muséographique**
- une formalisation des connaissances = concepts et relations portant sur les états de choses possibles dans un domaine
- une explication partagée plutôt qu’une structure commune de données (non prescriptif : ne dit pas ce qu’il faut décrireni comment, mais permet d’interpréter les descriptions effectivement produites par les musées)
- accessible aux humains (documentation textuelle) et auxmachines (OWL, etc.) pour permettre l’échange et l’intégrationde données, la recherche fédérée, etc.

------

## .red[OWL] Web Ontology Language

https://www.w3.org/standards/techs/owl#w3c_all

- un langage déclaratif pour exprimer des ontologies.
- plus riche que RDFs

Modélisation de base : 

- classes et instances
- hiérarchies de classes
- propriétés d’objects
- hiérarchies de propriétés
- Restrictions sur les propriétés
- égalité des individus
- types des valeurs de propriétés

???

Principe, un langage déclaratif pour exprimer des ontologies. Il ne s’agit pas d’un langage de schéma, et c’est un monde ouvert, ce qui change la façon de faire des preuves.

En OWL on se retrouve avec des axiomes, cad un ensemble d’énoncés de base supposés vrais. On a également des entités qui font référence à… Puis des expressions. L’ensemble formant une ontologique.

On y trouvera des énoncés de base et on parlera de conséquences des énoncés. On exprime des relations entre des énoncés, ensuite pourra voir si un énoncé a est vrai si d’autres A le sont. A entraîne (entails) a. Alors on dira que A est consistant si une situation où tous ses énoncés sont vrais.

Modélisation de base : être capable de définir des classes, des sous-classes, des propriétés et des sous-propriétés, des restrictions sur des propriétés, etc. Série d’éléments qui correspondent un peu à ce que peut faire avec RDFs mais plus riche

- classes et instances
- hiérarchies de classes
- propriétés d’objects
- hiérarchies de propriétés
- Restrictions sur les propriétés
- égalité des individus
- types des valeurs de propriétés

Ensuite relations avancées de classes : définition de classes complexes, restrictions de propriétés (ex famille nombreuse, plus de x individus enfants), mais aussi de cardinalice, énumérations d’individus. Choses qui s’expriment aussi en logique de premier ordre.

- classes complexes
- restrictions de propriétés
- restrictions de cardinalité
- énumérations d’individus

Utilisation avancée des propriétés

- caractéristiques des propriétés
- chaînes de propriétés
- clés

------

## Europeana Data Model

https://pro.europeana.eu/resources/standardization-tools/edm-documentation

???

### Le modèle initial Europeana Semantic Element

Passage de Europeana Semantic Elements Documentation à Europeana Data Model.

Modèle initial ESE fondé sur le plus petit dénominateur commun. Forçait l’interopérabilité et obligeait à convertir les ensemble des données vers une représentation plate, occasionnant une perte de la richesse des données originales.

### Passage au modèle EDM

Programme Européen eContentPlus

Effort collaboratif, développé collaborativement avec l’ensemble des acteurs.

Les besoins

- accommoder différents modèles de données
- accommoder des besoins de domaines spécifiques
- éviter les pertes de données et conserver la meilleure granulairté
- co-exister avec les données originales

Distinguer les objets de leur représentation, permettre plusieurs description d’un même objet, y compris contradictoires. Prendre en charge la composition, support de données contextuelles et de vocabulaires contrôlés.

Promouvoir la réutilisation de ressources externes (LOD)

Propriétés et classes dans l’espace de nom edm (edm:hasView, etc.). Réutilisation des éléments d’autres ontologies ore, skos, etc.

https://pro.europeana.eu/resources/standardization-tools/edm-documentation

> A vast number of Europe's cultural heritage objects are digitised by a wide range of data providers from the library, museum, archive and audio-visual sectors, and they all use different metadata standards. This data needs to appear in a meaningful way in a cross- cultural, multilingual context such as Europeana. Numerous cultural heritage resources such as thesauri exist worldwide and have the potential to add valuable content at low cost when re-used. Duplication of effort, however, needs to be avoided. The Linked Open Data environment lacks authoritative data from the cultural heritage community to contribute to the development of new knowledge.
>
> The Europeana Data Model (EDM) aims to bridge these gaps in the Europeana context.EDM is a major improvement on ESE, Europeana’s first data model.
>
> - EDM transcends domain-specific metadata standards, yet accommodates the rangeand richness of community standards such as LIDO for museums, EAD for archivesor METS for digital libraries.
> - It facilitates Europeana’s participation in the Semantic Web, basing itself on an open,cross-domain, semantic web-based framework.
> - EDM is a more developed data model that brings more meaningful links to Europe’scultural heritage data. Data from partners or external information resources withreferences to persons, places, subjects, etc., will connect to other initiatives andinstitutions. This will result in sharing enriched content, adding to it and therebygenerating more content in ways that no single provider could achieve alone.
> - The EDM semantic approach will translate into the richer resource discovery andimproved display of more complex data.

EDM développé avec des experts technologiques issus de collections audiovisuelles et patrimoniales en tenant compte des standards existants comme DC, EAD, LIDO.

Améliorer les réponses aux utilisateurs et augmenter et faciliter la découverte de ressource afin d’augmenter le traffic sur les fournisseurs de données.

Meilleure représentation des objets, et faciliter de visualisation des contenus.

Enrichissement des contenus, multilinguisme.

Contribution au web de données.