### 1. Protein enzymes involved in the biosynthesis of glycan G24994OK in mouse [Check Data]

*SPARQL:*
```sparql
SELECT DISTINCT ?protein_uri ?protein_name  
WHERE {
   <http://glygen.org/glycan/G24994OK> glycan:synthesized_by ?rxn . ?rxn gly:has_enzyme_protein ?protein_uri . ?protein_uri up:organism <http://purl.uniprot.org/taxonomy/10090> . optional { ?protein_uri up:recommendedName ?recnameuri . ?recnameuri up:fullName ?protein_name . }
} LIMIT 10000 OFFSET 0
```

*Cypher:*
```cypher
MATCH (glycan:Resource {uri: 'http://glygen.org/glycan/G24994OK'})-[:classifiedWith]->(rxn:Reaction_Annotation)-[:enzyme]->(protein:Protein)-[:organism]->(organism:Taxon {uri: 'http://purl.uniprot.org/taxonomy/10090'})
OPTIONAL MATCH (protein)-[:recommendedName]->(recname:Structured_Name)-[:annotation]->(name:Simple_Sequence)
RETURN DISTINCT protein.uri AS protein_uri, name.value AS protein_name
LIMIT 10000
```

---

### 2. Glycans synthesized by enzyme protein P42867 [SPARQL: 12,901, Cypher: 12,902]

*SPARQL:*
```sparql
SELECT DISTINCT ?glycan_uri  
WHERE {
?glycan_uri glycan:synthesized_by ?rxn . ?rxn gly:has_enzyme_protein <http://purl.uniprot.org/uniprot/P42867> . 
} LIMIT 10000 OFFSET 0
```
*Cypher:*
```cypher
MATCH (glycan:Resource)-[]->(rxn)-[]->(protein:Protein {uri: 'http://purl.uniprot.org/uniprot/P42867'})
RETURN DISTINCT glycan.uri AS glycan_uri
LIMIT 10000
```

---

### 3. Gene locus for enzymes involved in the biosynthesis of glycan G24994OK in mouse [SPARQL: 8, Cypher: 15]

Reason of difference: Some of data are not loaded, thus filtering is not same

*SPARQL:*
```sparql
SELECT DISTINCT ?gene_name ?gene_locus  
WHERE {
   <http://glygen.org/glycan/G24994OK> glycan:synthesized_by ?rxn . ?rxn gly:has_enzyme_protein ?protein_uri .  ?protein_uri up:encodedBy ?gene_uri . ?gene_uri skos:prefLabel ?gene_name . ?gene_uri gly:hasLocus ?gene_locus . ?protein_uri up:organism <http://purl.uniprot.org/taxonomy/10090> .
} LIMIT 10000 OFFSET 0
```

*Cypher:*
```cypher
MATCH (glycan:Resource {uri: 'http://glygen.org/glycan/G24994OK'})-[]->(rxn)-[]->(protein:Protein)-[:encodedBy]->(gene:Gene)-[]->(o:Gene_Locus)
RETURN DISTINCT gene.prefLabel, o.uri
LIMIT 10000
```
---

### 4. Glycoproteins shown to bear G17689DH and which site is this glycan attached to

*SPARQL:*
```sparql
SELECT DISTINCT ?glycoprotein_id  ?pos ?amino_acid
WHERE {
   ?glycoprotein_id gco:glycosylated_at ?site . ?site faldo:location ?loc . ?loc faldo:position ?pos . ?loc glycan:has_amino_acid ?amino_acid . ?site gco:has_saccharide <http://glygen.org/glycan/G17689DH> . 
} LIMIT 10000 OFFSET 0
```

*Cypher:*
```cypher
MATCH (glycoprotein:Protein)-[:glycosylated_at]->(site)-[:location]->(loc)
MATCH (loc)-[:position]->(pos)-[:has_amino_acid]->(amino_acid)
MATCH (site)-[:has_saccharide]->(:Resource {uri: 'http://glygen.org/glycan/G17689DH'})
RETURN DISTINCT glycoprotein.uri AS glycoprotein_id, pos.value AS pos, amino_acid.value AS amino_acid
LIMIT 10000
```
---

### 5. Glycoproteins reported in mouse [SPARQL: 21709, Cypher: 21717]

*SPARQL:*
```sparql
SELECT DISTINCT ?isoform_uri 
WHERE { 
      ?glycoprotein_uri up:sequence ?isoform_uri . ?protein_uri up:sequence ?isoform_uri .  ?protein_uri up:organism <http://purl.uniprot.org/taxonomy/10090> . ?isoform_uri gly:canonical "true"^^<http://www.w3.org/2001/XMLSchema#boolean> . 
}  LIMIT 10000 OFFSET 0
```

*Cypher:*
```cypher
MATCH (glycoprotein:Protein)-[:sequence]->(isoform:Simple_Sequence)
MATCH (protein:Protein)-[:sequence]->(isoform)
MATCH (protein)-[:organism]->(organism:Taxon {uri: 'http://purl.uniprot.org/taxonomy/10090'})
WHERE isoform.canonical = true
RETURN DISTINCT isoform.uri AS isoform_uri
LIMIT 10000
```
---

### 6. Protein functions for protein P14210

*SPARQL:*
```sparql
SELECT DISTINCT "P14210" ?protein_function 
WHERE {
   <http://purl.uniprot.org/uniprot/P14210> up:annotation ?annuri . ?annuri rdfs:comment ?protein_function . ?annuri rdf:type up:Function_Annotation .
} LIMIT 10000 OFFSET 0
```

*Cypher:*
```cypher
MATCH (protein:Protein {uri: 'http://purl.uniprot.org/uniprot/P14210'})-[:annotation]->(ann:Function_Annotation)-[:comment]->(protein_function:Structured_Name)
RETURN DISTINCT 'P14210' AS protein_uri, protein_function.value AS protein_function
LIMIT 10000
```
---

### 7. Sites with glycosylation, phosphorylation and SNV [Check Data]

*SPARQL:*
```sparql
SELECT DISTINCT ?isoform ?start_pos ?end_pos 
WHERE {
 ?isoform gly:has_site ?site . 
 ?site faldo:begin ?begin . 
 ?site gly:glycosite ?glycosite . 
 ?site gly:phosphosite ?phosphosite . 
 ?site gly:snvsite ?snvsite . 
 ?begin faldo:position ?start_pos . 
 ?site faldo:end ?end . 
 ?end faldo:position ?end_pos . 
} LIMIT 10000 OFFSET 0
```

*Cypher:*
```cypher
MATCH (isoform:Simple_Sequence)-[:has_site]->(site)
MATCH (site)-[:begin]->(begin)
MATCH (site)-[:glycosite]->(glycosite)
MATCH (site)-[:phosphosite]->(phosphosite)
MATCH (site)-[:snvsite]->(snvsite)
MATCH (begin)-[:position]->(start_pos)
MATCH (site)-[:end]->(end)
MATCH (end)-[:position]->(end_pos)
RETURN DISTINCT isoform.uri AS isoform, start_pos.value AS start_pos, end_pos.value AS end_pos
LIMIT 10000
```
