	****************************************************************
	*     GSI:detect - An EVALITA 2026 Task - TEST Set Release     *
	****************************************************************

				December 1, 2025
			Fondazione Bruno Kessler (FBK)  
				Trento, Italy


## Overview on GSI:detect Dataset

GSI:detect Dataset contains short Italian texts collected from social media and informative websites. Each text has been independently annotated by four expert annotators for the presence of gender stereotypes.

Unlike traditional majority-vote approaches, we adopt a perspectivist approach: all annotations are preserved, and a GS Value is derived from the degree of agreement/disagreement among annotators, highlighting the value of annotator disagreement.

⚠️ Trigger warning ⚠️: Some texts may contain sensitive or potentially distressing content.
Disclaimer: The views and opinions expressed in the dataset do not necessarily reflect the views or positions of the task organizers or the informants, as items in the dataset may be short excerpts from a longer text.


## Dataset Split

Total size: 1010 texts
DEV set: 200 texts (released on October 3rd)
TEST set: 810 texts (released here for evaluation)


## TEST Set Data Format

The TEST Set is released in .jsonl format, without any gender stereotype annotation.
Each line in the file corresponds to a single data instance with the following structure:

{
  "id": "unique_identifier",
  "text": "Italian_short_text",
  "gs_value": "",
  "gs_category": "",
  "context": "with_context | no_context"
}


## Required Output Format

Participants must submit their system(s)'s output in a .jsonl file with the following structure:

{
  "id": "unique_identifier",
  "text": "Italian_short_text",
  "gs_value": "number_between_0_and_1_with_two_decimals",
  "gs_category": "role | personality | competence | physical | sexual | relational",
  "context": "with_context | no_context"
}
	
	### GS Value
	For each single text, return a number between or equal to 0 and 1, with two decimals.

	### GS Category
	One of six discrete categories: role, personality, competence, physical, sexual, relational.
	It is required to provide one gs_category label for each single text instance, regardless of its assigned gs_value: i.e., also instances with a gs_value equal to 0 must be assigned one gs_category label.


## How To Submit

	### Naming the files: 
	- choose a team name and name your files following this format: gsidetect_TeamName_SystemName_Runtype_RunNumber
	- specify the number of examples used in the few-shot runtype (e.g.,  gsidetect_TeamName_SystemName_few-shot10_RunNumber)

	### Submission:
	Compress all relevant files into a single .zip archive containing:
	- .jsonl output files in the required format;
	- a brief .txt file with information about any additional data or resource used in your system(s).

	Send it via email to:	gsievalita@gmail.com
	Subject line: 		gsidetect_outputs – TeamName


## Release

The test set is released under CC-BY-NC-SA 4.0 license.

This release contains the following files: 
- gsi-d_TEST_blank.jsonl--> test set, 810 short texts in Italian to be annotated for the presence and category of gender stereotypes.
- README_test.txt 	--> this file.


## Contacts

For further information about this data release refer to https://gsi-d-evalita.fbk.eu/ or please contact: gsievalita@gmail.com

-------------------------------------------------------------------------------
README created by Sofia Brenna on December 1st, 2025.
