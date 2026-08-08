# Generative AI Exposure in the Australian Workforce

An analysis of how generative AI exposure varies across Australian occupations and how workers of different ages and sexes are distributed across occupations with different levels of AI exposure.

The project integrates **2021 Australian Census workforce data** with occupation-level **Jobs and Skills Australia generative AI exposure estimates** to examine both the demographic distribution of AI exposure and the balance between AI augmentation and automation.

**R · tidyverse · sf · ABS Census · Jobs and Skills Australia · Data Integration · Data Visualisation**

## Project Overview

Generative AI is expected to affect occupations differently depending on the types of tasks involved. While some occupations may experience greater automation of existing tasks, others may primarily use AI to augment and support human work.

This project investigates how these differences in occupational AI exposure intersect with the demographic structure of the Australian workforce.

### Research Question

**How are demographic characteristics associated with employment in occupations with different levels of generative AI exposure in Australia?**

### Sub-Questions

1. Which occupations exhibit the highest and lowest levels of generative AI exposure?
2. Which demographic groups, by age and sex, are most concentrated in occupations with high AI exposure?
3. To what extent are AI-exposed occupations characterised by AI augmentation versus AI automation?

## Data Sources

| Dataset | Source | Purpose |
| --- | --- | --- |
| 2021 Census G60: Occupation by Age by Sex | [Australian Bureau of Statistics](https://www.abs.gov.au/census/find-census-data/geopackages?release=2021&geography=AUST&table=G60&gda=GDA2020) | Workforce counts by occupation, age and sex |
| Generative AI Exposure Data | [Jobs and Skills Australia](https://www.jobsandskills.gov.au/studies/generative-artificial-intelligence-capacity-study) | Occupation-level AI augmentation and automation exposure measures |

The ABS Census dataset contains aggregated counts of employed people by occupation, age group and sex. The Jobs and Skills Australia dataset provides model-based estimates of the potential exposure of occupational tasks to generative AI.

> **Note:** Large raw Census GeoPackage files and the processed `merged_data.rds` dataset are not included in this repository due to their file size. The original datasets can be downloaded from the sources above and reproduced using the provided Quarto analysis.

## Data Processing

The two datasets use different structures and levels of occupational classification, requiring several processing steps before they could be integrated.

The workflow included:

- Aggregating Jobs and Skills Australia occupation-level exposure measures into the eight ANZSCO major occupation groups
- Calculating mean AI augmentation and automation exposure scores for each occupation group
- Transforming the ABS Census data from wide to long format
- Extracting sex, age group and occupation information encoded within Census variable names
- Standardising occupation classifications between the ABS and Jobs and Skills Australia datasets
- Validating occupation matches before joining the datasets
- Combining workforce demographic counts with occupation-level AI exposure measures
- Deriving an AI balance measure as augmentation exposure minus automation exposure

### Processing Workflow

```text
Jobs and Skills Australia              ABS 2021 Census
AI exposure data                       workforce data
        │                                   │
        ↓                                   ↓
Clean and aggregate                Reshape and extract
occupation measures                demographic variables
        │                                   │
        ↓                                   ↓
ANZSCO major occupation            ANZSCO major occupation
groups                             groups
        │                                   │
        └──────────────┬────────────────────┘
                       ↓
                 Data integration
                       ↓
            Demographic + AI exposure
                       ↓
                     Analysis
```

## Analysis

### Occupational AI Exposure

AI augmentation and automation exposure scores were compared across the eight ANZSCO major occupation groups.

The analysis distinguishes between:

- **Augmentation** — AI supporting or enhancing tasks performed by workers
- **Automation** — AI potentially performing tasks currently undertaken by workers

### Demographic Concentration

Occupations with AI augmentation exposure above the median were classified as **high AI-exposure occupations**.

The proportion of each age and sex group employed in these occupations was then calculated. This approach measures how concentrated each demographic group is within higher-exposure work rather than simply examining the demographic composition of those occupations.

### Augmentation vs Automation

An **AI balance** measure was calculated as:

```text
AI Balance = Augmentation Exposure − Automation Exposure
```

Positive values indicate that augmentation exposure exceeds automation exposure.

## Key Findings

- **Professionals, Clerical and Administrative Workers, and Managers recorded the highest AI augmentation exposure scores**, at approximately 0.693, 0.692 and 0.691 respectively.

- **Clerical and Administrative Workers had the highest automation exposure score (0.600)**, followed by Sales Workers (0.475) and Managers (0.395).

- Occupations involving more physical work had comparatively lower exposure. **Machinery Operators and Drivers** recorded augmentation and automation scores of 0.548 and 0.275, while **Labourers** recorded the lowest scores at 0.456 and 0.196.

- **69.9% of female workers were employed in occupations classified as high AI exposure**, compared with **49.8% of male workers**.

- The proportion of workers in high AI-exposure occupations generally increased with age, from **43.1% among workers aged 15–19** and **46.3% among those aged 20–24**, to **74.2% among workers aged 75–84** and **81.5% among those aged 85+**.

- **AI augmentation exposure exceeded automation exposure across all eight major occupation groups**, suggesting that generative AI exposure is more strongly associated with supporting and enhancing work tasks than replacing them.

Overall, the demographic differences observed in the analysis primarily reflect differences in **where demographic groups are employed**. They should not be interpreted as evidence that age or sex itself causes greater exposure to generative AI.

## Limitations

The AI exposure measures are **model-based estimates of potential occupational exposure**, not observed measures of AI adoption, use or job displacement.

Occupations were aggregated to the eight ANZSCO major occupation groups to enable integration between the datasets. This improves comparability but may conceal substantial differences between individual occupations within the same major group.

The demographic analysis is limited to age and sex, while other characteristics such as income, industry and geographic location may also be associated with occupational AI exposure.

The analysis is descriptive and does not establish causal relationships between demographic characteristics and AI exposure.

Finally, the demographic data comes from the **2021 Census**, while the AI exposure estimates are more recent. Workforce composition and occupational structures may therefore have changed between the two periods.

## Future Improvements

Potential extensions of this analysis include:

- Using more detailed occupation classifications to capture variation within major occupation groups
- Incorporating additional demographic and socioeconomic characteristics
- Examining geographic differences in occupational AI exposure
- Incorporating industry-level information
- Applying statistical modelling to investigate associations between workforce characteristics and employment in AI-exposed occupations
- Updating the demographic analysis as newer Census or workforce data becomes available

## Repository Structure

```text
australian-workforce-ai-exposure/
│
├── README.md
├── ai-workforce-analysis.qmd
│
├── raw_data/
│   └── raw_exposure_data.xlsx
│
└── processed_data/
    └── README.txt
    └── data_dictionary.csv
    └── merged_data.rds
```

## Reproducing the Analysis

To reproduce the project:

1. Download the **2021 Census G60 Occupation by Age by Sex GeoPackage** from the Australian Bureau of Statistics.
2. Download the **JSA AI Study Interactive Tables** from Jobs and Skills Australia.
3. Place the downloaded files in the locations expected by `ai-workforce-analysis.qmd`.
4. Install the required R packages, including `tidyverse`, `sf`, `readxl` and `here`.
5. Render or run `ai-workforce-analysis.qmd`.

The Quarto document contains the complete data processing, integration, analysis and visualisation workflow.

## Project Context

This project was completed individually as part of **ETC5512: Wild-Caught Data at Monash University**.
