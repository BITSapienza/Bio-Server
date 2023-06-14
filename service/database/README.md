# Collections
These rapresent the structures of the database collections. This "database" folder package retrieve all data from database.

Base collections:

- `nucleotide_data`			contains the data obtainable by searching in the Nucleotide NCBI database.
- `taxonomy_data`			contains the data obtainable by searching in the Taxonomy NCBI database.
- `protein_data`			contains the data obtainable by searching in the Nucleotide Protein database.
- `sra`						contains the data obtainable by searching in the SRA NCBI database.

Collections made for performance reason:
  
- `taxonomy_tree`         	contains the childrens for every taxonomy term, used in Vulgaris Platform's Taxonomy View.
- `table_basic`           	contains a lightweight version of the data, used in Vulgaris Platform's Search view.
- `table_complete`        	contains a more complete version of the data, used in Vulgaris Platform's Organism View.

## `taxonomy_data`

Example of an element from taxonomy_data:
```json
{
	"TaxID"			: "string",
	"ScientificName"	: "string",
	"ParentTaxID"		: "string",
	"Rank"			: "string",
	"Divisio"		: "string",
	"GeneticCode":{
		"GCID"		: "string",
		"GCName"	: "string"
	},
	"MitoGeneticCode":{
		"MGCID"		: "string",
		"MGCName"	: "string"
	},
	"Lineage"	: "string",
	"LineageEx": [
		{
			"TaxID"			: "string",
			"ScientificName"	: "string",
			"Rank"			: "string",
		},
	]
	"CreateDate"	: "string",
	"UpdateDate"	: "string",
	"PubDate"	: "string"
}
```

## `nucleotide_data`

Example of an element from nucleotide_data:
```json
{
	"GBSeqAccessionVersion": "string",
	"GBSeqComment"         : "string",
	"GBSeqCreateDate"      : "string",
	"GBSeqDefinition"      : "string",
	"GBSeqDivision"        : "string",
	"GBSeqFeatureTable"    : [
		{
		    "GBFeatureIntervals": {
			"GBIntervalAccession": "string",
			"GBIntervalFrom"     : "string",
			"GBIntervalTo"       : "string"
		    },
		    "GBFeatureKey"     : "string",
		    "GBFeatureLocation": "string",
		    "GBFeatureQuals": [
			{
			    "GBQualifierName" : "string",
			    "GBQualifierValue": "string"
			}
		    ],
		    "GBFeaturePartial3": "string",
		    "GBFeaturePartial5": "string"
		}
	],
	"GBSeqLength"          : "string",
	"GBSeqLocus"           : "string",
	"GBSeqMoltype"         : "string",
	"GBSeqOrganism"        : "string",
	"GBSeqOtherSeqids"     : ["string"],
	"GBSeqPrimaryAccession": "string",
	"GBSeqReferences"      : [
		{
		    "GBReferenceAuthors"  : ["string"],
		    "GBReferenceJournal"  : "string",
		    "GBReferencePosition" : "string",
		    "GBReferenceReference": "string",
		    "GBReferenceTitle"    : "string"
		}
    	],
	"GBSeqSource"      : "string",
	"GBSeqStrandedness": "string",
	"GBSeqTaxonomy"    : "string",
	"GBSeqTopology"    : "string",
	"GBSeqUpdateDate"  : "string"
}
```

## `protein_data`

Example of an element from protein_data:
```json
{
	"GBSeqAccessionVersion"	: "string",
	"GBSeqComment"		: "string",
	"GBSeqCreateDate"	: "string",
	"GBSeqDefinition"	: "string",
	"GBSeqDivision"		: "string",
	"GBSeqFeatureTable"	: [
		{
			"GBFeatureIntervals": {
				"GBIntervalAccession"	: "string",
				"GBIntervalFrom"      	: "string",
				"GBIntervalTo"		: "string"
			},
			"GBFeatureKey"		: "string",
			"GBFeatureLocation"	: "string",
			"GBFeatureQuals"	: [
			{
				"GBQualifierName"	: "string",
				"GBQualifierValue"	: "string"
			}
			],
			"GBFeaturePartial3"	: "string",
			"GBFeaturePartial5"	: "string"
		}
	],
	"GBSeqLength"		: "string",
	"GBSeqLocus"            : "string",
	"GBSeqMoltype"		: "string",
	"GBSeqOrganism"        	: "string",
	"GBSeqOtherSeqids"	: "string",
	"GBSeqPrimaryAccession" : "string",
	"GBSeqReferences"	: [
		{
			"GBReferenceAuthors"	: ["string"],
			"GBReferenceJournal"	: "string",
			"GBReferencePosition"	: "string",
			"GBReferenceReference"	: "string",
			"GBReferenceTitle"	: "string"
		}
	],
	"GBSeqSource"		: "string",
	"GBSeqStrandedness"	: "string",
	"GBSeqTaxonomy"		: "string",
	"GBSeqTopology"		: "string",
	"GBSeqUpdateDate"	: "string"
}
```

## `table_basic`

Example of an element from table_basic:
``db.table_basic.findOne({ScientificName:"Chlorella vulgaris"})``
```json
{
	"ScientificName"	: "string",
	"TaxId"			: "string",
	"Nucleotides":		[
		{
			"GBSeq_locus"	: "string"
		}
	],
	"Proteins"	: [
		{
			"GBSeq_locus" : "string"
		}
	],
	"Products"	: [
		{
			"ProductName"	: "string",
			"QtyProduct"	: "string"
		}
	],
	"Country"	: [
		{
			"CountryName" : "string"
		}
	]
}
```


## `table_complete`

Example of an element from table_complete:
``db.table_complete.findOne({ScientificName:"Chlorella vulgaris"})``
```json
{
	"ScientificName"	: "string",
	"TaxId"			: "string",
	"Nucleotides"		: [
		{
			"SameAs"	: "nucleotide_data"
		}
	],
	"Proteins"	: [
		{
			"SameAs"	: "protein_data"
		}
	],
	"Products"	: [
		{
			"ProductName"	: "string",
			"QtyProduct"	: "string"
		}
	],
	"Country"	: [
		{
			"CountryName"	: "string"
		}
	]
}
```

Note: Nucleotides and Proteins have type structure of, respectively, nucleotide_data e protein_data.

## `taxonomy_tree`

Example of an element from taxonomy_tree:
``db.taxonomy_tree.findOne({TaxId:"3077"})``
```json
{
	"TaxId"			: "string",
	"Rank"			: "string",
	"ScientificName"	: "string",
	"SubClasses"		: [
		{
			"TaxId"			: "string",
			"Rank"			: "string",
			"ScientificName"	: "string"
		}
	]
}
```
