Cypher queries to gather various aspects of GlyGen graph:

### List all node labels and their counts
```cypher
CALL apoc.meta.stats()
YIELD labels
RETURN labels;
```
{
  "Journal_Citation": 154929,
  "_GraphConfig": 1,
  "Polymorphism_Annotation": 1060,
  "Cross-link_Annotation": 16598,
  "molecule_part_tRNA%20variable%20arm": 2,
  "Domain_Annotation": 18430,
  "Reaction_Annotation": 11256,
  "Motif_Annotation": 13943,
  "molecule_part_tRNA%20acceptor%20arm": 2,
  "Sequence_Conflict_Annotation": 107430,
  "Propeptide_Annotation": 3540,
  "Glycan_Motif": 121,
  "Subunit_Annotation": 59259,
  "molecule_substrate": 4282,
  "Glycosequence": 172999,
  "Saccharide": 53384,
  "Initiator_Methionine_Annotation": 6292,
  "Protein": 355144,
  "Interaction": 102340,
  "Disease_Annotation": 8210,
  "Gene_Locus": 186830,
  "Peptide_Annotation": 1608,
  "Glycosyltransferase_Reaction": 227,
  "molecule_part_mRNA%20cap": 14,
  "Beta_Strand_Annotation": 151210,
  "Intramembrane_Annotation": 1299,
  "Participant": 25276,
  "Lipidation_Annotation": 4273,
  "Helix_Annotation": 149513,
  "Sequence_Caution_Annotation": 2509,
  "Simple_Sequence": 391467,
  "Disulfide_Bond_Annotation": 86068,
  "Disruption_Phenotype_Annotation": 9934,
  "Site_Annotation": 11111,
  "Class": 24442,
  "Function_Annotation": 98531,
  "Binding_Site_Annotation": 165989,
  "Taxon": 368,
  "Activity_Regulation_Annotation": 5696,
  "Domain_Extent_Annotation": 395586,
  "Cellular_Component": 329,
  "Subcellular_Location_Annotation": 157991,
  "Database": 136,
  "Active_Site_Annotation": 29759,
  "Tissue": 2777,
  "PTM_Annotation": 25483,
  "Structured_Name": 519153,
  "ExactPosition": 2966526,
  "Catalytic_Activity": 139166,
  "Catalytic_Activity_Annotation": 97383,
  "Region": 5607833,
  "Nucleotide_Binding_Annotation": 5967,
  "Turn_Annotation": 38387,
  "Translated_Sequence": 444227,
  "Glycosylation_Annotation": 61621,
  "Enzyme": 2403,
  "Chain_Annotation": 111965,
  "CHEBI": 51487,
  "Modified_Residue_Annotation": 156088,
  "Part": 5485,
  "Resource": 24116804,
  "Disease": 6540,
  "Gene": 342674,
  "Signal_Peptide_Annotation": 42686,
  "Self_Interaction": 1932,
  "Concept": 890,
  "molecule_part_tRNA%20discriminator%20base": 3,
  "Transcript_Resource": 444203,
  "Natural_Variant_Annotation": 91416,
  "Structure_Resource": 88055,
  "Cofactor_Annotation": 25628,
  "Alternative_Sequence_Annotation": 47495,
  "Mutagenesis_Annotation": 57002,
  "molecule_part_matrix%20attachment%20region%20(MAR)%20of%20DNA": 2,
  "Mass_Spectrometry_Annotation": 502,
  "Non_Self_Interaction": 100408
}

### List all relationship types and their counts
```cypher
CALL apoc.meta.stats()
YIELD relTypesCount
RETURN relTypesCount;
```
{
  "sameAs": 25277,
  "geneRange": 186830,
  "has_image": 53384,
  "cofactor": 27209,
  "type": 19165095,
  "existence": 355144,
  "related": 41250,
  "locatedIn": 256354,
  "annotation": 2668835,
  "has_glycosequence": 172999,
  "enzyme": 60589,
  "exactMatch": 154909,
  "closeMatch": 8953,
  "component": 4488,
  "catalyzedReaction": 128506,
  "catalyzedPhysiologicalActivity": 39196,
  "submittedName": 208518,
  "reactionDatabase": 11256,
  "translatedTo": 444227,
  "citation": 1019983,
  "chainSequenceMapping": 167994,
  "host": 5,
  "replaces": 682,
  "transcriptRange": 458136,
  "cellularComponent": 255287,
  "exonRange": 3194402,
  "has_motif": 85549,
  "interaction": 195620,
  "ensTranscript": 448271,
  "organism": 380157,
  "glycan_database": 246114,
  "participant": 202748,
  "seeAlso": 10617504,
  "attached_by": 1507,
  "enzymeClass": 48422,
  "is_from_source": 63532,
  "attribution": 4610326,
  "subClassOf": 58195,
  "range": 1839430,
  "has_parent": 268,
  "evidence": 1793185,
  "has_taxon": 63532,
  "synthesized_by": 695885,
  "disease": 6993,
  "alternativeName": 136114,
  "in_carbohydrate_format": 172999,
  "domain": 997,
  "conflictingSequence": 109939,
  "has_enzyme_protein": 454,
  "activity": 2979,
  "end": 5607833,
  "recommendedName": 174546,
  "has_canonical_residue": 153756,
  "replacedBy": 20,
  "isolatedFrom": 173381,
  "catalyticActivity": 97383,
  "ligand": 165989,
  "hasLocus": 471205,
  "ligandPart": 3027,
  "database": 4778376,
  "begin": 5607833,
  "source": 805775,
  "sequence": 583269,
  "method": 88541,
  "classifiedWith": 6107180,
  "encodedBy": 342674
}

### Retrieve detailed properties of a specific node
```cypher
MATCH (n:Simple_Sequence {uri: 'http://purl.uniprot.org/isoforms/A0A1P8B3Z7-1'})
RETURN n;
```
{
  "identity": 345,
  "labels": [
    "Resource",
    "Simple_Sequence"
  ],
  "properties": {
    "md5Checksum": "3327343528bc2af86482ea3650b46b1a",
    "mass": 21171,
    "modified": "2017-04-12",
    "reviewed": false,
    "canonical": false,
    "version": 1,
    "value": "MAAKPGAATPTYSPKIVGRSRLPIFKDSDLDWSRPDGRGFHQCRPALLQTGAVSSASGSAYAEFGNTKVIVSVFGPRESKKAMVYSDVGRLNCNVSYTNFASPTLGQGTDHKEYSSMLHKALEGVIMMETFPKTTVDVFALVLESGGSDLSVLISCASLALADAGIMMYDLITAVSVVCVCYNSCIDSSALSLMFISIK",
    "uri": "http://purl.uniprot.org/isoforms/A0A1P8B3Z7-1"
  },
  "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:345"
}


### Sample nodes with specific labels and their relationships
```cypher
MATCH (n:Protein)-[r]-(m)
RETURN n, r, m
LIMIT 3;
```
[
  {
    "keys": [
      "n",
      "r",
      "m"
    ],
    "length": 3,
    "_fields": [
      {
        "identity": {
          "low": 132,
          "high": 0
        },
        "labels": [
          "Resource",
          "Protein"
        ],
        "properties": {
          "created": {
            "year": {
              "low": 2011,
              "high": 0
            },
            "month": {
              "low": 6,
              "high": 0
            },
            "day": {
              "low": 28,
              "high": 0
            }
          },
          "modified": {
            "year": {
              "low": 2024,
              "high": 0
            },
            "month": {
              "low": 5,
              "high": 0
            },
            "day": {
              "low": 29,
              "high": 0
            }
          },
          "mnemonic": "Y5371_ARATH",
          "reviewed": true,
          "uri": "http://purl.uniprot.org/uniprot/Q8W4S5",
          "version": {
            "low": 157,
            "high": 0
          }
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:132"
      },
      {
        "identity": {
          "low": 8394,
          "high": 0
        },
        "start": {
          "low": 132,
          "high": 0
        },
        "end": {
          "low": 1243,
          "high": 0
        },
        "type": "classifiedWith",
        "properties": {},
        "elementId": "5:5fd508ae-451d-4956-b6c4-17ded2eda554:8394",
        "startNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:132",
        "endNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:1243"
      },
      {
        "identity": {
          "low": 1243,
          "high": 0
        },
        "labels": [
          "Resource",
          "Concept"
        ],
        "properties": {
          "prefLabel": "Leucine-rich repeat",
          "altLabel": "LRR",
          "uri": "http://purl.uniprot.org/keywords/433"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:1243"
      }
    ],
    "_fieldLookup": {
      "n": 0,
      "r": 1,
      "m": 2
    }
  },
  {
    "keys": [
      "n",
      "r",
      "m"
    ],
    "length": 3,
    "_fields": [
      {
        "identity": {
          "low": 132,
          "high": 0
        },
        "labels": [
          "Resource",
          "Protein"
        ],
        "properties": {
          "created": {
            "year": {
              "low": 2011,
              "high": 0
            },
            "month": {
              "low": 6,
              "high": 0
            },
            "day": {
              "low": 28,
              "high": 0
            }
          },
          "modified": {
            "year": {
              "low": 2024,
              "high": 0
            },
            "month": {
              "low": 5,
              "high": 0
            },
            "day": {
              "low": 29,
              "high": 0
            }
          },
          "mnemonic": "Y5371_ARATH",
          "reviewed": true,
          "uri": "http://purl.uniprot.org/uniprot/Q8W4S5",
          "version": {
            "low": 157,
            "high": 0
          }
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:132"
      },
      {
        "identity": {
          "low": 15245,
          "high": 0
        },
        "start": {
          "low": 132,
          "high": 0
        },
        "end": {
          "low": 17512,
          "high": 0
        },
        "type": "classifiedWith",
        "properties": {},
        "elementId": "5:5fd508ae-451d-4956-b6c4-17ded2eda554:15245",
        "startNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:132",
        "endNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:17512"
      },
      {
        "identity": {
          "low": 17512,
          "high": 0
        },
        "labels": [
          "Resource"
        ],
        "properties": {
          "uri": "http://purl.uniprot.org/uniprot/#_kb.Q8W4S5_up.classifiedWith_obo.GO_0005886"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:17512"
      }
    ],
    "_fieldLookup": {
      "n": 0,
      "r": 1,
      "m": 2
    }
  },
  {
    "keys": [
      "n",
      "r",
      "m"
    ],
    "length": 3,
    "_fields": [
      {
        "identity": {
          "low": 132,
          "high": 0
        },
        "labels": [
          "Resource",
          "Protein"
        ],
        "properties": {
          "created": {
            "year": {
              "low": 2011,
              "high": 0
            },
            "month": {
              "low": 6,
              "high": 0
            },
            "day": {
              "low": 28,
              "high": 0
            }
          },
          "modified": {
            "year": {
              "low": 2024,
              "high": 0
            },
            "month": {
              "low": 5,
              "high": 0
            },
            "day": {
              "low": 29,
              "high": 0
            }
          },
          "mnemonic": "Y5371_ARATH",
          "reviewed": true,
          "uri": "http://purl.uniprot.org/uniprot/Q8W4S5",
          "version": {
            "low": 157,
            "high": 0
          }
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:132"
      },
      {
        "identity": {
          "low": 6862,
          "high": 0
        },
        "start": {
          "low": 132,
          "high": 0
        },
        "end": {
          "low": 6950,
          "high": 0
        },
        "type": "classifiedWith",
        "properties": {},
        "elementId": "5:5fd508ae-451d-4956-b6c4-17ded2eda554:6862",
        "startNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:132",
        "endNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:6950"
      },
      {
        "identity": {
          "low": 6950,
          "high": 0
        },
        "labels": [
          "Resource",
          "Concept"
        ],
        "properties": {
          "prefLabel": "Repeat",
          "uri": "http://purl.uniprot.org/keywords/677"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:6950"
      }
    ],
    "_fieldLookup": {
      "n": 0,
      "r": 1,
      "m": 2
    }
  }
]

### 7. Retrieve nodes with a specific property
```cypher
MATCH (n:ExactPosition)
RETURN n
LIMIT 3;
```
	
[
  {
    "keys": [
      "n"
    ],
    "length": 1,
    "_fields": [
      {
        "identity": {
          "low": 1250117,
          "high": 0
        },
        "labels": [
          "Resource",
          "ExactPosition"
        ],
        "properties": {
          "position": {
            "low": 3431764,
            "high": 0
          },
          "uri": "http://purl.uniprot.org/position/57dcef819ca248e08569080d57b773cf"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:1250117"
      }
    ],
    "_fieldLookup": {
      "n": 0
    }
  },
  {
    "keys": [
      "n"
    ],
    "length": 1,
    "_fields": [
      {
        "identity": {
          "low": 1250120,
          "high": 0
        },
        "labels": [
          "Resource",
          "ExactPosition"
        ],
        "properties": {
          "position": {
            "low": 3479066,
            "high": 0
          },
          "uri": "http://purl.uniprot.org/position/2f7f98e3da544137bb3c48207346b8fb"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:1250120"
      }
    ],
    "_fieldLookup": {
      "n": 0
    }
  },
  {
    "keys": [
      "n"
    ],
    "length": 1,
    "_fields": [
      {
        "identity": {
          "low": 1250121,
          "high": 0
        },
        "labels": [
          "Resource",
          "ExactPosition"
        ],
        "properties": {
          "position": {
            "low": 2573818,
            "high": 0
          },
          "uri": "http://purl.uniprot.org/position/f0a4d8f654774e40afd147336bb2ea42"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:1250121"
      }
    ],
    "_fieldLookup": {
      "n": 0
    }
  }
]



### Retrieve nodes and relationships based on a specific relationship type
```cypher
[
  {
    "keys": [
      "n",
      "r",
      "m"
    ],
    "length": 3,
    "_fields": [
      {
        "identity": {
          "low": 5366,
          "high": 0
        },
        "labels": [
          "Resource",
          "Protein"
        ],
        "properties": {
          "created": {
            "year": {
              "low": 2009,
              "high": 0
            },
            "month": {
              "low": 11,
              "high": 0
            },
            "day": {
              "low": 3,
              "high": 0
            }
          },
          "modified": {
            "year": {
              "low": 2024,
              "high": 0
            },
            "month": {
              "low": 5,
              "high": 0
            },
            "day": {
              "low": 29,
              "high": 0
            }
          },
          "mnemonic": "RPK1_ARATH",
          "reviewed": true,
          "uri": "http://purl.uniprot.org/uniprot/Q9ZRF9",
          "version": {
            "low": 170,
            "high": 0
          }
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:5366"
      },
      {
        "identity": {
          "low": 4,
          "high": 0
        },
        "start": {
          "low": 5366,
          "high": 0
        },
        "end": {
          "low": 8839,
          "high": 0
        },
        "type": "annotation",
        "properties": {},
        "elementId": "5:5fd508ae-451d-4956-b6c4-17ded2eda554:4",
        "startNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:5366",
        "endNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:8839"
      },
      {
        "identity": {
          "low": 8839,
          "high": 0
        },
        "labels": [
          "Resource",
          "Modified_Residue_Annotation"
        ],
        "properties": {
          "comment": "Phosphothreonine",
          "uri": "http://purl.uniprot.org/uniprot/Q9ZRF9#SIP95D953628819581B"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:8839"
      }
    ],
    "_fieldLookup": {
      "n": 0,
      "r": 1,
      "m": 2
    }
  },
  {
    "keys": [
      "n",
      "r",
      "m"
    ],
    "length": 3,
    "_fields": [
      {
        "identity": {
          "low": 3473,
          "high": 0
        },
        "labels": [
          "Resource",
          "Protein"
        ],
        "properties": {
          "created": {
            "year": {
              "low": 2013,
              "high": 0
            },
            "month": {
              "low": 5,
              "high": 0
            },
            "day": {
              "low": 1,
              "high": 0
            }
          },
          "modified": {
            "year": {
              "low": 2024,
              "high": 0
            },
            "month": {
              "low": 5,
              "high": 0
            },
            "day": {
              "low": 29,
              "high": 0
            }
          },
          "mnemonic": "TWIH_ARATH",
          "reviewed": true,
          "uri": "http://purl.uniprot.org/uniprot/B5X582",
          "version": {
            "low": 108,
            "high": 0
          }
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:3473"
      },
      {
        "identity": {
          "low": 15,
          "high": 0
        },
        "start": {
          "low": 3473,
          "high": 0
        },
        "end": {
          "low": 9216,
          "high": 0
        },
        "type": "annotation",
        "properties": {},
        "elementId": "5:5fd508ae-451d-4956-b6c4-17ded2eda554:15",
        "startNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:3473",
        "endNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:9216"
      },
      {
        "identity": {
          "low": 9216,
          "high": 0
        },
        "labels": [
          "Resource",
          "Binding_Site_Annotation"
        ],
        "properties": {
          "uri": "http://purl.uniprot.org/uniprot/B5X582#SIP549A528DFFBBFA1F"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:9216"
      }
    ],
    "_fieldLookup": {
      "n": 0,
      "r": 1,
      "m": 2
    }
  },
  {
    "keys": [
      "n",
      "r",
      "m"
    ],
    "length": 3,
    "_fields": [
      {
        "identity": {
          "low": 3601,
          "high": 0
        },
        "labels": [
          "Resource",
          "Protein"
        ],
        "properties": {
          "created": {
            "year": {
              "low": 2007,
              "high": 0
            },
            "month": {
              "low": 11,
              "high": 0
            },
            "day": {
              "low": 13,
              "high": 0
            }
          },
          "modified": {
            "year": {
              "low": 2024,
              "high": 0
            },
            "month": {
              "low": 5,
              "high": 0
            },
            "day": {
              "low": 29,
              "high": 0
            }
          },
          "mnemonic": "BIK1_ARATH",
          "reviewed": true,
          "uri": "http://purl.uniprot.org/uniprot/O48814",
          "version": {
            "low": 173,
            "high": 0
          }
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:3601"
      },
      {
        "identity": {
          "low": 27,
          "high": 0
        },
        "start": {
          "low": 3601,
          "high": 0
        },
        "end": {
          "low": 15691,
          "high": 0
        },
        "type": "annotation",
        "properties": {},
        "elementId": "5:5fd508ae-451d-4956-b6c4-17ded2eda554:27",
        "startNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:3601",
        "endNodeElementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:15691"
      },
      {
        "identity": {
          "low": 15691,
          "high": 0
        },
        "labels": [
          "Resource",
          "Modified_Residue_Annotation"
        ],
        "properties": {
          "comment": "Phosphoserine",
          "uri": "http://purl.uniprot.org/uniprot/O48814#SIP6B05989B54191F65"
        },
        "elementId": "4:5fd508ae-451d-4956-b6c4-17ded2eda554:15691"
      }
    ],
    "_fieldLookup": {
      "n": 0,
      "r": 1,
      "m": 2
    }
  }
]
```

### List All Properties
```cypher
CALL apoc.meta.schema() YIELD value AS schema
UNWIND keys(schema) AS label
UNWIND keys(schema[label].properties) AS property
RETURN label, property
```
label	property
"Structure_Resource"	"uri"
"Structure_Resource"	"resolution"
"Peptide_Annotation"	"uri"
"Peptide_Annotation"	"comment"
"Intramembrane_Annotation"	"uri"
"Intramembrane_Annotation"	"comment"
"Journal_Citation"	"date"
"Journal_Citation"	"volume"
"Journal_Citation"	"identifier"
"Journal_Citation"	"pages"
"Journal_Citation"	"author"
"Journal_Citation"	"name"
"Journal_Citation"	"title"
"Journal_Citation"	"uri"
"Gene"	"orfName"
"Gene"	"altLabel"
"Gene"	"uri"
"Gene"	"prefLabel"
"CHEBI"	"uri"
"CHEBI"	"label"
"Database"	"category"
"Database"	"abbreviation"
"Database"	"uri"
"Database"	"urlTemplate"
"molecule_substrate"	"uri"
"Mutagenesis_Annotation"	"comment"
"Mutagenesis_Annotation"	"substitution"
"Mutagenesis_Annotation"	"uri"
"Cofactor_Annotation"	"uri"
"Cofactor_Annotation"	"comment"
"Disulfide_Bond_Annotation"	"uri"
"Disulfide_Bond_Annotation"	"comment"
"Nucleotide_Binding_Annotation"	"uri"
"Nucleotide_Binding_Annotation"	"comment"
"Sequence_Conflict_Annotation"	"uri"
"Sequence_Conflict_Annotation"	"substitution"
"Activity_Regulation_Annotation"	"uri"
"Activity_Regulation_Annotation"	"comment"
"molecule_part_tRNA%20acceptor%20arm"	"uri"
"Cellular_Component"	"comment"
"Cellular_Component"	"altLabel"
"Cellular_Component"	"uri"
"Cellular_Component"	"prefLabel"
"Participant"	"mnemonic"
"Participant"	"label"
"Participant"	"uri"
"Alternative_Sequence_Annotation"	"comment"
"Alternative_Sequence_Annotation"	"substitution"
"Alternative_Sequence_Annotation"	"uri"
"Part"	"uri"
"Catalytic_Activity_Annotation"	"uri"
"molecule_part_tRNA%20variable%20arm"	"uri"
"Non_Self_Interaction"	"uri"
"Non_Self_Interaction"	"xeno"
"Non_Self_Interaction"	"experiments"
"Turn_Annotation"	"uri"
"ExactPosition"	"uri"
"ExactPosition"	"position"
"PTM_Annotation"	"uri"
"PTM_Annotation"	"comment"
"Gene_Locus"	"reverseStrand"
"Gene_Locus"	"uri"
"Gene_Locus"	"chromosome"
"Propeptide_Annotation"	"uri"
"Propeptide_Annotation"	"comment"
"Active_Site_Annotation"	"uri"
"Active_Site_Annotation"	"comment"
"Tissue"	"uri"
"Tissue"	"label"
"Natural_Variant_Annotation"	"comment"
"Natural_Variant_Annotation"	"substitution"
"Natural_Variant_Annotation"	"uri"
"Subunit_Annotation"	"uri"
"Subunit_Annotation"	"comment"
"Binding_Site_Annotation"	"uri"
"Binding_Site_Annotation"	"comment"
"Enzyme"	"obsolete"
"Enzyme"	"altLabel"
"Enzyme"	"uri"
"Enzyme"	"prefLabel"
"Taxon"	"commonName"
"Taxon"	"scientificName"
"Taxon"	"uri"
"Simple_Sequence"	"md5Checksum"
"Simple_Sequence"	"fragment"
"Simple_Sequence"	"mass"
"Simple_Sequence"	"name"
"Simple_Sequence"	"precursor"
"Simple_Sequence"	"modified"
"Simple_Sequence"	"reviewed"
"Simple_Sequence"	"canonical"
"Simple_Sequence"	"version"
"Simple_Sequence"	"value"
"Simple_Sequence"	"uri"
"Domain_Annotation"	"uri"
"Domain_Annotation"	"comment"
"Subcellular_Location_Annotation"	"uri"
"Subcellular_Location_Annotation"	"comment"
"Disease_Annotation"	"uri"
"Disease_Annotation"	"comment"
"Reaction_Annotation"	"uri"
"Reaction_Annotation"	"equation"
"Polymorphism_Annotation"	"uri"
"Polymorphism_Annotation"	"comment"
"Catalytic_Activity"	"uri"
"Catalytic_Activity"	"label"
"Self_Interaction"	"uri"
"Self_Interaction"	"xeno"
"Self_Interaction"	"experiments"
"Disease"	"mnemonic"
"Disease"	"comment"
"Disease"	"altLabel"
"Disease"	"uri"
"Disease"	"prefLabel"
"Cross-link_Annotation"	"uri"
"Cross-link_Annotation"	"comment"
"Concept"	"altLabel"
"Concept"	"uri"
"Concept"	"prefLabel"
"Domain_Extent_Annotation"	"uri"
"Domain_Extent_Annotation"	"comment"
"Interaction"	"uri"
"Interaction"	"xeno"
"Interaction"	"experiments"
"Resource"	"date"
"Resource"	"substitution"
"Resource"	"mass"
"Resource"	"experiments"
"Resource"	"altLabel"
"Resource"	"goClassification"
"Resource"	"reverseStrand"
"Resource"	"title"
"Resource"	"resolution"
"Resource"	"md5Checksum"
"Resource"	"orfName"
"Resource"	"pages"
"Resource"	"xeno"
"Resource"	"modified"
"Resource"	"mnemonic"
"Resource"	"reviewed"
"Resource"	"value"
"Resource"	"identifier"
"Resource"	"chain"
"Resource"	"created"
"Resource"	"author"
"Resource"	"chromosome"
"Resource"	"prefLabel"
"Resource"	"equation"
"Resource"	"fullName"
"Resource"	"canonical"
"Resource"	"label"
"Resource"	"uri"
"Resource"	"version"
"Resource"	"volume"
"Resource"	"fragment"
"Resource"	"ecName"
"Resource"	"name"
"Resource"	"comment"
"Resource"	"position"
"Resource"	"shortName"
"Protein"	"created"
"Protein"	"modified"
"Protein"	"mnemonic"
"Protein"	"reviewed"
"Protein"	"uri"
"Protein"	"version"
"Signal_Peptide_Annotation"	"uri"
"Site_Annotation"	"uri"
"Site_Annotation"	"comment"
"molecule_part_matrix%20attachment%20region%20(MAR)%20of%20DNA"	"uri"
"Region"	"uri"
"Class"	"goClassification"
"Class"	"label"
"Class"	"uri"
"Translated_Sequence"	"uri"
"Translated_Sequence"	"value"
"Chain_Annotation"	"uri"
"Chain_Annotation"	"comment"
"Transcript_Resource"	"reverseStrand"
"Transcript_Resource"	"uri"
"Transcript_Resource"	"value"
"Transcript_Resource"	"chromosome"
"Function_Annotation"	"uri"
"Function_Annotation"	"comment"
"Glycosylation_Annotation"	"uri"
"Glycosylation_Annotation"	"comment"
"molecule_part_mRNA%20cap"	"uri"
"Modified_Residue_Annotation"	"uri"
"Modified_Residue_Annotation"	"comment"
"Mass_Spectrometry_Annotation"	"comment"
"Mass_Spectrometry_Annotation"	"measuredError"
"Mass_Spectrometry_Annotation"	"uri"
"Mass_Spectrometry_Annotation"	"measuredValue"
"molecule_part_tRNA%20discriminator%20base"	"uri"
"Beta_Strand_Annotation"	"uri"
"Sequence_Caution_Annotation"	"uri"
"Sequence_Caution_Annotation"	"comment"
"Structured_Name"	"ecName"
"Structured_Name"	"fullName"
"Structured_Name"	"shortName"
"Structured_Name"	"uri"
"Disruption_Phenotype_Annotation"	"uri"
"Disruption_Phenotype_Annotation"	"comment"
"Initiator_Methionine_Annotation"	"uri"
"Initiator_Methionine_Annotation"	"comment"
"Lipidation_Annotation"	"uri"
"Lipidation_Annotation"	"comment"
"Motif_Annotation"	"uri"
"Motif_Annotation"	"comment"
"Helix_Annotation"	"uri"
