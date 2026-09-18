# MoBa – Overview for researchers

This page gives a short introduction to MoBa and what kind of data you can expect to work with.

For practical guidance (merging, variables, data structure, etc.), see:  
➡️ Using_MoBa_Data.md

---
### Scope and Purpose
The Norwegian Mother, Father and Child Cohort Study (MoBa) is an ongoing and consent-based longitudinal cohort study conducted by the Norwegian Institute of Public Health (FHI). The study was established to generate knowledge about the causes, risk factors, courses, and consequences of diseases and health outcomes, with the objective of improving prevention and treatment. This objective determines both the design of the cohort and the structure of the data. 

The participants in Moba are enrolled during pregnancy and followed over time with repeated data collections. The cohort includes mothers, fathers, and children. 

The data support analyses of associations between exposures and health outcomes, temporal development of disease, interactions between genetic and environmental factors and variation in risk across individuals and families, and the study enables analyses at the individual, family, and intergenerational level. MoBa can be linked to national health registries, which allows comprehensive follow-up across the life course.

Projects must fullfil a set of requirements before access to data is granted. Further details on the application process can be found here: [Slik søker du om MoBa-data (FHI)](https://www.fhi.no/op/studier/moba/forskere/forskning-og-datatilgang-fra-den-no/)

### Consent to participation and withdrawal of consent

Moba is a consent-based study, meaning that participants can withdraw their concent to participate.

Projects granted access to Moba data gain access to a file containing information about the individuals and pregnancies with valid consent at the particular point in time (SV_INFO file). 

The number of participants and pregnancies included in this file follow a complicated set of rules:
    - If a participating mother withdraws her concent from Moba, every individual in all her pregnancies are removed from the file, regardless of the other individuals state of consent in these pregnancies. The          corresponding father(s) of this mother can however participate in other pregnancies with other women in Moba, but not with this particlar mother that has withdrawn her consent
    - If a father withdraws consent, only his individual identifier (F_ID) is removed from the pregnancies in which he participates in the SV_INFO file.
    - Children can withdraw their consent when reaching the age of 18. Each children participates in only one pregnancy since each person is born only once. Removal of a child's consent from Moba therefore               results in removal in all participants from this pregnancy - meaning all parents and potential siblings (twins/triplets) within this particular pregnancy. 

More information about withdrawal of children's consent can be found here (in Norwegian): https://www.fhi.no/op/studier/moba/deltakere/informasjonsbrev-om-reservasjonsrett/

## Questions

#### If you have questions about the data or notice something that looks wrong, contact:  MorBarnData@fhi.no




