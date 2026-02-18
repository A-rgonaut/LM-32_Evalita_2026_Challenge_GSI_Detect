	*************************************************************
	*  GSI:detect - An EVALITA 2026 Task - DEV Dataset Release  *
	*************************************************************

				October 3, 2025
			Fondazione Bruno Kessler (FBK)  
				Trento, Italy


## Overview

GSI:detect Dataset contains short Italian texts collected from social media and informative websites. Each text has been independently annotated by four expert annotators for the presence of gender stereotypes.

Unlike traditional majority-vote approaches, we adopt a perspectivist approach: all annotations are preserved, and a GS Value is derived from the degree of agreement/disagreement among annotators, highlighting the value of annotator disagreement.

⚠️ Trigger warning ⚠️: Some texts may contain sensitive or potentially distressing content.
Disclaimer: The views and opinions expressed in the dataset do not necessarily reflect the views or positions of the task organizers or the informants, as items in the dataset may be short excerpts from a longer text.


## Dataset Split

Total size: ~1000 texts
DEV set: 20% (released here)
TEST set: 80% (held back for evaluation)


## Data Format

The dataset is released in .jsonl format. Each line corresponds to a single data instance with the following structure:

{
  "id": "unique_identifier",
  "text": "Italian_short_text",
  "annotations": ["yes/no", "yes/no", "yes/no", "yes/no"],
  "gs_value": "number_between_0_and_1_with_two_decimals",
  "gs_category": "role | personality | competence | physical | sexual | relational",
  "context": "with_context | no_context"
}


##  Annotation Details
	
	### Annotations
	Binary annotation yes/no for the presence of a gender steretype performed by four expert annotators. 

	### GS Value
	Derived from the four binary annotations (yes/no):
	0.00 → all annotators: no stereotype
	1.00 → all annotators: stereotype present
	Intermediate values reflect disagreement, e.g.:
	0.25 → 1 yes, 3 no
	0.50 → 2 yes, 2 no
	0.75 → 3 yes, 1 no

	### GS Category
	One of six discrete categories: role, personality, competence, physical, sexual, relational.
	Labels are assigned through majority vote; unresolved cases are solved by a super-judge.

	### Context
	with_context → requires external context (provided)
	no_context → self-contained text


## Release

The development set is released under CC-BY-NC-SA 4.0 license.

This release contains the following files: 
- gsi-d_DEV.jsonl --> development set, 200 short texts in Italian annotated for the presence and category of gender stereotypes.
- gsi-d_guidelines_for_annotation.pdf --> the guidelines that were followed during the manual annotation of GSI:detect Dataset.
- README.txt --> this file.


## Contacts

For further information about this data release, please contact: gsievalita@gmail.com

---------------------------------------------------------------------------------------
README created by Sofia Brenna on October 3rd, 2025.
