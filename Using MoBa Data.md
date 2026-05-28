# Using MoBa data

This page covers things you will need to know when working with MoBa data in practice. 

For questions, contact MorBarnData@fhi.no

---

## Data structure and identifiers

MoBa data are delivered as multiple datasets that need to be merged before analysis.

The main identifiers are:

- `PREG_ID` – pregnancy  
- `BARN_NR` – child within pregnancy  
- `M_ID` – mother  
- `F_ID` – father  

These determine how datasets can be linked and how relationships are defined. Note that identifiers are project-specific. The same individual will have different IDs in different projects.


## Merging data files

Each questionnaire is delivered as a separate file.

### Data from pregnancy (before birth)

Applies to:
- Q1, QF (week 15–17)
- Q2 (week 22)
- Q3 (week 30)

For merging, use:
- `PREG_ID`  

### Data after birth

Applies to:
- Q4, Q5, Q6, Q5Y, Q7Y, etc.

for merging, use:
- `PREG_ID` + `BARN_NR`  

Both are needed to correctly separate children in multiple births.

### Father questionnaire (QF2)

There are two parts:

- Part 1 (father): use `F_ID` for merging
- Part 2 (child): use `PREG_ID` + `BARN_NR` for merging


### A note on missing data

Not everyone participates in all questionnaires.

Missing values may therefore mean:
- the question was not asked  
- the questionnaire version did not include it  
- the participant did not respond  


### SV_INFO

You will receive a file called `SV_INFO`.

This file:
- contains individuals with valid consent  
- includes `M_ID`, which can be used to identify women with multiple pregnancies  


## Consent and withdrawal

MoBa is based on consent, and participants can withdraw.

The rules are not entirely intuitive:

- If a mother withdraws → all her pregnancies are removed  
- If a father withdraws → only the father is removed  
- If a child (≥18 years) withdraws → the entire pregnancy is removed  

More details (Norwegian):  
https://www.fhi.no/op/studier/moba/deltakere/informasjonsbrev-om-reservasjonsrett/


## Variables and coding

There is no single coding standard across MoBa datasets.

A common pattern is:
- 1 = No  
- 2 = Yes  

But the opposite also occurs, so always check.

For many variables:
- a tick = 1  
- no tick = missing  

### Questionnaire versions

Most questionnaires exist in several versions (A, B, C, etc.).

This affects:
- wording  
- response options  
- whether variables are directly comparable  


To identify which version was answered, use `VERSJON_SKJEMAX_TBL1`

Documentation:
https://www.fhi.no/en/ch/studies/moba/for-forskere-artikler/questionnaires-from-moba/


### Things worth checking

- skip patterns (missing values after “No” answers)  
- inconsistent answers  
- version differences  

Example:  
Someone can answer “No” to smoking history but still report current smoking.


### Twins and triplets

After birth, one questionnaire is filled out per child.

However:
- the “About yourself” section is only filled out once  
- data are not duplicated  

This means some variables will be missing for siblings.


## Variable names and labels

Variable names are linked to questionnaires:

- Q1 → `AA...`
- Q3 → `CC...`

Labels typically include:
- questionnaire version  
- question number  
- question text  


## Data quality

MoBa data have gone through quality control, but are not fully “cleaned” for analysis.

### Two levels

**Level 1**
- checks during scanning and data entry  

**Level 2**
- checks for inconsistencies and extreme values  

Important:  
Values are usually corrected only if clearly wrong. Implausible values may still remain.


### Age variables

`ALDERUTFYLT_Sx` is often used, but can contain errors.

Alternatives:
- `ALDERUTSENDT_Sx`
- `ALDERRETUR_Sx`

These can be useful if dates are inconsistent.


## Other data types

### Free text

- Occupation: coded for ~70%  
- Medication: coded using ATC  
- Other text fields: not included  


### Generated variables

Some data are only available as derived variables.

#### Dietary data (Q2)

- Stored in `Q2_calculation`
- Based on Food Composition Table (2001)

Note:
Versions A/B and C/D/W are quite different and not directly comparable.


## Final tips

Before starting an analysis, it is usually worth:

- checking which questionnaire versions you are using  
- verifying coding for key variables  
- looking at missingness patterns  
- making sure merges behave as expected  
