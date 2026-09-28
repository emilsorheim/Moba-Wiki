
# Getting Started with MoBa

This page provides a high-level introduction to the structure of MoBa and how to work efficiently with MoBa data.

It complements existing wiki pages and focuses on understanding the MoBa ecosystem rather than detailed variable documentation.

For detailed information, see:

- Read this before analyses
- Questionnaires
- Generated variables
- Quality control
- Genetic data in MoBa
- Phenotools

---

# What is MoBa?

The Norwegian Mother, Father and Child Cohort Study (MoBa) is a longitudinal family-based cohort study.

Participants were recruited during pregnancy and followed over time through questionnaires, biological samples, genetic data and linkage to national registries.

MoBa is particularly valuable because it contains:

- mothers
- fathers
- children
- siblings
- twins and triplets
- repeated measurements across life stages

This allows analyses at:

- individual level
- pregnancy level
- family level
- sibling level
- intergenerational level

---

# Understanding the MoBa Data Landscape

MoBa consists of several interconnected data sources.

## Questionnaire data

Questionnaires form the core of MoBa.

Data include:

- physical health
- mental health
- lifestyle
- diet
- pregnancy exposures
- family environment
- child development
- education and work

Questionnaires exist from pregnancy through adolescence and adulthood.

See:

- Questionnaires

---

## Registry data

Projects may receive linked registry data.

Examples include:

- Medical Birth Registry of Norway (MBRN)
- Norwegian Patient Registry (NPR)
- Norwegian Prescription Database (NorPD)
- Cause of Death Registry
- Cancer Registry
- Additional approved registries

Registry data often provide:

- diagnoses
- procedures
- medication use
- mortality
- long-term follow-up

---

## Biological samples

MoBa contains one of the world's largest pregnancy biobanks.

Available materials may include:

- maternal blood
- paternal blood
- cord blood
- urine
- DNA

These resources support:

- biomarker research
- genomics
- proteomics
- metabolomics
- epigenetics

---

## Genetic data

Genetic data are available for large subsets of MoBa participants.

Unique strengths include:

- parent-offspring trios
- sibling pairs
- family-based analyses
- within-family genetic designs

See:

- Genetic data in MoBa
- MoBaGenetics
- Phenotools

---

# Common Study Designs in MoBa

Many researchers are unfamiliar with the family structure of MoBa.

Common approaches include:

## Pregnancy exposure studies

Example:

- smoking during pregnancy
- alcohol use
- medication use
- nutrition

## Prospective cohort studies

Exposure measured before outcome occurs.

A major strength of MoBa.

## Family-based studies

Comparison within:

- siblings
- parent-child pairs
- trios

These analyses can reduce confounding.

## Genetic analyses

Examples:

- GWAS
- Polygenic Scores
- Mendelian Randomization
- Within-family GWAS

---

# Frequently Overlooked Issues

Researchers new to MoBa often overlook the following:

## Multiple pregnancies

The same woman can participate with several pregnancies.

Always determine whether analyses should be based on:

- pregnancies
- mothers
- children

before calculating sample size.

---

## Multiple births

One pregnancy can produce:

- twins
- triplets

Pregnancy-level analyses and child-level analyses may therefore produce different numbers of observations.

---

## Questionnaire versions

Most questionnaires exist in multiple versions.

Before combining data:

- verify comparability
- inspect questionnaire versions
- review instrument documentation

---

## Missing values

Missing values do not always mean missing information.

Common reasons include:

- questionnaire version differences
- skip patterns
- twin questionnaires
- conditional questions

Always investigate the reason before treating missing values as true missingness.

---

## Identifier level

Before merging any datasets, determine whether variables exist at:

- mother level
- father level
- pregnancy level
- child level

Failure to do so is one of the most common causes of incorrect analyses.

---

# Recommended Workflow

1. Read "Read this before analyses"

2. Identify relevant questionnaires and registries

3. Review questionnaire versions

4. Determine unit of analysis
   - mother
   - father
   - pregnancy
   - child

5. Review generated variables

6. Review quality control documentation

7. Merge data and validate record counts

8. Perform descriptive checks before main analyses

---

# Useful Resources

## Documentation

- Questionnaires
- Generated variables
- Quality control
- Coding of medication (ATC codes)
- Coding of occupation and industry
- Phenotools

## External resources

- MoBa researcher portal
- Instrument documentation
- Registry documentation
- MoBaGenetics GitHub repository

## Support

Questions about data:

MorBarnData@fhi.no

Questions regarding approved applications and access:

mobaadm@fhi.no

---

# A Final Recommendation

When working with MoBa, spend as much time understanding the structure of the data as analyzing it.

Most problems experienced by new researchers are caused by:

- incorrect merging
- misunderstanding unit of analysis
- questionnaire version differences
- family structure complexities

Understanding these issues before analysis will save substantial time later.
