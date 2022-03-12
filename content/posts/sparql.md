+++
author = "Emmanuel"
title = "SPARQL"
date = "2022-03-10"
description = "SPARQL"
seance = 2
layout = "diapo"
diapo = "seance-03.html"
toc = "oui"
sommaire = "oui"
impression = "oui"
+++
## 1. Le protocole et le langage de requête SPARQL

### La pile des technologies du web sémantique

![](/presentations/images/sw_layercake.png)


### Rappels sur la notation Turtle

#### Notation des IRI (rappels)

[Internationalized Resource Identifiers](https://tools.ietf.org/html/rfc3987) (IRIs)

- Les IRI sont encadrées par des chevrons ouvrants et fermants

  `<http://monIri.ca/ontologie#concept>`

#### Notation des triplets (rappels)

Un triplet est noté par trois IRI suivis par un point. Ils désignent respectivement le sujet, le prédicat et l’objet RDF. 

```turtle
<sujet> <prédicat> <objet> .
```

```turtle
ex:s ex:p ex:q .
```

L’objet peut aussi être un littéral 

```turtle
ex:s ex:p "o" .
```

### Remarques

Un triplets regroupe trois composantes, séparées par un espace pour éviter les ambiguïtés.

Ne pas oublier le point final.


### Définitions de préfixes (rappels)

Un préfixe pour un IRI est défini par

`PREFIX *ident*: *IRI* .`

Exemple :

```turtle
PREFIX ex: <http://publicarchitectura/exemple#> .
```

Ce préfixe est utilisé à une déclaration pour former l’IRI complet. Ainsi `ex:toto` désignera l’IRI `<http://publicarchitectura/exemple#toto>`. 

L’identificateur de préfixe peut être vide.


### Raccourcis

Lorsqu’un **sujet est partagé par plusieurs triplets** successifs, les paires prédicat et objet sont séparées par un point-virgule : `;`

```turtle
ex:s ex:p1 "o1" ; ex:p2 "o2" .
```

```turtle
ex:s ex:p1 "o1" . 
ex:s ex:p2 "o2" .
```

Lorsqu’un **sujet et un prédicat sont communs** à plusieurs déclarations, ces dernières sont séparées par des virgules

`ex:s ex:p ex:o , "o1".`

```turtle
ex:s ex:p ex:o. 
ex:s ex:p "o1".
```

**Attention** ! dans ce contexte, les parenthèses sont utilisées pour dénoter des collections


### Notation des nœuds anonymes

Plusieurs notations possibles :

-  `[ ]`
-  `_:`

La notation avec crochets permet de combiner des triplets avec les raccourcis `,` et `;`

| `[ex:p "o"] .`             | `_:b1 ex:p "o" .`                    |
| -------------------------- | ------------------------------------ |
| `[ex:p "o"] ex:q ex:o2 .`  | `_:b2 ex:p "o". _b2 ex:q ex:o2 .`    |
| `ex:s ex:p [ex:p1 ex:o]. ` | `ex:s ex:p _:b3 . _:b3 ex:p1 ex:o .` |
| `[ex:p ex:o; ex:p1 "o1"].` | `_:b4 ex:p ex:o . _:b4 ex:p1 "o1" .` |


### Constantes et littéraux

Les constantes sont des **chaînes de caractères** entourées par des guillemets simples `’` ou doubles `"`

Il est possible de **typer les littéraux** avec [XML Schema](https://www.w3.org/TR/xmlschema-2/)

- suffixe `^^` suivi immédiatement du type xsd
- déclarer le préfixe avec `@PREFIX xsd: http://www.w3.org/2001/XMLSchema-datatypes .`

```
"3"^^xsd:integer
"1.4"^^xsd:decimal
"2019-03-12T12:34:45"^^xsd:dateTime
```

- entier `1 ≡ "1"^^xsd:integer`
- décimal `1.2 ≡ "1.2"^^xsd:decimal`
- exposant `1.2e8 ≡ "1.2e8"^^xsd:double`

Il est aussi possible d’étiqueter la langue d’une chaîne de caractères avec le suffixe `@` et un code langue ISO

- `"toto"@fr`
- `"toto"@en`


### SPARQL Protocol and RDF Query Language

SPARQL est [un ensemble de recommandations du W3C](https://www.w3.org/2009/sparql/wiki/Main_Page) pour travailler des bases de triplets RDF

- un protocole
- un langage de requête et de manipulation de données

Syntaxe basée sur la définition de modèles de triplets comportant des variables

### Standards

- SPARQL 1.1 standardisé par le W3C en 2013 (ensemble de [11 recommandations](https://www.w3.org/TR/sparql11-overview/))
- SPARQL 1.0 en janvier 2008

Prononcer *sparkle* en anglais : « étincelle »

Acronyme récursif qui signifie **\*S**PARQL **P**rotocol **a**nd **R**DF **Q**uery **L**anguage*

SPARQL a une syntaxe basée sur la définition de modèles de triplets comportant des variables qui doivent correspondre à des triplets de la base.

Inspiré des langages relationnels SQL, plusieurs antécédents SPARQL, RQL, TRIPLE, Xcerpt, SeRQL


#### SQL vs SPARQL

```sql
SELECT e.surname AS es, p.name AS pn
FROM employee e, project p
WHERE e.gender = 'male'
		AND p.administratorId = e.id
		AND e.surname LIKE 'N\%';
```

```SPARQL
PREFIX : <http://example.org/> SELECT ?sn, (?projname AS ?pn) 
WHERE {
	?e a :Employee .
	?e :surname ?sn .
	?e :gender 'male'.
	?p a :Project .
	?p :name ?pn .
	?p :administrator ?e. 
	FILTER (strstarts(?sn,'N'))
}                      
```

Obtenir les projets dont les administrateurs sont des hommes et le nom commence par la lettre `N`.


### Les spécifications SPARQL 1.1

Une spécification du W3C modularisée

- [SPARQL 1.1 Overview](http://www.w3.org/TR/sparql11-overview/)
- [SPARQL 1.1 Query Language](http://www.w3.org/TR/sparql11-query/)
- [SPARQL 1.1 Update](http://www.w3.org/TR/sparql11-update/)
- [SPARQL 1.1 Service Description](http://www.w3.org/TR/sparql11-service-description/)
- [SPARQL 1.1 Federated Query](http://www.w3.org/TR/sparql11-federated-query/)
- [SPARQL 1.1 Query Results JSON Format](http://www.w3.org/TR/sparql11-results-json/)
- [SPARQL 1.1 Query Results CSV and TSV Formats](http://www.w3.org/TR/sparql11-results-csv-tsv/)
- [SPARQL Query Results XML Format (Second Edition)](http://www.w3.org/TR/rdf-sparql-XMLres/)
- [SPARQL 1.1 Entailment Regimes](http://www.w3.org/TR/sparql11-entailment/)
- [SPARQL 1.1 Protocol](http://www.w3.org/TR/sparql11-protocol/)
- [SPARQL 1.1 Graph Store HTTP Protocol](http://www.w3.org/TR/sparql11-http-rdf-update/)


### SPARQL Query Language

[SPARQL 1.1 Query Language](http://www.w3.org/TR/sparql11-query/)

Supposant un graphe de triplet chargé dans un service SPARQL, le Langage de requêtes SPARQL permet de formuler des requêtes qui prennent la forme de **motifs de graphe** plus ou moins complexes. 

### Formats des résultats

- Extensible Markup Language ([XML](http://www.w3.org/XML/)), cf. [SPARQL Query Results XML Format (Second Edition)](http://www.w3.org/TR/rdf-sparql-XMLres/)
- JavaScript Object Notation ([JSON](https://www.ietf.org/rfc/rfc4627.txt)), cf. [SPARQL 1.1 Query Results JSON Format](http://www.w3.org/TR/sparql11-results-json/)
- Comma Separated Values ([CSV](https://www.ietf.org/rfc/rfc4180.txt)), cf. [SPARQL 1.1 Query Results CSV and TSV Formats](http://www.w3.org/TR/sparql11-results-csv-tsv/)
- Tab Separated Values ([TSV](http://www.iana.org/assignments/media-types/text/tab-separated-values)), cf. [SPARQL 1.1 Query Results CSV and TSV Formats](http://www.w3.org/TR/sparql11-results-csv-tsv/)

Supposant un graphe de triplet chargé dans un service SPARQL, le Langage de requêtes SPARQL permet de formuler des requêtes qui prennent la forme de **motifs de graphe** plus ou moins complexes. 

### Formats des résultats

Afin de pouvoir échanger les résultats dans des formats lisibles par la machine, SPARQL supporte **quatre formats d’échanges** : 

- Extensible Markup Language ([XML](http://www.w3.org/XML/)), cf. [SPARQL Query Results XML Format (Second Edition)](http://www.w3.org/TR/rdf-sparql-XMLres/)
- JavaScript Object Notation ([JSON](https://www.ietf.org/rfc/rfc4627.txt)), cf. [SPARQL 1.1 Query Results JSON Format](http://www.w3.org/TR/sparql11-results-json/)
- Comma Separated Values ([CSV](https://www.ietf.org/rfc/rfc4180.txt)), cf. [SPARQL 1.1 Query Results CSV and TSV Formats](http://www.w3.org/TR/sparql11-results-csv-tsv/)
- Tab Separated Values ([TSV](http://www.iana.org/assignments/media-types/text/tab-separated-values)), cf. [SPARQL 1.1 Query Results CSV and TSV Formats](http://www.w3.org/TR/sparql11-results-csv-tsv/)


##### Soit, le graphe de triplets suivant

```turtle
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
<http://example.org/alice#me> a foaf:Person .
<http://example.org/alice#me> foaf:name "Alice" .
<http://example.org/alice#me> foaf:mbox <mailto:alice@example.org> .
<http://example.org/alice#me> foaf:birthday "1998-05-13"^^xsd:date .
<http://example.org/alice#me> foaf:knows <http://example.org/bob#me> .
<http://example.org/bob#me> foaf:knows <http://example.org/alice#me> .
<http://example.org/bob#me> foaf:name "Bob" .
<http://example.org/bob#me> foaf:birthday "1996-12-04"^^xsd:date .
<http://example.org/bob#me> foaf:mbox <mailto:bob@example.org> .
<http://example.org/alice#me> foaf:knows <http://example.org/charlie#me> .
<http://example.org/charlie#me> foaf:knows <http://example.org/alice#me> .
<http://example.org/charlie#me> foaf:name "Charlie" .
<http://example.org/bob#me> foaf:birthday "1997-11-21"^^xsd:date .
<http://example.org/alice#me> foaf:knows <http://example.org/snoopy> .
<http://example.org/snoopy> foaf:name "Snoopy"@en .
```

cf. [SPARQL 1.1 Overview](http://www.w3.org/TR/sparql11-overview/)


##### La requête SPARQL suivante avec SELECT

```SPARQL
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?name ?email
WHERE
  {
    ?person a foaf:Person .
  }
```

--

Ramène toutes les personnes 

La requête précédente ramène les noms des personnes et leur courriel (s’il y en a).

Comme la syntaxe turtle, la syntaxe SPARQL vous permet de renseigner des préfixes. Le plus souvent avec une requête SPARQL, il vaut mieux d’abord d’abord s’intérerer à la clause WHERE car c’est elle qui décrit les triplets du dataset que nous voulons requêter. La clause WHERE fait cela avec un ou plusieurs motifs de triplets qui sont comme des triplets mais avec des variables comme comme des remplacement de l’un ou de toutes les parties du triplets.

Dans cette requête nous avons un premier motif de triplet qui sélectionne les triplets qui ont la propriété `rdf:type` avec pour objet `foaf:Person`.


<!-- .slide: data-background="/presentations/images/sparqlWhere.png" data-background-size="contain" -->

WHERE spécifie les données à tirer ; `SELECT` détermine les données qui doivent être présentées. 

(Figure dans Bob DuCharme, Learning SPARQL, O’Reilly)

@todo


##### La requête SPARQL suivante avec SELECT

```SPARQL
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?name ?email
WHERE
  {
    ?person a foaf:Person .
    ?person foaf:name ?name .
    ?person foaf:mbox ?email .
  }
```

--

Ramène les noms des personnes et leur courriel s’il y en a et qu’elles ont la propriété `foaf:name` et `foaf:mbox` renseignées.

Les autres motifs de triplets lient la variable personne avec des triplets qui ont des propriétés foaf:name et foaf:mbox. Le processeur, après avoir identifier les triplets qui correspondent au premier motif, garde en mémoire la valeur de la variable pour analyser les autres triplets.

La clause SELECT appelle deux variables qui sont le nom et l’email.

Cette requête opère une jointure entre tous les triplets qui ont un sujet correspondant, où le prédicat de type est person (`foaf:Person`), et la personne a un ou plusieurs noms (`foaf:name`) et adresses (`foaf:mbox`).


##### La requête SPARQL suivante avec SELECT

```SPARQL
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?name ?email
WHERE
  {
    ?person a foaf:Person .
    ?person foaf:name ?name .
    ?person foaf:mbox ?email .
    ?person foaf:birthday ?date .
    FILTER(?date > "1997-01-01")
  }
```

--

Ramène les noms des personnes et leur courriel (s’il y en avait) et filtre sur leur date de naissance.


##### La requête SPARQL suivante avec SELECT

```SPARQL
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?name (COUNT(?friend) AS ?count)
WHERE { 
    ?person foaf:name ?name . 
    ?person foaf:knows ?friend . 
} GROUP BY ?person ?name
```

--

ramène les noms des personnes et leur nombre d’amis

Soit le graphe de triplets RDF suivant, la requête SPARQL avec SELECT ramène les noms des personnes et leur nombre d’amis.

Exemple tiré de [SPARQL 1.1 Overview](http://www.w3.org/TR/sparql11-overview/).


### SPARQL Format des résultats

```xml
<?xml version="1.0"?>
<sparql xmlns="http://www.w3.org/2005/sparql-results#">
 <head>
   <variable name="name"/>
   <variable name="count"/>
 </head>
 <results>
   <result>
     <binding name="name">
       <literal>Alice</literal>
     </binding>
     <binding name="count">
       <literal datatype="http://www.w3.org/2001/XMLSchema#integer">3</literal>
     </binding>
   </result>
   <!-- ... autant d’élément <result> que de résultats -->
 </results>
</sparql>
```

```csv
name,count
Alice,3
Bob,1
Charlie,1
```


### Différences entre la spécification 1.0 et 1.1

- Comme dans la spécification précédente 1.0 de 2008, il est aussi possible de formuler des requêtes complexes avec union, des parties optionnelles (optional query parts) et des filtres (filters).
- La spécification 1.1 introduit l’agrégation de valeurs (*value aggregation*), les expressions de chemin  (*path expressions*), la possibilité de formuler des requêtes imbriquées (*nested queries*), etc. 
- En dehors de la clause `SELECT` - qui lie des variables - SPARQL supporte la clause `ASK` – i.e. boolean "yes/no" – et la clause `CONSTRUCT` avec laquelle de nouveaux graphes RDF peuvent être construits à partir d’un résultat de requête.

Nota : SPARQL 1.1 offre également la possibilité de faire des requêtes fédérées sur plusieurs SPARQL endpoints cf. [SPARQL 1.1 Federated Query](http://www.w3.org/TR/sparql11-federated-query/)


### SPARQL Update Language

[SPARQL 1.1 Update](http://www.w3.org/TR/sparql11-update/) (non couvert dans ce cours)

- un langage de manipulation de données complet
- opérations des mise à jour (*Update*) qui peuvent consister en plusieurs requêtes séquentielles réalisées sur une collection de graphes
- opérations possibles sur les graphes RDF dans un entrepôt
  - mise à jour
  - création
  - suppression

SPARQL est un langage de manipulation de données complet, à l’instar de SQL puisqu’il permet aussi de mettre à jour des graphes de triplets.

Les opérations de mise à jour (*Update*) peuvent consister en plusieurs requêtes séquentielles qui sont réalisées sur une collection de graphes contenue dans un entrepôt. 

Ces opérations permettent de mettre à jour, de créer et de supprimer des graphes RDF dans un entrepôt.


##### Exemple de mise à jour d’un graphe de triplets

````SPARQL
PREFIX foaf: <http://xmlns.com/foaf/0.1/> .

INSERT DATA { <http://www.example.org/alice#me> 
              foaf:knows [ foaf:name "Dorothy" ]. } ;
DELETE { ?person foaf:name ?mbox } 
WHERE { <http://www.example.org/alice#me> foaf:knows ?person .
        ?person foaf:name ?name FILTER ( lang(?name) = "EN" ) .}
````

Par exemple, la requête suivante, insère un nouvel ami d’Alice dénommée Dorothy dans le graph par défaut puis supprime tous les noms des amis d’Alice qui sont en anglais.

Comme on le voit, la seconde opération peut être dépendante du résultat d’une requête sur l’entrepôt. La syntaxe utilisée dans la clause WHERE est ici dérivée du langage de requête.


### SPARQL Protocol

[SPARQL 1.1 Protocol](http://www.w3.org/TR/sparql11-protocol/)

- définit une manière de transférer des requêtes ou opérations de mise à jour à un service SPARQL via HTTP
- définit une manière pour faire correspondre ces requêtes à des opérations HTTP GET et POST
- définit les réponses HTTP respectives de ces requêtes


#### Exemple de requête HTTP

```txt
GET /sparql/?query=PREFIX%20foaf%3A%20%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0ASELECT%20%3Fname%20%28COUNT%28%3Ffriend%29%20AS%20%3Fcount%29%0AWHERE%20%7B%20%0A%20%20%20%20%3Fperson%20foaf%3Aname%20%3Fname%20.%20%0A%20%20%20%20%3Fperson%20foaf%3Aknows%20%3Ffriend%20.%20%0A%7D%20GROUP%20BY%20%3Fperson%20%3Fname 
HTTP/1.1
Host: www.example.org
User-agent: my-sparql-client/0.1
```

Dans cet exemple, la requête SPARQL est adressé via HTTP à l’hôte `http://www.example.org/sparql/`. Conformément à la spécification, cette requête est inclue dans une requête GET où la chaîne de requête est encodée. Le protocole fournit plusieurs détails sur les opérations de requête et de mise à jour, les méthodes HTTP ainsi que les formats de réponses supportés. 

### Quelques notions relatives au protocole

- **SPARQL Protocol client** An HTTP client (as defined by [RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec1.html#sec1.3) [[RFC2616](https://www.w3.org/TR/2013/REC-sparql11-protocol-20130321/#rfc2616)]) that sends HTTP requests for SPARQL Protocol operations. (Also known as: *client*)
- **SPARQL Protocol service** An HTTP server that services HTTP requests and sends back HTTP responses for SPARQL Protocol operations. The URI at which a SPARQL Protocol service listens for requests is generally known as a SPARQL endpoint. (Also known as: *service*)
- **SPARQL endpoint** The URI at which a SPARQL Protocol service listens for requests from SPARQL Protocol clients.
- **SPARQL Protocol operation** An HTTP request and response that conform to the protocol defined in this document.
- **RDF Dataset** A collection of a default graph and zero or more named graphs, as defined by the [SPARQL 1.1 Query Language](http://www.w3.org/TR/sparql11-query/#rdfDataset).


### SPARQL endpoint

L’URI à laquelle un service au protocole SPARQL écoute les requêtes d’un client SPARQL

- https://ckan.org
- https://datahub.io
- http://sparqles.ai.wu.ac.at

### Exemples d’implémentations logicielles

- [RDF4J](http://rdf4j.org), anciennement le framework Sesame par la fondation Eclipse
- [Jena (framework)](https://jena.apache.org) par  la fondation Apache Software
- [OpenLink Virtuoso](https://virtuoso.openlinksw.com)
- cf. [List of SPARQL implementations (Wikipedia)](https://en.wikipedia.org/wiki/List_of_SPARQL_implementations)

Plusieurs logiciels sont disponibles pour exécuter créer des SPARQL endpoint, avec ou sans interface graphique (GUI).

ex. [SNORQL](https://github.com/kurtjx/SNORQL) est un client Ajax pour explorer des SPARQL endpoints.

Ex. [SPARQL Playground](http://sparql-playground.sib.swiss/) est un outil pédagogique pour apprendre l’écriture de requêtes SPARQL

## 2. Notation des requêtes SPARQL


### Syntaxe SPARQL

La syntaxe SPARQL est basée sur la définition de modèles de triplets comportant des variables qui correspondent à des triplets de la base

#### Clause de résultat (*result clause*)

`SELECT`, `WHERE`, `CONSTRUCT`, `ASK`, `DESCRIBE`

#### Modèle de graphe (*query pattern*)

Précédé par la clause `WHERE`

- requêtes basées sur la notion de **modèles de graphe**
- des **variables** (identificateurs précédés de `?` ou `$`) sont instanciées lorsqu’un triplet concorde avec le modèle

#### Modificateurs de requête (*query modifiers*)

- Pour limiter, ordonner ou réarranger les résulats


### Structure d’une requête SPARQL

```SPARQL
# prefix declarations
PREFIX foo: <http://example.com/resources/>
...
# dataset definition
FROM ...
# result clause
SELECT ...
# query pattern
WHERE {
    ...
}
# query modifiers
ORDER BY ...
```

Dans l’ordre, une requête SPARQL se compose des éléments (optionnels) suivants :

- Les **déclarations de préfixes** (*prefix declarations*), pour l’abbréviation des IRIs
- La **définition de jeu de données** (*dataset definition*), déclare le ou les graphes RDF requêtés
- Une **clause de résultats** (*result clause*), identifie quelle information retourner pour la requête
- Le **modèle de graphe** (*query pattern*), sépcifie ce qui doit être requêté dans le jeu de données
- Les **modificateurs de requêtes ou de résultats** (*query/solution modifiers*), pour limiter, sélectionner une partie des résultats, les ordonner ou les réarranger

(https://www.w3.org/2009/Talks/0615-qbe/)


### Clause de résulat (result clause)

- #### **SELECT** – retourne une table liée (similaire à SQL)

- #### **ASK** – retourne vrai ou faux selon l’existence d’un *pattern* donné dans le graphe RDF

- #### **CONSTRUCT** – retourne un graphe RDF construit à partir des tables liées

- #### **DESCRIBE** – retourne un graphe RDF décrivant une ressource donnée

### Clause de résulat ou type de requête

Une requête débute par une clause qui peut comporter l’un des verbes suivants

- `SELECT *vars* WHERE *modèle*` qui retourne la liste des valeurs des variables pour lesquelles il existait des triplets dans la base qui concordaient avec le modèle de graphe.
- `CONSTRUCT *modèle1* WHERE *modèle2*` où les variables des deux modèles sont liées. Cette requête retourne une structure RDF qui regroupe les triplets de *modèle1* avec les valeurs des variables qui sont liées à des valeurs pour lesquelles il existait des triplets dans la base qui concordaient avec le *modèle2*.
- `ASK *modèle*` retourne `true` s’il existe au moins un triplet qui concorde avec le modèle et `false` sinon.
- `DESCRIBE` permet de *décrire* un ressource ou une variable mais cette description est laissée au soin de l’implantation.


### Modèle de graphe

Les requêtes sont basées sur la notion de **modèle de graphe** qu’on cherche à retrouver dans une base de triplets. Dans un modèle de graphe, un triplet peut comporter des variables (i.e. des identificateurs précédés par `?` ou `$`) qui seront instanciées lorsqu’un triplet concorde au modèle en affectant une variable.

Un modèle de graphe est une suite de triplets entre accolades `{ }`. Une variable liée dans un triplet garde la même valeur dans tous les autres triplets où elle est utilisée dans le même modèle de graphe. Il est de plus possible d’ajouter des contraintes supplémentaires sur les triplets par un *filtre* qui peut apparaître entre des triplets dans un modèle de graphe. Par exemple, le modèle de graphe `{?s ex:p "o". ?s ex:p "o1"}` liera la variable `?s` à tous les sujets de la base de triplets qui ont comme prédicat `ex:p` et objet `"o"` et `"o1"`.

Comme on peut utiliser les notations abrégées de triplets, ce modèle de graphe aurait aussi pu s’écrire `{?s ex:p "o", "o1"}`.

### Modèle de graphe

SPARQL a une syntaxe basée sur la définition de modèles de triplets comportant des variables qui correspondent à des triplets de la base

- Les requêtes sont basées sur la notion de modèle de graphe qu’on cherchera à retrouver dans une base de triplets. 
- Dans un modèle de graphe, un triplet peut comporter des variables (i.e. des identificateurs précédés par `?` ou `$`) qui seront instanciées lorsqu’un triplet concorde au modèle en affectant une variable.


### Exemple de modèle de graphe

```SPARQL
PREFIX purl:
```

@todo


### Notation des variables et des modèles

- URI ou Littéral `?var ?une_autre_var $v`
- Nœuds vides `_:id []`

#### Patrons de triplets

- Match complet 	`ex:machin ex:numero "45692"`
- Match avec une variable 	`?machin ?ex:numero "?valeur`
- Match complet 	`ex:truc ?propriete ?valeur`


### Autres fonctionnalités

- `ORDER BY`, `LIMIT`, `OFFSET` 

  pour limiter l’ensemble résultat comme dans SQL

- `FROM`, `FROM NAMED` 

  employés pour spécifier des graphes par défaut ou des graphes nommés pour la requête

- `SELECT DISTINCT` 

  retire les doublons du résultat

- `VALUES` 

  variables prédéfinie spécifiant liant dans la forme tabulaire


### Modificateurs

- `ORDER BY *variables*`
- `DISTINCT`

Les triplets étant considérés comme un ensemble, il n’est pas possible de se fier à l’ordre d’apparition des résultats. Néanmoins, on peut modifier l’ordre de la sortie avec les mots-clefs suivants :

- `ORDER BY *variables*` à la fin de la requête, trie les solutions en ordre croissant des variables; pour l’ordre décroissant, on indique `DESC(*variable*)`. On peut trier les solutions sur plusieurs clés.
- `DISTINCT` à placer immédiatement après le *verbe* (i.e. le premier terme) d’une requête pour garantir que chaque solution n’apparaîtra qu’une fois.

### Autres possibilités

SPARQL 1.1 fournit également des fonctions d’agrégation telles des sommes ou des moyennes et la possibilité de définir des variables. 

Nous ne décrivons ici que les principaux éléments de la syntaxe SPARQL. Il est également possible d’interroger plusieurs graphes ou faire des requêtes fédérées. Pour la syntaxe complète, il convient de se référer à [la documentation du W3C](http://www.w3.org/TR/sparql11-query/).


### Modèles de graphe (*graph patterns*)

- #### **conjonction** (séquence de motifs de graphes)

- #### **disjonction** (UNION pattern), équivalent de l’opérateur booléen OU

- #### **négation** (FILTER NOT EXISTS, MINUS)

- #### **conjonction conditionnelle** (OPTIONAL)


### Graph Pattern (GP)

```SPARQL
# Basic Graph Pattern (BGP)
?x :p ?y .
?y :s _:a .
```

```SPARQL
# Group Graph Pattern (GGP)
{ ?x :p ?y . }
{ ?y :s _=a . }
```

```SPARQL
# Alternative Graph Pattern (AGP)
{ ?x :p1 ?y . }
UNION
{ ?x :p2 ?y . }	
```

```SPARQL
# Optional Graph Pattern (OGP)
?x :p ?y .
OPTIONAL { ?y :s _:a }
```

```SPARQL
# Patterns on Named Graph
```


### Filtres

Syntaxe : `FILTER(boolean condition)`

La clause filtre les résultats de BGP, il peut être placé n’importe où dans un BGP.

`FILTER *expression*` où `*expression*` est composée d’une combinaison des éléments suivants :

- **conversion** entre une chaîne et un type XML en appelant une fonction du nom du type `xsd:integer` ou `xsd:dateTime` sur une chaîne, une variable ou une expression
- une expression arithmétique ou logique entre parenthèses; cette expression utilise les opérateurs infixes *habituels*
- un appel à une fonction prédéfinie, p. ex. `isIRi(?x)`, `isBLANK(?x)` ou `REGEX(*string*,*pattern*)`.

Un filtre s’applique au modèle de graphe entier où il se trouve, peu importe sa position dans le graphe.

Fonctions de chaînes : strlen, contains, substr, concat, regex, replace

Fonction de terme RDF : isIRI, IRI, isBlank, BNODE

BGP : Basic Graph Pattern


### Exemple de filtres

```SPARQL
PREFIX dc: <http://purl.org/dc/elements/1.1/> 
SELECT ?title
WHERE { 
	?x dc:title ?title .
	?x dc:author ?author
	FILTER regex(?title, ".SPARQL") 
}
```

```SPARQL
PREFIX : <http://example.org/> 
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#> 
SELECT ?s ?l
WHERE {
	?s :invented ?i .
	?i rdfs:label ?l
	FILTER ( regex(?l,"ˆ.ul.*") && contains(str(?s),"Cimr") )
}
```

La clause `FILTER` utilise une condition booléenne pour filtrer les résultats non recherchés.

On peut associer deux expressions booléennes dans une parenthèse avec l’opérateur `&&`.

Il existe plusieurs fonctions et opérateurs de filtres prédéfinies

- *logique :* `!`, `&&`, `||`
- *arithmétique :* `+`, `-`, `*`, `/`
- *comparaison :* `=`, `!=`, `>`, `<`, ...
- *SPARQL tests:* `isURI`, `isBlank`, `isLiteral`, `bound`
- *SPARQL accessors:* `str`, `lang`, `datatype`
- *autres :* `sameTerm`, `langMatches`, `regex`


### Optional

Syntaxe : GP1 OPTIONAL { GP2 }

Les résultats de GP1 sont augmentés optionnellement avec les résultats de GP2, s’il y en a.

```SPARQL
PREFIX : <http://example.org/> 
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#> 
SELECT ?s ?i ?l
WHERE {
	?s :invented ?i . 
	OPTIONAL {
		?i rdfs:label ?l FILTER (lang(?l)="en") . 
	} 
	OPTIONAL {
		?i rdfs:label ?l FILTER (lang(?l)="fr")
	}
}
```

`OPTIONAL` essaye de faire correspondre le graph à un autre motif optionnellement. Si un motif optionnel échoue, les variables restent non liées avec cette solution.

L’ordre des OPTIONALs peut parfois être important.

Tous les triplets s’électionnés peuvent ne pas avoir d’étiquette dans chacune des langues.


### Alternatives

```SPARQL
PREFIX dcmi: <http://purl.org/dc/dcmitype/>
SELECT ?doc
WHERE { 
	{ ?doc a dcmi:Dataset . }
  UNION
	{ ?doc a dcmi:Image . }
}
```

 `UNION` forme une disjonction de deux motifs de graphe. Les solutions des deux côté de l’UNION sont incluent dans les résultats.


### Négation

Deux constructions MINUS vs. FILTER NOT EXISTS

````SPARQL
PREFIX : <http://example.org/> 
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#
SELECT ?s1 ?i
{ ?s1 :invented ?i.
  MINUS {
   ?s2 :invented ?i .
   FILTER(?s1 != ?s2) . 
   }
}
````

```SPARQL
SELECT ?s1 ?i 
{ ?s1 :invented ?i.
  FILTER NOT EXISTS {
   ?s2 :invented ?i .
   FILTER(?s1 != ?s2). 
   }
}
```

Dans le premier cas la variable ?s1 n’est pas liée dans le motif MINUS, retourne tous les inventeurs.

Dans le second cas, retourne toutes les inventions qui furent inventées par seulement un inventeur.


Find me members of the  Senate Armed Service committee’s Strategic Forces subcommittee who do  not also serve on the Personnel subcommittee.

```SPARQL
PREFIX foaf:  <http://xmlns.com/foaf/0.1/>
SELECT ?name 
WHERE {
  # find members in the Strategic Forces subcommittee
  <http://www.rdfabout.com/rdf/usgov/congress/committees/SenateArmedServices/StrategicForces> 
    foaf:member ?member .
  OPTIONAL {
    # find out if this same member is in the Personnel 
    # subcommittee - but call him/her something different 
    # (?member2)
    <http://www.rdfabout.com/rdf/usgov/congress/committees/SenateArmedServices/Personnel> 
      foaf:member ?member2 .
    FILTER (?member2 = ?member) .
  }
  # keep only those rows that failed to find a ?member2 
  # (member of Personnel subcommittee)
  FILTER (!bound(?member2)) .
  ?member foaf:name ?name .
}
```

- Together, `OPTIONAL` and the `!bound(...)` filter allow us to query for things that are *not* asserted in the RDF dataset.
- A similar technique allows for various types of universally quantified queries. (E.g. min or max value of a predicate.) See [this frequently asked question](http://thefigtrees.net/lee/sw/sparql-faq#universal).

Try it with [the GovTrack-specific SPARQL endpoint](http://www.govtrack.us/sparql.xpd). ([Expected results.](https://www.w3.org/2009/Talks/0615-qbe/#q13r))

https://www.w3.org/2009/Talks/0615-qbe/


### Agrégations

- `COUNT(?var)`, ou `COUNT(DISTINCT ?var)`

  compte le nombre ou les occurence (distinctes) de `?var` dans l’ensemble résultat

- `MIN(?v)`, `MAX(?v)`, `SUM(?v)`, `AVG(?v)` 

  analogues à leur équivalents SQL

- `GROUP CONCAT(?var; separator = <SEP>) AS ?group)`

  concatène tous les elements dans le groupe avec le caractère séparateur donné

- `SAMPLE` 

  prend une représentant arbitraire dans le groupe

Usage of (?expr as ?var) alias is obligatory.

Similarly to SQL, SPARQL allows computing aggregates over particular
data groups and filter in them using GROUP BY/HAVING construct


### Exemple d’agrégation

```SPARQL
PREFIX : <http://example.org/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
SELECT ?i COUNT(?s) AS ?count
FROM :inventors 
WHERE {
	?s :invented ?i. 
}
GROUP BY ?i
```


### Exemple d’agrégation

```SPARQL
PREFIX : <http://example.org/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
SELECT (COUNT(?s) AS ?count) ?i (GROUP_CONCAT(?s;separator=",") AS
	?inventors) 
FROM :inventors 
WHERE {
	?s :invented ?i. 
}
GROUP BY ?i
HAVING (COUNT(?s) > 1)
```

(expr AS ?v) assignent de variable où expr est une expression et ?v la nouvelle variable créée


## TP Écriture de requêtes SPARQL

Utilisation de http://yasgui.triply.cc/

http://epimorphics.github.io/qonsole

Utilisation dans [Twinkle](http://www.iro.umontreal.ca/~lapalme/ift6281/Twinkle.html) ?

Aide-Mémoire http://www.iro.umontreal.ca/~lapalme/ift6282/SparqlRappels.html


### SPARQL par l’exemple 

(dans **YASGUI** sur http://data.persee.fr/sparql)

- Explorer l’ensemble des contenus
- Chercher les noms, prénoms et auteurs de tous les auteurs
- Supprimer les doublons
- Limiter aux 20 premiers résultats
- Trier par ordre alphabétique
- Chercher Bernard Lepetit
- Lister tous les triplets dont cet auteur est l’objet
- Lister ses publications
- compter par type, etc. group by

Aide-mémoire par Guy Lapalme http://www.iro.umontreal.ca/~lapalme/ift6282/SparqlRappels.html


Explorer l’ensemble des contenus avec la requête

http://data.persee.fr/sparql

```SPARQL
SELECT * 
WHERE { ?subject ?predicate ?object }
LIMIT 100
```

```SPARQL
SELECT DISTINCT ?objet
WHERE {
  ?sujet a ?objet .
}
LIMIT 100
```

### Lister les classes

Très souvent, quand on aborde un SPARQL endpoint, il peut être utile de visualiser les classes

```SPARQL
SELECT DISTINCT ?Concept 
WHERE {
  [] a ?Concept.
}
LIMIT 100
```

Exemple https://isidore.science/sqe



### Chercher les noms et prénoms de tous les auteurs

```SPARQL
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?surname ?forename ?author
WHERE {
  ?doc marcrel:aut ?author .
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
}
```



### Ajouter un concat

```SPARQL
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?surname ?forename ?author
WHERE {
  ?doc marcrel:aut ?author .
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
}
```

@todo



### Supprimer les doublons

```SPARQL
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?surname ?forename DISTINCT ?author
WHERE {
  ?doc marcrel:aut ?author .
  ?author foaf:familyName ?surname .
  ?autor foaf:givenName ?forename .
}
```



### Limiter aux 20 premiers résultats

```SPARQL
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?surname ?forename ?author
WHERE {
  ?doc marcrel:aut ?author .
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
}
LIMIT 20
```



### Trier par ordre alphabétique

```SPARQL
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT DISTINCT ?surname ?forename ?author
WHERE {
  ?doc marcrel:aut ?author .
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
}
ORDER BY ?surname
LIMIT 100
```



### Tous les triplets dont ces auteurs sont l’objet

```SPARQL
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT * { 
  ?s ?p <http://data.persee.fr/authority/393571#Person> .
}
```



### Lister les documents avec des sujets en Français

```SPARQL
PREFIX bibo: <http://purl.org/ontology/bibo/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT DISTINCT ?doc ?titre ?sujet
WHERE {
  ?doc ?prop bibo:Document .
  ?doc dcterms:title ?titre .
  ?doc dcterms:subject ?sujet .
  FILTER (lang(?sujet) = "" || langMatches(lang(?sujet), "fr"))
} 
LIMIT 300
```



### Chercher l’auteur Bernard Lepetit

```SPARQL
PREFIX bibo: <http://purl.org/ontology/bibo/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?surname ?forename ?author
WHERE {
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
  FILTER ( REGEX(str(?surname), "Lepetit") && REGEX(str(?forename), "Bernard"))
}
```

| 1    | Lepetit | Bernard | <http://data.persee.fr/authority/275626#Person> |
| ---- | ------- | ------- | ----------------------------------------------- |
| 2    | Lepetit | Bernard | <http://data.persee.fr/authority/393571#Person> |



### xxx

```SPARQL
PREFIX bibo: <http://purl.org/ontology/bibo/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX persee: <http://data.persee.fr/ontology/persee_ontology/>
SELECT ?doc ?titre ?sujet
WHERE {
  ?doc a bibo:Document .
  ?doc dcterms:title ?titre .
  ?doc marcrel:aut ?author .
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
  OPTIONAL { ?doc dcterms:subject ?sujet }
  FILTER ( REGEX(str(?surname), "Lepetit") && REGEX(str(?forename), "Bernard"))
}
GROUP BY ?doc
LIMIT 100
```



### Lister les publications de Bernard Lepetit

```SPARQL
PREFIX bibo: <http://purl.org/ontology/bibo/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT ?author ?id { 
  ?doc dcterms:identifier ?id .
  ?doc marcrel:aut ?author .
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
  FILTER ( REGEX(str(?surname), "Lepetit") && REGEX(str(?forename), "Bernard"))
}
```



### Tous les documents qui ont pour auteur “Lepetit”, listés par date d’édition décroissante

```SPARQL
PREFIX bibo: <http://purl.org/ontology/bibo/>
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX purl: <http://purl.org/dc/terms/>
PREFIX rdam: <http://rdaregistry.info/Elements/m/>
PREFIX persee: <http://data.persee.fr/ontology/persee-ontology/>
PREFIX dcterms: <http://purl.org/dc/terms/>
SELECT ?author ?doc ?title ?date 
WHERE { 
  ?doc a bibo:Document .
  ?doc marcrel:aut ?author .
  ?doc dcterms:title ?title .
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
  OPTIONAL {?doc persee:dateOfPrintPublication ?date}
  FILTER ( REGEX(str(?surname), "Lepetit") && REGEX(str(?forename), "Bernard"))
}
ORDER BY $date
```



### Avant 1990

```SPARQL
PREFIX bibo: <http://purl.org/ontology/bibo/>
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX rdam: <http://rdaregistry.info/Elements/m/>
PREFIX persee: <http://data.persee.fr/ontology/persee-ontology/>
PREFIX dcterms: <http://purl.org/dc/terms/>
SELECT ?author ?doc ?title ?date { 
  ?doc a dcterms:Document .
  ?doc marcrel:aut ?author .
  ?doc dcterms:title ?title .
  ?author foaf:familyName ?surname .
  ?author foaf:givenName ?forename .
  OPTIONAL {?doc persee:dateOfPrintPublication ?date}
  FILTER ( REGEX(str(?surname), "Lepetit") && REGEX(str(?forename), "Bernard") )
  FILTER ( str(?dateOfPrintPublication_70) <= "1990" )
}
ORDER BY $date
```



### Celles entre 1970 et 1980 (nb chercher date dans le schema)

```SPARQL
PREFIX purl: <http://purl.org/net/schemas/space/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
SELECT *
{ ?launch purl:launched ?date
  FILTER (
    ?date > "1968-10-1"^^xsd:date &&
    ?date < "1968-10-30"^^xsd:date
  )
}
```



@todo revoir ex

@todo limiter quantité de résultats

```SPARQL
SELECT ?manifestation 
WHERE { ?manifestation a <http://rdaregistry.info/Elements/c/Manifestation> }
```



### Quid des deux auteurs ?

```SPARQL

```

@todo



### Les co-auteurs de Bernard Lepetit

```SPARQL
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
SELECT DISTINCT ?auteur ?nom
WHERE { ?auteur a foaf:Person .
        ?auteur foaf:name ?nom .
        FILTER ( !( ?nom = "Bernard Lepetit" ) )
        ?doc marcrel:aut ?auteur .
        ?doc marcrel:aut ?coauteur .
        ?coauteur foaf:name ?nom1 .
        FILTER ( ?nom1 = "Bernard Lepetit" ) }
LIMIT 200
```



### Le nombre de co-auteurs de Bernard Lepetit

```SPARQL
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX marcrel: <http://id.loc.gov/vocabulary/relators/>
SELECT DISTINCT (COUNT(DISTINCT ?auteur) AS ?nb)
WHERE { ?auteur a foaf:Person .
        ?auteur foaf:name ?nom .
        FILTER ( !( ?nom = "Bernard Lepetit" ) )
        ?doc marcrel:aut ?auteur .
        ?doc marcrel:aut ?coauteur .
        ?coauteur foaf:name ?nom1 .
        FILTER ( ?nom1 = "Bernard Lepetit" ) }
LIMIT 200
```



### Divers (obsolète)

#### Exemples Bristish Museum

```SPARQL
SELECT * 
WHERE { :Lyndal_Roper ?b ?c }
```

Identifier une URI comme valeur de , et chercher à visualiser tous les objets qui partagent le même objet

```SPARQL
SELECT * WHERE {
	?historian_name ?predicate <http://dbpedia.org/class/yago/Historian110177150>
}
```

Combiner avec une autre propriété

```
SELECT ?name
WHERE {
	?name ?b <http://dbpedia.org/class/yago/WikicatBritishHistorians> .
	?name ?b <http://dbpedia.org/class/yago/WikicatWomenHistorians>
}
```

```SPARQL
{ ?object ecrm:P108i_was_produced_by ?production .
  ?production ecrm:P9_consists_of ?date_node .
FILTER(?date >= "1580-01-01"^^xsd:date &&
         ?date <= "1600-01-01"^^xsd:date) }
```

```SPARQL
SELECT ?auteur ?name
WHERE { ?auteur a <> .
	?auteur foaf:name ?name .
	FILTER regex(?name, '^Paul') .}
```

```SPARQL
SELECT ?auteur ?name 
WHERE { ?auteur a <> ;
	foaf:name ?name .}
ORDER BY ?name LIMIT 20
```

```SPARQL
PREFIX bmo: <http://www.researchspace.org/ontology/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX ecrm: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT ?type (COUNT(?type) as ?n)
WHERE {
  # We still need to indicate the ?object_type variable,
  # however we will not require it to match "print" this time

  ?object bmo:PX_object_type ?object_type .
  ?object_type skos:prefLabel ?type .

  # Once again, we will also filter by date
  ?object ecrm:P108i_was_produced_by ?production .
  ?production ecrm:P9_consists_of ?date_node .
  ?date_node ecrm:P4_has_time-span ?timespan .
  ?timespan ecrm:P82a_begin_of_the_begin ?date .
  FILTER(?date >= "1580-01-01"^^xsd:date &&
         ?date <= "1600-01-01"^^xsd:date)
}
# The GROUP BY command designates the variable to tally by,
# and the ORDER BY DESC() command sorts the results by
# descending number.
GROUP BY ?type
ORDER BY DESC(?n)
```


### Cours en ligne 

- SPARQL in 11 minutes https://youtu.be/FvGndkpa4K0
- https://www.fun-mooc.fr/courses/course-v1:inria+41002+self-paced/about
- https://open.hpi.de/courses/semanticweb2015
- https://www.emse.fr/~zimmermann/Teaching/SemWeb/
- https://rubenverborgh.github.io/WebFundamentals/
- http://rali.iro.umontreal.ca/lapalme/ift6282/
- https://www.futurelearn.com/courses/linked-data
- https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/Building_a_query/Museums_on_Instagram


### Interfaces

- http://yasgui.org/
- http://doc.yasgui.org
- http://jena.apache.org
- http://fr.dbpedia.org/sparqlEditor/index.html
- https://allegrograph.com/products/gruff/


### Biblio

- DuCharme Bob. *Learning SPARQL: Querying and Updating with SPARQL 1.1.* 2e éd. O’Reilly, 2013. ISBN-10: 1449371434
- Allemang, Dean, James A Hendler, et Fabien Gandon. 2020. *Semantic web for the working ontologist: effective modeling for linked data, RDFS, and OWL*.
- Doerr, Martin. 2009. Ontologies for Cultural Heritage. *Handbook on Ontologies.* p. 463-486. DOI : 10.1007/978-3-540-92673-3
- Gandon, Fabien. 2012. Le web sémantique: comment lier les données et les schémas sur le web. Paris : Dunod. InfoPro. Management des systèmes d’information. ISBN 9782100572946.
- Hitzler, Pascal, Markus Krötzsch, Sebastian Rudolph. 2009. *Foundations of Semantic Web Technologies.* CRC Press. ISBN-10: 142009050X
- Yu, Liyang. 2014. *A Developer’s Guide to the Semantic Web.* 2e éd. Springer. ISBN-10: 3662437953.
- Van Holland Seth, Ruben Verborgh. 2014. *Linked Data for Libraries, Archives and Museums, How to clean, link and publish your metadata.* Facet publishing. ISBN 9781783300389
