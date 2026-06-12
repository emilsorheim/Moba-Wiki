# Overview of MoBa Data

### Would you like to contribute with syntax to MoBa's syntax library? 

MoBa Wiki includes a syntax library for variables that may be helpful when analyzing data from MoBa. The aim is to build a more extensive syntax library covering different types of variables based on data from all MoBa questionnaires. 

Please contact [MorBarnData@fhi.no](mailto:MorBarnData@fhi.no) if you have syntax on how to generate variables based on data from MoBa that you think might be helpful to other research projects. 

**All syntax published on the MoBa Wiki page is checked by MoBa, but MoBa is not responsible for any errors in the study results that are caused by errors in syntax.** 



### Scope and Purpose

The Norwegian Mother, Father and Child Cohort Study (MoBa) is a longitudinal, population-based cohort study conducted by the Norwegian Institute of Public Health (FHI). MoBa is a prospective cohort study in which participants are enrolled during pregnancy and followed over time with repeated data collections. 

The cohort comprises mothers recruited during pregnancy, fathers of the participating pregnancies and children followed from birth onwards. This structure enables analyses at the individual, family, and intergenerational level. 

The study was established to generate knowledge about the causes, risk factors, courses, and consequences of diseases and health outcomes, with the objective of improving prevention and treatment. 

This objective determines both the design of the cohort and the structure of the data. The data support analyses of associations between exposures and health outcomes, temporal development of disease, interactions between genetic and environmental factors and variation in risk across individuals and families  

MoBa can be linked to national health registries, which allows comprehensive follow-up across the life course. This provides:

- Diagnoses and hospital data  
- Prescription data  
- Mortality and long-term outcomes  

Projects must fullfil a set of requirements before access to data is approved. Further details on the application process can be found here: [Slik søker du om MoBa-data (FHI)](https://www.fhi.no/op/studier/moba/forskere/forskning-og-datatilgang-fra-den-no/)



### Types of Data in MoBa

An overview of MoBa-data files available to researchers can be viewed [here](https://www.fhi.no/en/ch/studies/moba/for-forskere-artikler/moba-research-data-files/) 

MoBa integrates multiple complementary data sources:

### 1. Questionnaire Data
- Collected from mothers, fathers, and children  
- Covers:
  - Physical and mental health  
  - Lifestyle and diet  
  - Socioeconomic and psychosocial factors  
- Repeated across time (pregnancy → adulthood)

### 2. Biological Data (Biobank)
- Blood, urine, cord blood, and other samples  
- Enables:
  - Genetic analyses (GWAS)  
  - Biomarker research  
  - Omics data (e.g., epigenetics, metabolomics)
 
Information about genetic data in MoBa can be viewed [here](https://www.fhi.no/en/ch/studies/moba/for-forskere-artikler/genetic-data-from-the-norwegian-mother-and-child-cohort-study-mobagenetics/). More information about the dataset, which files are available and how the quality control was performed, is available on the [MoBa Genetics Github site](https://github.com/folkehelseinstituttet/mobagen). 

### Phenotools
Phenotools is an R package written by Laurie Hannigan.
The goal of the phenotools package is to facilitate efficient and reproducible use of phenotypic data from MoBa and linked registry sources in the TSD environment. More information can be found on [MoBa Phenotools Github site](https://github.com/psychgen/phenotools).


### Core Structure

The data within Moba are distributed across multiple datasets and must be linked prior to analysis. They are recorded at both pregnancy level and individual level. These are the identifiers used in Moba:

- `PREG_ID` (pregnancy identifier)  
- `BARN_NR` (child identifier within pregnancy)
- `M_ID` (Mother's identifier)
- `F_ID` (Father's identifier) 

These variables determines how datasets can be linked and how relations within Moba are identified. All identifiers are specific for each project granted access to Moba, meaning that one person has different values on an personal identifer variable between different projects given access to Moba data.

---
  
### Consent to participation and withdrawal of consent

Moba is a consent-based study, meaning that participants can withdraw their concent to participate.

Projects granted access to Moba data gain access to a file containing information about the individuals and pregnancies with valid consent at the particular point in time (SV_INFO file). 

The number of participants and pregnancies included in this file follow a complicated set of rules:
    - If a participating mother withdraws her concent from Moba, every individual in all her pregnancies are removed from the file, regardless of the other individuals state of consent in these pregnancies. The          corresponding father(s) of this mother can however participate in other pregnancies with other women in Moba, but not with this particlar mother that has withdrawn her consent
    - If a father withdraws consent, only his individual identifier (F_ID) is removed from the pregnancies in which he participates in the SV_INFO file.
    - Children can withdraw their consent when reaching the age of 18. Each children participates in only one pregnancy since each person is born only once. Removal of a child's consent from Moba therefore               results in removal in all participants from this pregnancy - meaning all parents and potential siblings (twins/triplets) within this particular pregnancy. 

More information about withdrawal of children's consent can be found here (in Norwegian): https://www.fhi.no/op/studier/moba/deltakere/informasjonsbrev-om-reservasjonsrett/

---

### Merging files

Considering the large amount of data, each questionnaire is delivered as separate data files. When merging the files for analysis, it is important to be aware of the following

* **Data files based on data before birth** *(questionnaire at week 15-17 of pregnancy (Q1, QF), Week 22 of pregnancy (Q2), Week 30 of pregnancy(Q3))*: Include a unique identifier for pregnancy called ‘PREG_ID_XX’. This variable must be used as the key variable when merging files.
* **Data files based on data after birth** *(questionnaire at 6 months (Q4), 18 months (Q5), 3 years (Q6), 5 years (Q5Y), 7 years (Q7Y) etc.)*: Include a identifier for pregnancy (‘PREG_ID_XX’) and a identifier for the child (‘BARN_NR’). Both variables ‘PREG_ID_XX’ and ‘BARN_NR’ must be used when merging files based on data after birth to ensure that data is linked correctly for twins/triplets.
* **For the second Father questionnaire** *(QF2)*:
  * _**Data file based on data from Part 1 (about the father)**_ inlude a unique identifier for the father called ‘F_ID_XX’. This variable must be used as the key variable when merging files.
  * _**Data file based on data from Part 2 (about the child)**_ inlude a identifier for pregnancy (‘PREG_ID_XX’) and a identifier for the child (‘BARN_NR’). Both variables ‘PREG_ID_XX’ and ‘BARN_NR’ must be used when merging files based on data after birth to ensure that data is linked correctly for twins/triplets.

Syntax for merging files can be found on the wiki page [Merge files](Merge%20files.md#merge-files).

### Important considerations
Some participants will have data from all questionnaires, while others will only have data from one questionnaire. It is crucial to be aware of this when interpreting missing values. The data set “SV_INFO” includes a unique identifier for each woman called ‘M_ID_XX’. This variable can be used to identify women who participate with more than one pregnancy and hence identify siblings.



### Variables and Coding
#### Coding of variables 
A categorical variable is coded ‘1’ for the first category, ‘2’ for the second category, and so on. Normally, the answer category ‘No’ is coded ‘1’ and ‘Yes’ is coded ‘2’. However, there is no global coding convention across datasets in Moba, and the direction of coding might be opposite, where ‘Yes’ is coded ‘1’ and ‘No’ is coded ‘2’. 

In general, one should always check the questionnaires for the correct sequence of categories. Dichotomous variables are coded ‘1’ for a tick and a blank (missing) value when there is no tick.

Not all questions are present in every version of a questionnaire. Hence, a variable may have a missing value because the respondent has answered a version of the questionnaire that does not include the specific question. The variable label indicates in which version(s) a specific question was asked, while the variable ‘VERSJON_SKJEMAX_TBL1’ indicates which version of the questionnaire each respondent has answered. If you want to use a variable not included in e.g. version A of a questionnaire, you can use ‘VERSJON_SKJEMAX_TBL1’ to remove version A-respondents from the data set.

#### Important considerations
We urge you to consider how the specific question may be interpreted by the respondent. If a respondent has answered “No” to a question, he/she may not have answered the follow-up questions and the corresponding variable(s) will have a missing value. Some respondents may also have answered inconsistently, e.g. answered “No” when asked “Have you ever smoked?” and answered “Daily” when asked “Do you smoke now?”. Therefore, it is important to check for inconsistency.

For twins and triplets, the mother fills out one questionnaire for each child after birth (i.e. questionnaire 6 months, 18 months, 3 years, 5 years, 7 years and 8 years). The mothers are told to fill in the section “About yourself” for the first child only. MoBa have not duplicated this information to the other sibling(s). These variables are usually missing for one of the twins or two of the triplets.


### Versions
A guideline for use of MoBa data can be found on wiki page [User guides](User%20guides.md) (only available in Norwegian). Below, some important points are listed.

Throughout the history of Moba, questionnaires have been revised and there are more than one version of each questionnaire (A, B, C, ..).. This affects some variables between versions of a questionnaire, resulting in:
- variation in question wording  
- variation in response categories  
- version-specific variables
- differences between variables with identical names between versions in a questionnaire

Many questions are identical across versions and the data is stored in the same variable. Where the questions differs significally between versions data is stored in separate variables. In addition, there are both paper versions and a digital version (W) for the dietary (Q2), 3 year (Q6) and 7 year (Q7) questionnaire. The instrument documentation for each questionnaire contain information about differences between versions of questionnaires as well as meaning of each value on the variables within the questionnaire. 

The instrument documentation for each available Moba questionnaire can be found here: [Questionnaires from Moba](https://www.fhi.no/en/ch/studies/moba/for-forskere-artikler/questionnaires-from-moba/)

An overview of all questionnaires can be found on the wiki page [Questionnaires](Questionnaires.md) and on fhi.no ([English versions](https://www.fhi.no/en/ch/studies/moba/for-forskere-artikler/questionnaires-from-moba/), [Norwegian versions](https://www.fhi.no/op/studier/moba/forskere/sporreskjemaer---mor-og-barn-unders/))



### Variable names
The variable names consist of two or more letters and a number. In questionnaire 1 (Q1) all variables (corresponding to questions) are named ‘AA’ followed by a number. In questionnaire 3 (Q3) all variables (corresponding to questions) are named ‘CC’ followed by a number.

Note that the question number may differ in different versions of the questionnaire. Labels have been translated into English for the majority of the questionnaires.

### Variable labels
The variable labels include the following information:
1. The questionnaire version(s) in which the question is found
2. The question number(s)
3. The question text

### Data quality
### Questionnaire on paper
MoBa data have been through extensive quality control procedures. These are divided in two levels. <br>
**Level 1**: During scanning and verification, all scanned and digitalized numbers are evaluated to check correspondence with what is written in the questionnaires. Some check boxes will also be validated, i.e. when more than one check box is marked for a group of mutually exclusive check boxes.<br>
**Level 2**: Registered data are evaluated again. Rules have been defined for each variable to check values that are (slightly) extreme or not consistent with other answers. Note that limits for valid values set in the quality control procedure do not necessarily comply with plausible limits. Specifically, numbers are checked by comparing the digitalized number with the written response in the questionnaire. Where there are discrepancies, corrections are made. Otherwise data are left unchanged, even if implausible or illogical. Hence, for cut-offs, researchers must use their own considerations. Rules applied in level 2 of the quality control can be found on wiki page [Quality control](Quality%20control.md). Quality control is an ongoing process. Attached documentation explains what has already been done to ensure good data quality. However, if errors are discovered by use of MoBa data, please let us know. If necessary, new rules for quality control will be implemented. 

Variables corresponding to questions where only one answer is intended (index variables) are coded ‘0’ if more than one answer is given. However, some index variables are given valid codes for combinations of two or more ticks. 
The variable ‘ALDERUTFYLT_Sx’ is calculated from ”Date for filling out the questionnaire” given by the respondant in the questionnaire. <br><br>
Note that for the first (Q1), second (Q2) and third (Q3) mother's questionnaire as well as the first father’s questionnaire (QF), the variable ‘ALDERUTFYLT_Sx’ corresponds to the number of days before the child is born. <br><br>
Also note that we have observed some evident errors in the variable ”Date for filling out the questionnaire”. Some respondents have written their own date of birth, their child’s date of birth or other dates that are not valid. This results in errors in the generated variable ‘ALDERUTFYLT_Sx’. To control for these errors, we have added two generated variables to the dataset; ‘ALDERUTSENDT_Sx’ and ‘ALDERRETUR_Sx’. These variables are calculated in the same way as ‘ALDERUTFYLT_Sx’, but utilize the date the questionnaire was sent and the date we received it. These variables may be used for estimation of the child’s age when ‘ALDERUTFYLT_Sx’ is missing or implausible. 

### Digital Questionnaire
The variable ‘ALDERUTFYLT_Sx’ is calculated from the date when the questionnaire was submitted online by the respondant.
Limits for valid values are incorporated in the digital questionnaires. I.e. for questions where only one answer is intended a radio button that only let the user select one option of a collection of options is used in the questionnaire. 

### Data based on free text
Occupational information from questionnaire 1 is coded for approximately 70 % of the participants. Occupational data is mainly available on an aggregate level (See wiki page [Coding of occupation](Coding%20of%20occupation%20and%20industry.md)). All medicines stated in questionnaires during pregnancy and up until the child is 7 years have been coded using the ATC classification system (See wiki page [Coding of medication](Coding%20of%20medication%20(ATC-codes).md)). Data for diseases and other text fields are not coded and are not included in the data sets.



#### Only applies to Questionnaires on paper
A category of variables has been generated, providing the total number of responses filled in on each page of the questionnaire by the respondent. The variable names consist of the questionnaire number and page number; Q1P1, Q1P2 etc. Note that a question may be placed on different pages in different versions of the same questionnaire. These variables are meant to simplify quality control of the data for users and the interpretation of, for instance, missing values (e.g. without noticing, some women have left two pages blank because two sheets have been stuck together).

## Generated variables
Some questions are excluded from the data files for confidential and practical reasons. The information given in these questions is incorporated in generated variables. The most important generated variables are described in the sections below.

### Generated variables from the dietary questionnaire during pregnancy (Q2)
38 variables are generated from the dietary questionnaire and are included in the file “Q2_calculation”. These variables are calculated by use of the Norwegian Food Composition Table 2001. Note that dietary supplements are not included in the intake calculations of vitamins and minerals. The variable ‘VERSJON_KOST_TBL1’ specify which version (KOST_A=A/B or KOST_B=C/D/W) of the dietary questionnaire the calculations are based on. Questionnaires A and B are very different from questionnaires C, D and W. In version A and B the women are asked what they have been eating the last 12 months before they became pregnant, while in version C, D and W they are asked what they have been eating since they became pregnant and until the day they filled out the questionnaire (about week 17-22).
Note that data from the first two versions (A and B) of the diet questionnaire, are given in separate files only by request, since they are not comparable to the questionnaires C, D and W.


### Dates and age
All date variables in the questionnaires are replaced by variables that correspond with the child’s age in days/months/years. <br><br>
The generated variable ‘ALDERUTFYLT_Sx’ contains information about when the questionnaire was filled out by the respondent, given by time in days/months/years from the date of birth of the child until filling out the questionnaire. This will correspond to the child’s age in days, months or years. <br>



# Questions
If you have questions or comments about the data files or suspect that something can be incorrect in labels or other documentation, please contact us at MorBarnData@fhi.no.
