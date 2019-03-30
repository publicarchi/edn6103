## Comment récupérer la photo d’un auteur sur Wikipédia à partir d’un ISBN en 4 étapes ?

**Partons d’un cas concret**

**L’ISBN du nouveau roman de Marc Villard est 9782072748578.**

La première étape  va consiter à récupèrer l’ISNI via le SRU.

A voir aussi  Vous pouvez avec cet ISBN récupérer toute la veille sur ce titre publiée sur Bibliosurf II en format JSON-LDhttps://www.bibliosurf.com/?page=api&isbn=9782072748578 



**1. Récupérer l’ISNI via le SRU**

**Il convient d’utiliser la requête web suivante qui contient l’ISBNhttp://catalogue.bnf.fr/api/SRU?version=1.2&operation=searchRetrieve&query=bib.ean%20all%20%229782072748578%22 Vous obtenez du beau UNIMARC encapsulé dans du XML.Il vous suffira de récupérer la valeur du code 0 du tag 700.Deuxième étape. On récupère ensuite l’identifiant VIAF en interrogeant cette fois-ci data-bnf avec une requête SPARQL.**

**2. Récupérer l’identifiant VIAF sur data-bnf**

**La requête SPARQL avec l’ISNI est**

```
SELECT ?viaf
WHERE {?skosPersonne isni:identifierValid "0000000121417815". 
  ?skosPersonne skos:exactMatch ?viaf. 
FILTER contains (str(?viaf), "viaf")} 
```

**et on obtient un petit fichier JSON contenant la valeur attendue**

```
{ "head": { "link": [], "vars": ["viaf"] },  "results": { "distinct": false, "ordered": true, "bindings": [    { "viaf": { "type": "uri", "value": "http://viaf.org/viaf/84491481/" }} ] } }
```

**3. Récupérer le lien Wikipédia avec l’identifiant VIAF**

**en interrogeant le justlinks.json de VIAF.https://viaf.org/viaf/84491481/justlinks.json** 

```
{ "viafID":"84491481",
    "B2Q":["0000103580"],
    "BIBSYS":["90624947"],
    "BNE":["XX1135144"],
    "BNF":["http://catalogue.bnf.fr/ark:/12148/cb11928368n"],
     ....
    "SUDOC":["027185931"],
    "SWNL":["vtls008460868"],
    "WKP":["Q3288470"],
    "Wikipedia":["https://fr.wikipedia.org/wiki/Marc_Villard"]}
```

**4. Récupérer la photo de Marc Villard en interrogeant l’API de Wikipédia**

**avec ce lien https://fr.wikipedia.org/w/api.php?action=opensearch&search=Marc_Villard&format=xml** 

**Ca vous a plu ? Alors récupérez l’url du site de Marc Villard cette fois sur WIKIDATA en ayant au préalable récupéré l’identifiant de cette base sur data.bnf.**



cf. https://docs.google.com/presentation/d/1_L8PEqvpY5RCR2ufrSgv5g-8-AZV83eMh-D9uJWjh04/edit#slide=id.g3645650e10_0_25