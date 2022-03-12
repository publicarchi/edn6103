+++
author = "Emmanuel"
title = "Ontologies et RDF"
date = "2022-03-10"
description = "Ontologies et RDF"
seance = 1
layout = "diapo"
diapo = "seance-02.html"
toc = "oui"
sommaire = "oui"
impression = "oui"
+++
### Notion de schéma, d’ontologie et de vocabulaires

Plusieurs standards définis par le W3C sont destinés à déclarer des classes, des propriétés.

### Comment ne pas être ambigu dans la description ?

- en utilisant un langage commun d’interprétation de cette description ;
- en employant des vocabulaires partagés ;
- et des ontologies qui donnent une signification non-équivoque aux verbes, catégories de sujets et compléments.

Chaque ontologie peut être envisagée comme une manière particulière d’envisager un domaine. Un point de vue sur un domaine. Voir Gruber.

Les ontologies peuvent être alignées, partagées et connectées pour produire ces points de vue (interopérabilité).


## 1. SKOS et les vocabulaires structurés


### Sur les vocabulaires
Plusieurs ressources :

- http://www.slideshare.net/valexiev1/gvp-lodcidocshort
- http://www.slideshare.net/mzeng/aat-microthesauri

### Outils

[Skos play](http://labs.sparna.fr/skos-play/)

[Ginko](http://www.culturecommunication.gouv.fr/Divers/Harmonisation-des-donnees-culturelles/Referentiels/Les-vocabulaires-scientifiques-et-techniques/L-application-GINCO)

[OpenTheso](https://github.com/miledrousset/opentheso)


### La pile des technologies du web sémantique

![](/presentations/images/sw_layercake.png)


### Simple Knowledge Organization System SKOS

**Famille de langage formels conçus pour la représentation des thesauri, des taxonomies, ou tout autre type de vocabulaire contrôlé, destinée faciliter la publication et la connexion entre des vocabulaires contrôlés pour le web sémantique** 

- extensibilité 
- modèle de graphe (application de RDF) 
- fournit des propriétés pour le mapping sémantique entre plusieurs vocabulaires contrôlés 
- offre seulement la structure

http://www.w3.org/2004/02/skos/ (2009)

[SKOS](http://www.w3.org/2004/02/skos/ (2009)) est publié par le W3C en août 2009 et la norme ISO 25964 « Thésaurus pour la recherche d’information et interopérabilité avec d’autres vocabulaires » définit des liens avec SKOS (2011 à 2013)

cf. "Évolution des outils d’indexation documentaire des années 1980 aux années 2010." <https://www.reseau-canope.fr/savoirscdi/centre-de-ressources/fonds-documentaire-acquisition-traitement/le-traitement-documentaire/evolution-des-outils-dindexation-documentaire-des-annees-1980-aux-annees-2010.html>


**SKOS est un langage destiné à faciliter la publication, l’échange et l’interconnexion de ces vocabulaires dans le contexte du web sémantique.**

SKOS est un standard publié par le W3C en août 2009 et norme ISO 25964 « Thésaurus pour la recherche d’information et interopérabilité avec d’autres vocabulaires » (2011 à 2013).

Sa conception est inspirée par des formats ou des guides comme la norme ISO 2788:1986 pour les thésaurus mais n’a pas vocation à les remplacer. 

Le but de SKOS est de pouvoir récupérer des données produites dans différents contextes, et de les unifier pour pouvoir les réemployer dans le contexte du web sémantique.

cf. "Évolution des outils d’indexation documentaire des années 1980 aux années 2010." <https://www.reseau-canope.fr/savoirscdi/centre-de-ressources/fonds-documentaire-acquisition-traitement/le-traitement-documentaire/evolution-des-outils-dindexation-documentaire-des-annees-1980-aux-annees-2010.html>


### Simple Knowledge Organization System SKOS

[SKOS](http://www.w3.org/2004/02/skos/) est un vocabulaire RDF permettant de décrire des référentiels de type **thésaurus**.

- **décrire des concepts** (en utilisant la classe principale, `skos:Concept`) 
- **exprimer les relations entre ces concepts** (relations hiérarchiques – termes plus spécifiques ou génériques – ou autres – termes en relation).
- des **propriétés pour décrire des résultats d’alignements** automatiques ou manuels entre des concepts issus de thésaurus distincts (`skos:closeMatch`, `skos:exactMatch`).

#### Ressources

- Miles, Alistair, et Dan Brickley. 2005. « SKOS Core Guide ». Working Draft. W3C. <https://www.w3.org/TR/swbp-skos-core-guide/>.
- Isaac, Antoine, et Ed Summers. 2009. « SKOS Simple Knowledge Organization System Primer ». Working Group Note. W3C. <https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/>.


On va ainsi faire des liens entre différentes ressources. Simplement, un certain nombre de propriétés et de termes auront ici un sens particulier et permettront d’unifier des ressources hétéroclites.

Tout cela s’exprime sous la forme de triplets. Les concepts seront identifiés par des URI, ainsi que les relations entre ces concepts. Des étiquettes vont aussi permettre de fournir des valeurs de chaînes dans plusieurs langues. Il existe donc une notation Turtle ou RDF pour SKOS.

>SKOS Core provides a model for expressing the basic structure and content of concept schemes such as thesauri, classification schemes, subject heading lists, taxonomies, 'folksonomies', other types of controlled vocabulary, and also  concept schemes embedded in glossaries and terminologies.
>
>The SKOS Core Vocabulary is an application of the [Resource Description Framework (RDF)](http://www.w3.org/RDF/), that can be used to express a concept scheme as an RDF graph. Using RDF allows data to be linked to and/or merged with other data, enabling data sources to be  distributed across the web, but still be meaningfully composed and integrated.
>
>(Miles, Alistair, et Dan Brickley. 2005. « SKOS Core Guide ». Working Draft. W3C. <https://www.w3.org/TR/swbp-skos-core-guide/>.)

SKOS s’adapte à la diversité des systèmes d’organisation des connaissances

> [Nouveau] standard qui établit un pont entre le monde des systèmes d’organisation des connaissances (thésaurus, systèmes de classification, systèmes de rubrique, taxinomies et folksonomies) et la communauté Linked Data, pour servir les intérêts de tous. Les bibliothèques, musées, journaux, portails administratifs, entreprises, applications de réseaux sociaux et autres communautés qui gèrent de larges collections de livres, documents historiques, bulletins de presse, glossaires métier, billets de blogue, etc. peuvent désormais utiliser la spécification de système simple d’organisation des connaissances ([Simple Knowledge Organization System - SKOS](http://www.w3.org/TR/2009/REC-skos-reference-20090818/)) pour tirer pleinement parti du potentiel des données liées. Quand les différentes communautés disposant de vocabulaires établis et experts utilisent SKOS pour les intégrer au Web sémantique, elles ajoutent de la valeur à ces informations pour tous.
>
> (<http://www.bnf.fr/fr/professionnels/web_semantique_boite_outils/a.web_semantique_rdf_vocabulaires.html#SHDC__Attribute_BlocArticle3BnF>)


### SKOS Simple Knowledge Organisation System

| Concepts      | Labels & notation | Documentation | Relations sémantiques | Propriété de mapping | Collections       |
| ------------- | :---------------- | ------------- | --------------------- | -------------------- | ----------------- |
| Concept       | prefLabel         | note          | broader               | broadMatch           | Collection        |
| ConceptScheme | altLabel          | changeNote    | narrower              | narrowMatch          | orderedCollection |
| inScheme      | hiddenLabel       | definition    | related               | relatedMatch         | member            |
| hasTopConcept | notation          | editorialNote | broaderTransitive     | closeMatch           | memberList        |
| topConceptOf  |                   | example       | narrowerTransitive    | exactMatch           |                   |
|               |                   | historyNote   | semanticTransitive    | mappingRelation      |                   |
|               |                   | scopeNote     |                       |                      |                   |


Plusieurs espaces de noms sont utilisés, celui spécifique de SKOS, mais également rdf, rdfs, etc.

Plutôt que de parler de classe, on parle ici de concepts. Ce qu’on appelle un concept est ce qu’on appelle une classe ailleurs, mais le terme est plus général. Il peut s’agir d’unité de sens, de choses, etc. qui existent indépendamment de leur étiquette.

On peut ensuite associer à un concept, une manière d’y référer dans différentes langues naturelles.

- `skos:prefLabel` un seul
- `skos:altLabel` synonyme ou abréviation
- `skos:hiddenLabel` pour la machine seulement.

Pas quelque chose qui va permettre de faire des preuves mais plutôt quelque chose pour fédérer des ressources. C’est la raison pour laquelle beaucoup de soin a été mis sur les différentes manières de de désigner un même concept.

### Relations

#### Liens hiérarchiques

`skos:broader`

- du particulier au général
- de la partie vers le tout

Exemple des mammifères en relation avec un autre concept plus général. Pourrait dire que ceci est une sous-classe de cela, mais ici ne parle pas de sous-classe car pas les mêmes contraintes. On sait tout de même que certains concepts sont plus précis que d’autres.

`skos:narrower`

#### Liens associatifs

Il existe aussi des liens associatifs. Mais les liens seront relativement flou.

`skos:related`

### Documentation

De nombreux éléments définis par SKOS concernent la documentation.

- `skos:scopeNote`
- `skos:definition`
- `skos:example`
- `skos:historyNote`


<!-- .slide: data-background="/presentations/images/skosCore.png" data-background-size="contain" -->


SKOS Core définit :

- deux objets primitifs `ConceptScheme` et `Concept`
- de propriétés rattachées aux `Concept`
  - `prefLabel` une étiquette préférentielle par langue (vedettes)
  - `altLabel` des étiquettes alternatives (termes exclus)
  - `note`, `definition`, `example`, `scopeNote` qui concernent les notes d’application et la documentation
  - `broader`, `narrower` pour des liens vers d’autres `Concept` (liens hiérarchiques)
  - `related` des liens vers des `Concept` (liens associatifs)

skos: http://www.w3.org/2004/02/skos/core#

- A skos:Concept can be viewed as an idea or notion; a unit of thought. In CMSPV, we encode vocabulary terms as skos:Concept's.
- A skos:ConceptScheme can be viewed as an aggregation of one or more SKOS concepts. We encode the whole NIMS vocabulary as a skos:ConceptScheme.
- skos:inScheme is usually used to describe the relation that a skos:Concept "belongs to" a skos:ConceptScheme, such as, in our case, a NIMS term skos:inScheme the whole NIMS vocabulary.
- skos:topConceptOf is a sub-property of skos:inScheme, meaning a skos:Concept is important to a skos:ConceptScheme. For example, top-level categories are treated as top concepts of the NIMS vocabulary. We can see that multiple concepts can simultaneously be top concepts of the same concept scheme.
- skos:prefLabel and skos:altLabel mean the preferred and alternative labels, respectively. They are useful when generating or creating human-readable representations of a knowledge organization system. These labels provide the strongest clues as to the meaning of a SKOS concept.
- The properties skos:broader and skos:narrower are used to assert a direct hierarchical link between two SKOS concepts. A triple <A> skos:broader <B> asserts that <B>, the object of the triple, is a broader concept than <A>, the subject of the triple. Similarly, a triple <C> skos:narrower <D> asserts that <D>, the object of the triple, is a narrower concept than <C>, the subject of the triple. By convention, skos:broader and skos:narrower are only used to assert a direct (i.e., immediate) hierarchical link between two SKOS concepts. This provides applications with a convenient and reliable way to access the direct broader and narrower links for any given concept. Note that, to support this usage convention, the properties skos:broader and skos:narrower are not declared as transitive properties.

For the full list of classes and properties in SKOS as well as their detailed definitions, see [SKOS Simple Knowledge Organization System Reference](http://www.w3.org/TR/2009/REC-skos-reference-20090818/).


<!-- .slide: data-background="/presentations/images/SKOS-Model.png" data-background-size="contain" -->


SKOS Mapping

Langage d’alignement de vocabulaires qui définit différents types de correspondances :

- `Exact` correspondance parfaite
- `Inexact` correspondance imparfaite
  - `Major` > 50%
  - `Minor` < 50%
- `Partial`correspondance partielle
  - `Broad`, `Narrow` relation d’appartenance

skos: http://www.w3.org/2004/02/skos/core#

> - A skos:Concept can be viewed as an idea or notion; a unit of thought. In CMSPV, we encode vocabulary terms as skos:Concept’s.
> - A skos:ConceptScheme can be viewed as an aggregation of one or more SKOS concepts. We encode the whole NIMS vocabulary as a skos:ConceptScheme.
> - skos:inScheme is usually used to describe the relation that a skos:Concept "belongs to" a skos:ConceptScheme, such as, in our case, a NIMS term skos:inScheme the whole NIMS vocabulary.
> - `skos:topConceptOf` is a sub-property of `skos:inScheme`, meaning a `skos:Concept` is important to a `skos:ConceptScheme. For example, top-level categories are treated as top concepts of the NIMS vocabulary. We can see that multiple concepts can simultaneously be top concepts of the same concept scheme.
> - skos:prefLabel and `skos:altLabel` mean the preferred and alternative labels, respectively. They are useful when generating or creating human-readable representations of a knowledge organization system. These labels provide the strongest clues as to the meaning of a SKOS concept.
> - The properties `skos:broader` and `skos:narrower` are used to assert a direct hierarchical link between two SKOS concepts. A triple \<A> `skos:broader` \<B> asserts that \<B>, the object of the triple, is a broader concept than \<A>, the subject of the triple. Similarly, a triple \<C> `skos:narrower` \<D> asserts that \<D>, the object of the triple, is a narrower concept than \<C>, the subject of the triple. By convention, `skos:broader` and `skos:narrower` are only used to assert a direct (i.e., immediate) hierarchical link between two SKOS concepts. This provides applications with a convenient and reliable way to access the direct broader and narrower links for any given concept. Note that, to support this usage convention, the properties skos:broader and skos:narrower are not declared as transitive properties.
>

For the full list of classes and properties in SKOS as well as their detailed definitions, see [SKOS Simple Knowledge Organization System Reference](http://www.w3.org/TR/2009/REC-skos-reference-20090818/).


<!-- .slide: data-background="/presentations/images/skossRameau.png" data-background-size="contain" -->

Deux concepts de Rameau représentés sous forme de graphe RDF/SKOS


Travail interconnexion RAMEAU LCSH

Source : Isaac, Antoine, et Bouchet. 2009. « Rameau et SKOS ». *Arabesques*, juin 2009. <http://rameau.bnf.fr/informations/pdf/arabesques54_art_isaac_bouchet.pdf>.

Projet de RAMEAU -> SKOS lancé début 2008, projet TELplus

http://www.few.vu.nl/~aisaac/


### Exemple SKOS

```xml
<skosConcept 
rdf:about="http://www.ihr-tobias.org/concepts/21250/Abdication">
    <skos:prefLabel>Abdication</skos:prefLabel>
</skosConcept>
```

exemple tiré du [thesaurus of British and Irish History](http://www.history.ac.uk/projects/digital/tobias)


### Exemple SKOS

```xml
<skosConcept 
rdf:about="http://www.ihr-tobias.org/concepts/21250/abdication">
    <skos:prefLabel>Abdication</skos:prefLabel>
    <skos:narrower rdf:resource="http://www.ihr-tobias.org/concepts/19838/abdication_crisis_1936"/>
</skosConcept>
```

exemple tiré du [thesaurus of British and Irish History](http://www.history.ac.uk/projects/digital/tobias)


Visionner ce RDF en Turtle avec [EasyRDF](http://www.easyrdf.org/converter)


### Thesaurus

> vocabulaire contrôlé et structuré dans lequel les concepts sont représentés par des termes, et organisés de manière à rendre explicite les relations entre les concepts les termes préférentiels sont accompagnés de synonymes ou quasi-synonymes

- on distingue les thésaurus des autres types de vocabulaires contrôlés
- une norme adaptée aux évolutions des systèmes d’information
- une norme en phase avec le web sémantique et ses standards

[norme ISO 25964](https://www.iso.org/fr/standard/53657.html)

- partie 1 : thésaurus pour la recherche documentaire (2011)
- partie 2 : interopérabilité avec des vocabulaires (2013)


### Vocabulaires contrôlés

lexique, ensemble fermé de termes de description (motset expression) soigneusement choisis pour un domaine accompagnés de leurs définitions précises

utilisés pour étiqueter des documents de manière à ce qu'ils soient plus facilement repérables lors d'une recherche

Résoudre des problèmes : 

- d’homographie  | de polysémie | de synonymie
- réduire l’ambiguïté inhérente au langage naturel
- différents noms peuvent être attribués à un même concept

### Thesaurus

norme ISO 25964

- partie 1 : thésaurus pour la recherche documentaire (2011)
- partie 2 : interopérabilité avec des vocabulaires (2013)

souvent utilisés pour les documents techniques ou dans des domaines spécialisés (vocabulaires métiers)

> vocabulaire contrôlé et structuré dans lequel les concepts sont représentés par des termes, et organisés de manière à rendre explicite les relations entre les concepts les termes préférentiels sont accompagnés de synonymes ou quasi-synonymes.
>
> (norme ISO 25964)

- on distingue les thésaurus des autres types de vocabulaires contrôlés
- une norme adaptée aux évolutions des systèmes d’information
- une norme en phase avec le web sémantique et ses standards


### Exemples de thesaurus

- **Icon Class** (iconographic description) 

  <http://www.iconclass.org/>

- **Getty Arts and Architecture thesaurus** (AAT) 

  <http://www.getty.edu/research/conducting_research/vocabularies/aat/>

- **Getty Union List of Artist** (ULAN) 

  <http://www.getty.edu/research/conducting_research/vocabularies/ulan/>

- **Getty Thesaurus of Geographical Names** (TGN) 

  <http://www.getty.edu/research/conducting_research/vocabularies/tgn>


### TP SKOS Play

http://labs.sparna.fr/skos-play

1. Naviguer dans le thesaurus de désignation architecturale du ministère de la Culture et de la communication en France 
   http://data.culture.fr/thesaurus/

2. Télécharger le vocabulaire au format SKOS

3. Prendre connaissance du fichier, de sa structure, identifier les liens internes et externes

4. Visualiser le fichier dans SKOS Play


### Logiciels

OpenTheso https://github.com/miledrousset/opentheso

Ginco http://www.culture.gouv.fr/Divers/Harmonisation-des-donnees-culturelles/Referentiels/Les-vocabulaires-scientifiques-et-techniques/L-application-GINCO

Terminology Management Platform (TMP) http://linkedheritage.eu

Open Refine http://openrefine.org

Karma http://usc-isi-i2.github.io/karma/

Skosmos http://skosmos.org/


https://www.jlis.it/article/view/5471


### Linked Open Vocabularies (LOV)

https://lov.linkeddata.es/dataset/lov/

### Schema.org

https://schema.org

> Schema.org is a collaborative, community activity with a mission to create, maintain, and promote schemas for structured data on the Internet, on web pages, in email messages, and beyond.

https://doremus-anr.github.io/schema-visualizer/


## 2. Ontologies (RDFs et OWL)


### Les ontologies

une description formelle explicite des concepts partagés dans un domaine donné et des relations entre ces concepts

- contient des définitions lisibles en machine des concepts (classes) et de leurs relations
- caractéristiques et attributs du concepts (rôles ou propriétés)
- restrictions sur les attributs (facettes ou restrictions de rôles)
- permet de formuler des raisonnements

une ontologie définit **une conceptualisation commune** pour une communauté qui a besoin de partager l’information dans un certain domaine


En sciences de l’informatique, une ontologie est une spécification formelle d'un modèle conceptuel lisible par la machine dans laquelle les concepts, propriétés,relations, fonctions, contraintes et axiomes sontexplicitement définis

- pas un vocabulaire contrôlé proprement dit
- mais peut en employer un ou plusieurs

Une description formelle explicite des concepts partagés dans un domaine donné et des relations entre ces concepts

- contient des définitions lisibles en machine des concepts (classes) et de leurs relations
- caractéristiques et attributs du concepts (rôles ou propriétés)
- restrictions sur les attributs (facettes ou restrictions de rôles)
- permet de formuler des raisonnements

**une ontologie définit une conceptualisation commune pour une communauté qui a besoin de partager l’information dans un certain domaine**


### Les ontologies (définitions)

> **An ontology is an explicit specification of a conceptualization.** The term is borrowed from philosophy, where an Ontology is a systematic account of Existence. For AI systems, what “exists” is that which can be represented. When **the knowledge of a domain is represented in a declarative formalism**, the set of objects that can be represented is called the universe of discourse. This set of objects, and the describable relationships among them, are reflected in the representational vocabulary with which a knowledge-based program represents knowledge. Thus, in the context of AI, we can describe the ontology of a program by defining a set of representational terms. In such an ontology, definitions associate the names of entities in the universe of discourse (e.g., classes, relations, functions, or other objects) with human-readable text describing what the names mean, and formal axioms that constrain the interpretation and well-formed use of these terms. Formally, an ontology is the statement of a logical theory. 
>
> (Thomas R. Gruber, 1993 http://tomgruber.org/writing/onto-design.htm)


### Notion d’ontologie

Une ontologie est un ensemble de déclarations descriptives explicites à propos du monde (habituellement référée comme le domaine d’intérêt ou le sujet de l’ontologie). Par leur caractère explicite, ces descriptions satisfont plusieurs fonctions :

- prévenir l’ambiguïté et l’incompréhension dans la communication (explicites)
- se comporter de manière uniforme et prévisible pour fonctionner dans un environnement logiciel

http://www-ksl.stanford.edu/kst/what-is-an-ontology.html

http://tomgruber.org/writing/onto-design.htm


> An ontology is an explicit, formal specification of a shared conceptualization. (Thomas R. Gruber, 1993)

> […] ontologies are defined as a formal specification of a shared conceptualization. (Borst 1997)

> […] an ontology is a formal, explicit specification of a shared conceptualization.
> Conceptualization refers to an abstract model of some phenomenon in the world by having identified the relevant concepts of that phenomenon.
> Explicit means that the type of concepts used, and the constraints on their use are explicitly defined.
> Formal refers to the fact that the ontology should be machine readable.
> Shared reflects the notion that an ontology captures consensual knowledge, that is, it is not private of some individual but accepted by a group. (Studer 1998)


Il faut ici souligner plusieurs notions : 

- Conceptuatlisation : modèle abstrait du domaine et ses expressions en rapport
- Spécification : relative à un domaine
- Explicite : la sémantique de toutes les expressions est claire
- Formelle : lisible par la machine
- Shared : consensus dans une communauté

En somme, il s’agit de produire :

- langage commun (symboles, expressions) —> syntaxe
- signification des symboles et expressions claires —> sémantiques
- les symboles et expressions de sémantique similaire sont groupés en classes —> conceptualisation
- les concepts sont organisés de manière hiérarchique —> taxonomie
- du savoir implicite peut être rendu explicite —> raisonnement

cf. https://fr.slideshare.net/UMR7324/therese-libourel-ontologiesshs20151109tours?qid=5b2c86c6-d0ec-4194-af1d-6ff9dc9a22b7&v=&b=&from_search=9

https://keet.wordpress.com/2017/01/20/on-that-shared-conceptualization-and-other-definitions-of-an-ontology/

### Biblio

- Doerr, Martin, Stefan Gradmann, Steffen Hennicke, Antoine Isaac, Carlo Meghini, et Herbert van de Sompel. 2010. « The Europeana Data Model (EDM) ». Dans *Subject Analysis and Access*. . Gothenburg, Sweden : IFLA. https://www.ifla.org/past-wlic/2010/149-doerr-en.pdf.
- Oldman, Dominic. 2014. « The CIDOC Conceptual Reference Model (CIDOC-CRM): PRIMER | CIDOC CRM ». CIDOC. Consulté le 19 mars 2021. http://www.cidoc-crm.org/Resources/the-cidoc-conceptual-reference-model-cidoc-crm-primer.
- Juanals, Brigitte et Jean-Luc Minel. 2016. La construction d’un espace patrimonial partagé dans le Web de données ouvert. *Communication* 34 n° 1 p. doi :10.4000/communication.6650. <https://communication.revues.org/6650>.
- Bruseker, George, Nicola Carboni, et Anaïs Guillem. 2017. « Cultural Heritage Data Management: The Role of Formal Ontology and CIDOC CRM ». Dans *Heritage and Archaeology in the Digital Age: Acquisition, Curation, and Dissemination of Spatial Cultural Heritage Data*. Sous la direction de Matthew L. Vincent, Víctor Manuel López-Menchero Bendicho, Marinos Ioannides, et Thomas E. Levy, 93‑131. Quantitative Methods in the Humanities and Social Sciences. Cham : Springer International Publishing. https://doi.org/10.1007/978-3-319-65370-9_6.


### RDF Schema

- Premier brouillon du W3C en avril 1998
- Recommandation en février 2004

#### **RDF Schema** définit **un modèle de données** pour la création de déclarations RDF.

### Le vocabulaire autorise :

- la définition de **classes**
- l’**instantiation de classes** en RDF avec `rdf:type`
- la définition de **propriétés** et de **restrictions**
- la définition de **hiérarchies**
  - sous-classes et super-classes
  - sous-propriétés et super-propriétés


Les ontologies qui peuvent être définies au moyen des standards RDF schéma (RDFs) et du Web Ontologie Language (OWL), ces formats peuvent contenir à la fois des définitions informelles sous la forme de documentation pour les humains et des documentations formelles sous la forme de règles et de contraintes qui permettent de détecter des inconsistances ou de dériver de nouveaux faits à partir d’assertions.

Une ontologie peut, par exemple, définir des classes pour des livres des peintures, des tableaux et des personnes, une propriété d’auteur, et déclarer formellement que toutes les ressources connectées aux livres par la propriété auteur sont de type personne. Elle peut aussi formellement définir une autre classe d’objet comme une superclasse des livres et des peintures. En employant un moteur d’inférence sur les données de la collections de peinture et de livres, et en cherchant tous les objets créés par une personne, on pourra retrouver tous ces objets, sans connaissance préalable de leur type spécifique ; une fonctionnalité cruciale dès lors que l’intégration d’information est requise.

Pour en savoir plus sur les ontologies : https://fr.slideshare.net/SergeLinckels/semantic-web-ontologies-212812210

### RDFs

Depuis la semaine dernière, on vous vend l’idée que le web sémantique nous permettrait de faire des déductions à partir de faits documentés. Toutefois, jusqu’ici on n’a pas fait grand chose. On s’est contenté de combiner des requêtes, etc. Les seules déductions que l’on ait faites consistaient à savoir dire si x est marié a y, etc.

Pour pouvoir formuler ce genre de déductions, nous allons avoir besoin de pouvoir intégrer plus de sémantique. C’est ce que va permettre RDFs en introduisant les notions de classes et de propriétés.

RDFs est un vocabulaire pour la modélisation de données RDF sépcifié par le W3C à partir de 2014. La version courante est la 1.1 qui date de 2014. 

https://www.w3.org/TR/rdf-schema/

**Il s’agit de quelque chose de bâti par-dessus RDF.** Avec RDFs, il sera possible de définir les notions de classe, d’instances de classes et de spécifier les relations entre ces classes par des propriétés.

- Classes
- Instances
- relations


### La représentation des connaissances en RDF

- Toute information est encodée comme un triplet
- un fait complexe est encodé comme une conjonction de triplets élémentaires
- on ne peut exprimer la négation ou la disjonction
- on peut déduire des nouvelles informations à l’aide d’un processus d’implication (*entailment*)


Exemple de typage, rappelle l’utilisation des types XML Schema

### RDFs types

RDF permet d’exprimer des énoncés simples à propos de ressources, de propriétés et de valeurs, mais il est nécessaire de pouvoir définir le vocabulaire utilisé dans ces énoncés —> RDFs

En RDF, toutes les ressources disposent d’un type (ou plusieurs) appelé classe. Ces classes peuvent être organisées en hiérarchies (classes, sous-classes).

- le type est une sorte ou classes de ressources
- les entités d’une même classe partagent des propriétés

e `rdf:type`, `rdfs:Class`, `rdfs:subClassOf`

### par ex. :

- Livre : auteur, titre, sujet...
- Personne : nom, prénom, titre, adresse, âge
- Entreprise : nom de société, nombre d’employés, adresse


### Vocabulaire RDFs, les **Classes**

### `rdf:Class`
concept de classe, définit un objet abstrait qui est appliqué avec `rdf:type` pour créer des instances

### `rdf:Property`
classe de base pour les propriétés

### `rdfs:Resource`
toutes les entités du modèle RDF sont instances de cette classe

### de plus :

`rdf:Datatype`, `rdf:XMLLiteral`, `rdfs:Container`, `rdfs:ContainerMembershipProperty`.


### Classes de RDFs et RDF

### Classes fondamentales

- `rdfs:Resource`
- `rdfs:Class`
- `rdfs:Literal, rdf:XMLLiteral`
- `rdfs:Property`
- `rdf:Statement`

### Relations

- `rdf:type`
- `rdfs:subClassOf`
- `rdfs:subPropertyOf`

Type et liens entre les propriétés et des classes

#### Pour les propriétés

- `rdfs:domain` (dont les ressources peuvent être sujet)
- `rdfs:range` (dont les ressource peuvent être objet)


### Propriétés pour la réification  Statement, subject, prédicateur, object

#### Container

- `rdf:Bag`, `rdf:Seq`, `rdf:Alt`
- `rdf:List`, `rdf:first`, `rdf:rest`
- `rdfs:Container`, `rdfs:ContainerMembershipProperty`, `rdfs:member`

#### Autres propriétés auxiliaires (documentation pour les humains, pas de sémantique associée)

- `rdf:seeAlso` (lien vers une autre propriété qui l’expliqque
- `rdfs:isDefinedBy`
- `rdfs:comment`
- `rdfs:label`


### Containers

On peut aussi construire par dessus RDF un certain nombre de structures avec les *containers*. Ici reste dans RDF. Pour le moment, on se contentait de dire que l’on avait des relations entre a et b. Mais si veut dire que l’on a un cours et que des étudiants font partie de ce cours là, et que ce cours là, c’est l’ensemble de ses étudiants. Comme il s’agit de cas de cas de figure courants, on a défini en RDF des containers pour prendre en charge ces cas là.

Un type prédéfini destiné à exprimer le fait qu’on ait un ensemble d’étudiants. Ce qui dit que c’est un container, c’est que son type, l’URI de RDF bag.

http://www.w3c.org/1999/02/22-rdf-syntax-ns#Bag

en fait on a un nœud vide, et son type, le type prédéfini de bag.

Les éléments du bag sont codés à la suite en étant numérotés.

Pour accéder à tous les étudiants de ce bag, possibilité de faire des expressions régulière sur la valeur. Mais il existe ici un rdfs:member qui est un prédicat spécial interprété par l’interprète SPARQL.

Notation qui emploie des noms internes.

également les containers alt, collection, etc.


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-19-638.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-21-638.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-22-638.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-23-638.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-24-638.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-25-638-1.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-27-638-1.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-27-638.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/openhpi-26-how-to-model-classes-and-relations-rdfs-28-638.jpg" data-background-size="contain" -->


https://www.w3.org/TR/rdf11-primer/


```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix ex: <http://www.example.org/schemas/vehicles#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
### Classes
ex:MotorVehicle rdf:type rdfs:Class .
ex:PassengerVehicle
	rdf:type rdfs:Class ;
    rdfs:subClassOf ex:MotorVehicle .
ex:Truck
      rdf:type rdfs:Class ;
      rdfs:subClassOf ex:MotorVehicle .
ex:Van
      rdf:type rdfs:Class ;
      rdfs:subClassOf ex:MotorVehicle .
ex:MiniVan
      rdf:type rdfs:Class ;
      rdfs:subClassOf ex:PassengerVehicle , ex:Van .
```


### Propriétés associant les classes

### **rdfs:domain** : propriété qui s’applique à une classe de ressource

- absent: toute ressource peut utiliser cette propriété
- 1 fois : s’applique aux instances de cette classe
- plusieurs fois : s’applique à des instances de toutes ces classes à la fois

### **rdfs:range** : classe des valeurs possibles

- absent: aucune restriction
- 1 fois: doit être instance de ce type
- plusieurs fois: instance de **toutes** ces classes


```rdf
ex:Person
	rdf:type rdfs:Class .
<http://www.w3.org/2001/XMLSchema#integer>
	rdf:type rdfs:DataType .
ex:registeredTo
	rdf:type rdf:Property ;
    rdfs:domain ex:MotorVehicle ;
	rdfs:range ex:Person .
ex:rearSeatLegRoom
	rdf:type rdf:Property ;
	rdfs:domain ex:PassengerVehicle ;
	rdfs:range <http://www.w3.org/2001/XMLSchema#integer> .
ex:driver
      rdf:type rdf:Property ;
      rdfs:domain ex:MotorVehicle .
ex:primaryDriver
      rdf:type rdf:Property ;
      rdfs:subPropertyOf ex:driver .
### Instances
ex:johnSmithsCar
    rdf:type ex:PassengerVehicle ;
    ex:primaryDriver <http://www.example.org/staffid/85740> ;
    ex:rearSeatLegRoom "127"^^<xsd:integer> ;
	ex:registeredTo <http://www.example.org/staffid/85740> .
```


<!-- .slide: data-background="/presentations/images/CBWC-RDF-S.png" data-background-size="contain" -->

http://www.iro.umontreal.ca/~lapalme/ForestInsteadOfTheTrees/HTML/ch07s01.html


### TP RDFs

Téléchargez le fichier suivant `https://publicarchi.github.io/edn6103/exercices/CBWC-RDF-S.ttl`

Modifier le fichier local pour y ajouter les informations du tableau suivant associées à des vins qui sont déjà dans le fichier mais sans autre information.

Il faut aussi indiquer que le rdf:type de ces éléments est cb:Wine.

| uri   | wc:C00871996       | wc:C00042101   | wc:C00043125             |
| ----- | ------------------ | -------------- | ------------------------ |
| nom   | Château Montguérêt | Riesling Hügel | Domaine de l’Île Margaux |
| prix  | 14.65              | 7.95           | 22.80                    |
| année | 2011               | 2002           | 2004                     |

Comment faudrait-il procéder pour

1. Lister les vins (noms, prix et année) en ordre croissant d’année.
2. Lister les vins (noms, prix et année) en ordre croissant de prix.
3. Indiquez les types pour les prix (xsd:decimal) et les années (xsd:gYear).
4. Lister les vins (noms, prix et année) en ordre croissant de prix.
5. Lister les vins (noms, prix et année) en ordre croissant de prix en n’affichant pas les indications de type.

Solutions SPARQL http://www.iro.umontreal.ca/~lapalme/ift6281/RDF/ExerciceRDF.pdf


### Web Ontology Language (OWL)

Est un langage de schéma ou un langage de représentation de la connaissance du web sémantique. OWL permet de définir des concepts de manière à pouvoir les réutiliser. 

<http://www.w3.org/TR/owl2-overview/>

<http://www.w3.org/TR/owl2-primer/>


> **OWL (Web Ontology Language):** The schema language, or knowledge representation (KR) language, of the Semantic Web. OWL enables you to define concepts composably so that these concepts can be reused as much and as often as possible. Composability means that each concept is carefully defined so that it can be selected and assembled in various combinations with other concepts as needed for many different applications and purposes

Différences entre SKOS et OWL

> SKOS fait partie de la pile technologique du [Web sémantique](http://www.w3.org/2001/sw/). Comme le langage d’ontologie Web (Web Ontology Language ou OWL), SKOS peut servir à définir des vocabulaires. Cependant, ces deux technologies servent des besoins différents. SKOS est un simple langage comportant juste quelques fonctions, optimisées pour le partage et la liaison des systèmes d’organisation des connaissances tels que thésaurus et systèmes de classification. OWL fournit une structure générale et puissante pour la représentation des connaissances, dont la « rigueur » confère d’autres avantages tels que le traitement des règles métier.
>
> https://www.w3.org/2009/07/skos-pr


### OWL Web Ontology Language

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

cf. https://www.w3.org/TR/owl2-primer/


**Principe :** un langage déclaratif pour exprimer des ontologies. Il ne s’agit pas d’un langage de schéma, et c’est un monde ouvert, ce qui change la façon de faire des preuves.

En OWL on se retrouve avec des axiomes, cad un ensemble d’énoncés de base supposés vrais. On a également des entités qui font référence à… Puis des expressions. L’ensemble formant une ontologique.

On y trouvera des énoncés de base et on parlera de conséquences des énoncés. On exprime des relations entre des énoncés, ensuite pourra voir si un énoncé a est vrai si d’autres A le sont. A entraîne (entails) a. Alors on dira que A est consistant si une situation où tous ses énoncés sont vrais.

**Modélisation de base :** être capable de définir des classes, des sous-classes, des propriétés et des sous-propriétés, des restrictions sur des propriétés, etc. Série d’éléments qui correspondent un peu à ce que peut faire avec RDFs mais plus riche

- classes et instances
- hiérarchies de classes
- propriétés d’objects
- hiérarchies de propriétés
- Restrictions sur les propriétés
- égalité des individus
- types des valeurs de propriétés

**Ensuite relations avancées de classes :** définition de classes complexes, restrictions de propriétés (ex famille nombreuse, plus de x individus enfants), mais aussi de cardinalice, énumérations d’individus. Choses qui s’expriment aussi en logique de premier ordre.

- classes complexes
- restrictions de propriétés
- restrictions de cardinalité
- énumérations d’individus

**Utilisation avancée des propriétés**

- caractéristiques des propriétés
- chaînes de propriétés
- clés


### Classes

Les classes groupent tous les individus qui partagent des propriétés pour y faire référence. Les classes représentent ainsi essentiellement des ensembles d’individus. 

En modélisation, les classes sont souvent employées pour dénoter l’ensemble des objets compris par un concept dans la pensée humaine : par exemple, le concept de *personne* ou de *femme*.

- Hiérarchies de classes
- Instances de classes (individus)
- Propriétés

cf. https://www.w3.org/TR/owl2-primer/#CWhat_is_OWL_2.3F


@todo compléter


#### Assertion de classes

- `ClassAssertion( :Woman :Mary )`

#### Hiérarchie de classe

- `SubClassOf( :Woman :Person )`
- `SubClassOf( :Mother :Woman )`

#### Équivalence de classe

- `EquivalentClasses( :Person :Human )`

#### Classe disjointe

- `DisjointClasses( :Woman :Man )`


### Syntaxe fonctionnelle

Assertion de classe, équivalent de *est membre de*, est une instance de. Les classes sont généralement utilisées pour regrouper les individus qui partagent des caractéristiques pour y faire référence. Ainsi, les classes représentent essentiellement des ensembles d’individus.

Le fait d’appartenir à une classe n’est pas exclusif.

Si on veut décrire le fait qu’il existe des hommes et des femmes, il est courant en modélisation d’ontologie d’avoir recours à des sous-classes pour déclarer les interdépendances mais aussi spécifier les relations de généralisation.

Un raisonneur peut ainsi dériver, pour chaque individu, que si c’est une mère, c’est une femme. Techniquement les relations de sous-classes sont transitives.

Notion d’équivalence de classe.

Incompatibilité d’individu, équivalence de classe. Souvent omis car intuitivement les classes sont considérées disjointes. Cependant cette propriété peut s’avérer précieuse pour les déductions. Ici on a a besoin pour déduire que Mary n’est pas un homme.


#### Propriétés

- `ObjectPropertyAssertion( :hasWife :John :Mary )`
- ` NegativeObjectPropertyAssertion( :hasWife :Bill :Mary )`

#### Hiérarchies de propriétés

- `SubObjectPropertyOf( :hasWife :hasSpouse )`

#### Restrictions de domaine et de portée

- `ObjectPropertyDomain( :hasWife :Man )`
- `ObjectPropertyRange( :hasWife :Woman )`

#### Égalité et inégalité des individus

- `DifferentIndividuals( :John :Bill )`
- `SameIndividual( :James :Jim )`


#### Classes complexes

- `ObjectIntersectionOf`
- `ObjectUnionOf`
- `ObjectComplementOf` 
- `ObjectComplementOf`

```
EquivalentClasses(
   :Parent 
   ObjectUnionOf( :Mother :Father )
 ) 
```

```
EquivalentClasses(
   :ChildlessPerson 
   ObjectIntersectionOf(
     :Person 
     ObjectComplementOf( :Parent )
   )
 ) 
```


```
SubClassOf( 
   :Grandfather 
   ObjectIntersectionOf( :Man :Parent )
 )
```

```
ClassAssertion(
   ObjectIntersectionOf(
     :Person 
     ObjectComplementOf( :Parent )
   ) 
   :Jack
 )
```


### Éditeurs d’ontologies

https://protege.stanford.edu (libre et open source)

http://owlgred.lumii.lv

VOWL: Visual Notation for OWL Ontologies http://purl.org/vowl/spec/


### TP visualiser l’ontologie FOAF

- Prendre connaissance de l’ontologie Friend Of a Friend

  [FOAF Vocabulary Specification](http://xmlns.com/foaf/spec/)

- Visualiser FOAF avec WebVOWL

  http://visualdataweb.de/webvowl/#iri=http://xmlns.com/foaf/0.1/

### Décrire la classe avec FOAF

- Histoire de réviser un peu sa notation turtle, produisez une notice personnelle avec FOAF
- Visualiser le graphe produit avec [EasyRDF](http://www.easyrdf.org/converter) ou [RDF grapher](https://www.ldf.fi/service/rdf-grapher)

cf. [WebVOWL: Web-based Visualization of Ontologies](http://vowl.visualdataweb.org/webvowl.html)


<!-- .slide: data-background="/presentations/images//presentations/images/foaf.jpg" data-background-size="contain" -->


<!-- .slide: data-background="/presentations/images/FOAF_concept_view.svg" data-background-size="contain" -->


### Exemples d’ontologies

[BIBO](http://bibliontology.com/) (Bibliographical Ontology)

[SPAR](http://www.sparontologies.net) - Semantic Publishing and Referencing Ontologies.

[BIBFRAME](https://www.loc.gov/bibframe/docs/bibframe2-model.html) Bibliographic Framework

[PROV-O](https://www.w3.org/TR/prov-o/) - Represent provenance information.

### Exemple BBC ontologies

https://www.bbc.co.uk/ontologies

[CIDOC-CRM](http://www.cidoc-crm.org/) – CIDOC Conceptual Reference Model


### Trouver des ontologies

http://prefix.cc

http://kmi.open.ac.uk/technologies/theme/semantic-web-and-knowledge-services

https://lov.linkeddata.es

http://vocab.deri.ie

https://ontindex.io

http://bioportal.bioontology.org

https://treegenesdb.org/ontologies_directory

http://ontologydesignpatterns.org

http://ontolog.cim3.net/wiki/

https://protegewiki.stanford.edu/wiki/Protege_Ontology_Library

http://schemapedia.com

http://linkeddata.org

https://ckan.org


### Discussion

### **Quelles opportunités pour le domaine éditorial ?**

--

- Quelles conséquences sur le format livre ?

--

- Quelles sources de données pourraient être utiles ?

--

- Quels types d’applications possibles ?


### Biblio

- Allemang, Dean, James A Hendler, et Fabien Gandon. 2020. *Semantic web for the working ontologist: effective modeling for linked data, RDFS, and OWL*.
- Doerr, Martin. 2009. Ontologies for Cultural Heritage. *Handbook on Ontologies.* p. 463-486. DOI : 10.1007/978-3-540-92673-3
- Gandon, Fabien. 2012. Le web sémantique: comment lier les données et les schémas sur le web. Paris : Dunod. InfoPro. Management des systèmes d’information. ISBN 9782100572946.
- Hitzler, Pascal, Markus Krötzsch, Sebastian Rudolph. 2009. *Foundations of Semantic Web Technologies.* CRC Press. ISBN-10: 142009050X
- Yu, Liyang. 2014. *A Developer’s Guide to the Semantic Web.* 2e éd. Springer. ISBN-10: 3662437953.
- Van Holland Seth, Ruben Verborgh. 2014. *Linked Data for Libraries, Archives and Museums, How to clean, link and publish your metadata.* Facet publishing. ISBN 9781783300389


### Lectures muséologie, culture

- Bermès, Emmanuelle dir. 2013. *Le Web sémantique en bibliothèque*. « Bibliothèques ». Paris : Édition du Cercle de la Librairie. ISBN 9782765414179
- Eero Hyvönen. 2012. *Publishing and Using Cultural Heritage Linked Data on the Semantic Web.* Synthesis Lectures on semantic web : Theory and technology. Morgan & Claypool publishers. ISBN 1608459985
- Juanals, Brigitte et Jean-Luc Minel. 2016. « La construction d’un espace patrimonial partagé dans le Web de données ouvert. » Communication vol. 34 n° 1. doi :10.4000/communication.6650. <https://communication.revues.org/6650>
- Szekely, Pedro, Craig A. Knoblock, Fengyu Yang, Eleanor E. Fink, Shubham Gupta, Rachel Allen, et Georgina Goodlander. Publishing the Data of the Smithsonian American Art Museum to the Linked Data Cloud. International Journal of Humanities and Arts Computing.vol. 8 n° supplement, 2014. 152-166. <https://doi.org/10.3366/ijhac.2014.0104>
