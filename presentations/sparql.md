## EDN6103 - Web sémantique pour l'édition numérique

# SPARQL
Emmanuel Château-Dutier et Antoine Fauchié, mars 2021

Site web pour les ressources du cours :  
[https://publicarchi.github.io/edn6103/](https://publicarchi.github.io/edn6103/)

===↓===

# Sommaire

## 1. Le protocole et le langage de requête SPARQL

## 2. Notation SPARQL

???

===→===

# 1. Le protocole et le langage de requête SPARQL

???



===↓===

## La pile des technologies du web sémantique

![](images/sw_layercake.png)

===↓===

## Rappels sur la notation Turtle

#### Notation des IRI (rappels)

[Internationalized Resource Identifiers](https://tools.ietf.org/html/rfc3987) (IRIs)

- Les IRI sont encadrées par des chevrons ouvrants et fermants

  `<http://monIri.ca/ontologie#concept>`

#### Notation des triplets (rappels)

Un triplet est noté par trois URI suivis par un point. Ils désignent respectivement le sujet, le prédicat et l’objet RDF. 

`<sujet> <prédicat> <objet> .`

`ex:s ex:p ex:q .`

L’objet peut aussi être un littéral 

`ex:s ex:p "o" .`

???

## Rappels sur la notation Turtle

Un triplets regroupe trois composantes, séparées par un espace pour éviter les ambiguïtés

===→===

## Définitions de préfixes (rappels)

Un préfixe pour un URI est défini par

`PREFIX *ident*: *IRI* .`

Exemple :

```rdf
PREFIX ex: <http://publicarchitectura/exemple#> .
```

Ce préfixe est utilisé à une déclaration pour former l’URI complet. Ainsi `ex:toto` désignera l’URI <http://publicarchitectura/exemple#toto>`. L’identificateur de préfixe peut être vide.

===→===

### Raccourcis

Lorsqu’un **sujet est partagé par plusieurs triplets** successifs, les paires prédicat et objet sont séparées par un point-virgule

`ex:s ex:p1 "o1" ; ex:p2 "o2" .`

```rdf
ex:s ex:p1 "o1" . 
ex:s ex:p2 "o2" .
```

Lorsqu’un **sujet et un prédicat sont communs** à plusieurs déclarations, ces dernières sont séparées par des virgules

`ex:s ex:p ex:o , "o1".`

```rdf
ex:s ex:p ex:o. 
ex:s ex:p "o1".
```

???

**Attention** ! dans ce contexte, les parenthèses sont utilisées pour dénoter des collections

===→===

## Notation des nœuds anonymes

Plusieurs notations possibles :

-  `[ ]`
-  `_:`

La notation avec crochets permet de combiner des triplets avec les raccourcis `,` et `;`

| `[ex:p "o"] .`             | `_:b1 ex:p "o" .`                    |
| -------------------------- | ------------------------------------ |
| `[ex:p "o"] ex:q ex:o2 .`  | `_:b2 ex:p "o". _b2 ex:q ex:o2 .`    |
| `ex:s ex:p [ex:p1 ex:o]. ` | `ex:s ex:p _:b3 . _:b3 ex:p1 ex:o .` |
| `[ex:p ex:o; ex:p1 "o1"].` | `_:b4 ex:p ex:o . _:b4 ex:p1 "o1" .` |

===→===

## Constantes et littéraux

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

===→===



# 2. Notation SPARQL

===↓===

## Discussion

### **Quelles opportunités pour le domaine éditorial ?**

--

- Quelles conséquences sur le format livre ?

--

- Quelles sources de données pourraient être utiles ?

--

- Quels types d’applications possibles ?

===↓===

## Biblio

- DuCharme Bob. *Learning SPARQL: Querying and Updating with SPARQL 1.1.* 2e éd. O’Reilly, 2013. ISBN-10: 1449371434

===↓===

- ## Biblio

  - Allemang, Dean, James A Hendler, et Fabien Gandon. 2020. *Semantic web for the working ontologist: effective modeling for linked data, RDFS, and OWL*.
  - Doerr, Martin. 2009. Ontologies for Cultural Heritage. *Handbook on Ontologies.* p. 463-486. DOI : 10.1007/978-3-540-92673-3
  - Gandon, Fabien. 2012. Le web sémantique: comment lier les données et les schémas sur le web. Paris : Dunod. InfoPro. Management des systèmes d’information. ISBN 9782100572946.
  - Hitzler, Pascal, Markus Krötzsch, Sebastian Rudolph. 2009. *Foundations of Semantic Web Technologies.* CRC Press. ISBN-10: 142009050X
  - Yu, Liyang. 2014. *A Developer’s Guide to the Semantic Web.* 2e éd. Springer. ISBN-10: 3662437953.
  - Van Holland Seth, Ruben Verborgh. 2014. *Linked Data for Libraries, Archives and Museums, How to clean, link and publish your metadata.* Facet publishing. ISBN 9781783300389

===↓===

## Lectures muséo

- Juanals, Brigitte et Jean-Luc Minel. « La construction d’un espace patrimonial partagé dans le Web de données ouvert. » Communication vol. 34 n° 1. doi :10.4000/communication.6650. <https://communication.revues.org/6650>
- Szekely, Pedro, Craig A. Knoblock, Fengyu Yang, Eleanor E. Fink, Shubham Gupta, Rachel Allen, et Georgina Goodlander. Publishing the Data of the Smithsonian American Art Museum to the Linked Data Cloud. International Journal of Humanities and Arts Computing.vol. 8 n° supplement, 2014. 152-166. <https://doi.org/10.3366/ijhac.2014.0104>

===↓===

## WTF sur Tweeter

- Antoine Isaac (Europeana, Europe) @antoine_isaac
- Patrick Murray-John @patrick_mj
- Antoine Courtin @seeksanusername
- Josée Plamondon @joplam
- ICOM.CIDOC @icomCIDOC
