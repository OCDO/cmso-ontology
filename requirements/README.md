CQ1: What are the space groups of all structures with 4 atoms?
```
PREFIX cmso: <https://purls.helmholtz-metadaten.de/cmso/>
SELECT DISTINCT ?symbol
WHERE {
    ?sample cmso:hasNumberOfAtoms ?number .
    ?sample cmso:hasMaterial ?material .
    ?material cmso:hasStructure ?structure .
    ?structure cmso:hasSpaceGroupSymbol ?symbol .
FILTER (?number="4"^^xsd:integer)
}
```

CQ2: List all computational samples with 'bcc' or 'fcc' crystal structure.
```
PREFIX cmso: <https://purls.helmholtz-metadaten.de/cmso/> 
PREFIX pldo: <https://purls.helmholtz-metadaten.de/pldo/> 
PREFIX podo: <https://purls.helmholtz-metadaten.de/podo/> 
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
SELECT DISTINCT ?sample 
WHERE {     
    ?sample cmso:hasMaterial ?material .     
    ?material cmso:hasStructure ?crystalstructure .     
    ?crystalstructure cmso:hasAltName ?crystalstructurealtname . 
FILTER (?crystalstructurealtname="bcc"^^xsd:string || ?crystalstructurealtname="fcc"^^xsd:string) 
}
```

CQ3: List all simulation cells with volume equal to 30 (ANGSTROM3).
```
PREFIX cmso: <https://purls.helmholtz-metadaten.de/cmso/> 
PREFIX pldo: <https://purls.helmholtz-metadaten.de/pldo/> 
PREFIX podo: <https://purls.helmholtz-metadaten.de/podo/> 
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
SELECT DISTINCT ?sample 
WHERE {     
    ?sample cmso:hasSimulationCell ?simulationcell .     
    ?simulationcell cmso:hasVolume ?volume . 
FILTER (?volume >= "10.0"^^xsd:float && ?volume <= "30.0"^^xsd:float) 
}
```

CQ4: List all computational samples with a supercell containing two atoms.
```
PREFIX cmso: <https://purls.helmholtz-metadaten.de/cmso/> 
PREFIX pldo: <https://purls.helmholtz-metadaten.de/pldo/> 
PREFIX podo: <https://purls.helmholtz-metadaten.de/podo/> 
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
SELECT DISTINCT ?sample 
WHERE {
    ?sample cmso:hasNumberOfAtoms ?numberofatoms . 
FILTER (?numberofatoms="2"^^xsd:integer) 
}
```
