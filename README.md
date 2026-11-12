# Genetic and nutritional contributions to height variation

Course project for Data Analytics at Rensselaer Polytechnic Institute (August–December 2023), designed and
carried out independently. All code is in R.

## Question

Adult height is highly heritable, yet average height also differs between countries in ways that track diet
and living standards. This project asked whether population-level patterns in height-associated genetic
variants and in national food supply each relate to average height, and what can and cannot be concluded when
genetic and nutritional data come from different sources.

## Data

| Source | Used for |
| --- | --- |
| 1000 Genomes Project (2,504 individuals) | Genotypes for candidate variants in 10 height-associated genes chosen from the literature, with sex, population and super-population |
| A population-to-country table I compiled | Linking each 1000 Genomes population to a country or region |
| NCD Risk Factor Collaboration (NCD-RisC): country-level mean height at age 19, by sex and year | Outcome |
| FAOSTAT food balance sheets | Protein, fat and energy supply per person, and supply of individual food groups |

The data files are not included in this repository.

## Approach

`analysis/height_genetics_nutrition.R`
1. **Genotype coding.** Recoded phased genotypes as 0 (two reference alleles), 1 (heterozygous) or 2 (two
   alternative alleles), and counted each type per individual across the candidate variants.
2. **Exploratory analysis.** Compared genotype-type counts across countries, and looked at the distribution of
   height and of protein, fat and energy supply across countries.
3. **Merging.** Linked genetic summaries, height and food supply by country (and by year where available),
   separately for males and females.
4. **Modelling.** Fitted linear regressions of mean height on nutritional variables, on genetic summaries, and
   on both together, overall and by sex. Used PCA on the standardized food-supply variables to deal with the
   many correlated food items, and decision trees (described in the report) to check which variables the
   models selected.

## What I learned

- In the joint models, both nutritional and genetic terms were associated with height, but the analysis is
  ecological: genotype counts from a small number of 1000 Genomes populations were assigned to whole
  countries, so it cannot separate genetic from environmental differences between populations.
- Only a limited number of countries had all three data types, compared with the number of correlated food
  variables, so the full regressions should be read with caution; PCA helped summarize the food variables.
- Counting genotype types across variants is a crude summary. A polygenic score weighted by published effect
  sizes would be the natural next step, and this is the approach I moved on to in my MSc work on polygenic
  risk.

## Other files

`coursework/` holds two earlier labs from the same course (exploratory analysis of the 2010 Environmental
Performance Index data, and a short multivariate exercise).

Line endings were converted from the old Mac format so that the code displays correctly on GitHub; the code is
otherwise as submitted.

## Contact

Yunqi (Vicky) Liu — vickyliu1998424@gmail.com
