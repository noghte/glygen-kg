# GlyGen Knowledge Graph

Built by triples available at https://sparql.glygen.org/

## Improting in Neo4j: Steps

- In Neo4j Desktop, add a local DBMS (verion `5.14`)
- Click on three dots beside the DBMS name, open folder, plugins.
- Copy the `plugins/neosemantics-5.14.0.jar` from this repo to the plugin folder.
- Start the DMBS.
- Create a database (e.g., `glygenkg`).


- Open the DBMS and run: 
```cypher
CREATE CONSTRAINT n10s_unique_uri FOR (r:Resource) REQUIRE r.uri IS UNIQUE
```
- Run the following command to initialize the graph in Neo4j. Pay attention to the `handleVocabUris` and `handleMultival` parameters. [More info](https://neo4j.com/labs/neosemantics/5.14/reference/):
        ```cypher
        CALL n10s.graphconfig.init({
        handleVocabUris: 'IGNORE', 
        handleMultival: 'OVERWRITE',
        multivalPropList: [''], //provide a list of properties that are arrays (full uris)
        handleRDFTypes: 'LABELS_AND_NODES',
        keepLangTag: false
            })
        ```
- For each N-Triple file (i.e., files having `.nt` extension) run:
    `CALL n10s.rdf.import.fetch("file:///home/saber/workspace/glygen/triples/file-name.nt", "N-Triples");` 




### Postprocessing

By running `CALL db.labels();` yoglu will see many labels like `CHEBI_{number}`. To rename those to `CHEBI` but keeping the number as a property:

First, match the nodes with labels starting with "CHEBI_", extract the trailing number, and store it in the "label" property:
```cypher
MATCH (n)
WHERE ANY(label IN labels(n) WHERE label STARTS WITH 'CHEBI_')
WITH n, [label IN labels(n) WHERE label STARTS WITH 'CHEBI_'] AS chebiLabels
UNWIND chebiLabels AS chebiLabel
SET n.label = substring(chebiLabel, 6)
```

Next, remove the old "CHEBI_" labels and set the new "CHEBI" label:
```cypher
MATCH (n)
WHERE ANY(label IN labels(n) WHERE label STARTS WITH 'CHEBI_')
WITH n, [label IN labels(n) WHERE label STARTS WITH 'CHEBI_'] AS chebiLabels
UNWIND chebiLabels AS chebiLabel
CALL apoc.create.removeLabels(n, [chebiLabel]) YIELD node
SET n:CHEBI
```