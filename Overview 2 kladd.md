# MoBa – Overview for researchers

This page gives a short introduction to MoBa and what kind of data you can expect to work with.

For practical guidance (merging, variables, data structure, etc.), see:  
➡️ Using_MoBa_Data.md

---

## What is MoBa?

The Norwegian Mother, Father and Child Cohort Study (MoBa) is a longitudinal cohort study run by the Norwegian Institute of Public Health (FHI).

Participants were recruited during pregnancy and followed over time through repeated data collections. The cohort includes mothers, fathers, and children.

Because of this structure, the data can be used for analyses at several levels — individuals, families, and across generations.

The main purpose of MoBa is to study causes and development of disease, and factors that influence health over time.

MoBa data are often used to look at:
- associations between exposures and outcomes
- how disease develops over time
- genetic and environmental interactions
- differences between individuals and families  

MoBa can also be linked to national health registries, which makes it possible to follow participants over many years using:
- hospital data  
- prescription data  
- mortality and other long-term outcomes  

More information about applying for data:  
https://www.fhi.no/op/studier/moba/forskere/forskning-og-datatilgang-fra-den-no/

---

## What data are available?

An overview of available data files can be found here:  
https://www.fhi.no/en/ch/studies/moba/for-forskere-artikler/moba-research-data-files/

In short, MoBa combines several types of data.

### Questionnaire data
Collected from mothers, fathers, and children at multiple timepoints.

Topics include:
- physical and mental health  
- diet and lifestyle  
- socioeconomic and psychosocial factors  

### Biological data
The biobank includes blood, urine, cord blood and other samples.

These data are commonly used for:
- genetic analyses (GWAS)  
- biomarker studies  
- other omics-based analyses  

More details:
- https://www.fhi.no/en/ch/studies/moba/for-forskere-artikler/genetic-data-from-the-norwegian-mother-and-child-cohort-study-mobagenetics/  
- https://github.com/folkehelseinstituttet/mobagen  

---

## Tools

### Phenotools

Phenotools is an R package developed to make it easier to work with MoBa data in TSD.

It is particularly useful if you are working with multiple data sources or reproducible pipelines.

https://github.com/psychgen/phenotools

---

## Contributing syntax

There is a shared syntax library on the MoBa Wiki.

If you have code for generating variables that could be useful for others, feel free to share it.

Contact: MorBarnData@fhi.no

Note that syntax is checked before it is published, but MoBa is not responsible for errors in analyses that result from use of shared syntax.

---

## Questions

If you have questions about the data or notice something that looks wrong, contact:  
MorBarnData@fhi.no
