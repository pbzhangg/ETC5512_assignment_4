Data Origin

This project combines two publicly available datasets to examine how generative 
AI exposure varies across occupations and demographic groups in Australia.

The first dataset is the Australian Bureau of Statistics (ABS) Census 2021 G60: 
Occupation by Age by Sex dataset. This dataset was obtained from the Australian 
Bureau of Statistics and contains aggregated counts of employed persons by state, 
sex, age group, and occupation. It is based on the 2021 national Census, which aims
to collect comprehensive demographic and labour force information about residents 
in Australia. The dataset is released under the Creative Commons Attribution 4.0 
International (CC BY 4.0) licence.

The second dataset is the Jobs and Skills Australia (JSA) Generative AI Exposure 
dataset, which forms part of their "Our Gen AI Transition: Exposure, Adaptation 
and Dynamism" project. This dataset provides occupation-level estimates of generative 
AI exposure, including measures of augmentation and automation scores. It is publicly 
released under an Australian Government open data licence and is based on modelled 
estimates of occupational task exposure to generative AI technologies.

Files Included

The raw_data/ folder contains the original datasets as they were downloaded from 
their respective sources. This includes the ABS Census 2021 GeoPackage files, which 
provide spatial and demographic information on employment by occupation, and the 
JSA generative AI exposure dataset, which is stored in an Excel format and contains 
occupation-level AI exposure estimates.

merged_data.rds
This file contains the final processed dataset used for analysis. The dataset 
combines ABS Census 2021 demographic and occupational count data with Jobs and 
Skills Australia generative AI exposure scores. It includes variables state, sex, 
age group, major occupation group, employment counts, and occupational AI exposure 
measures. The dataset is structured to support analysis of how generative AI exposure 
varies across demographic and occupational groups in the Australian workforce.

data_dictionary.csv
This file contains the data dictionary for the processed dataset. It describes 
each variable in the dataset, including variable names, data types, descriptions, 
and derivation methods. The data dictionary provides information on how each variable 
was constructed from the original ABS Census and JSA datasets and should be used as a 
reference for correctly interpreting the transformed data.

README.txt
This file contains documentation describing the origin of the datasets, the structure 
of the repository, the data processing workflow, and the intended use of the final 
processed dataset. It also outlines key assumptions and limitations associated with the 
data, as well as guidance on how to reproduce the analysis using the provided scripts 
and publicly available data sources.

Intended Use

This project is intended for academic and research purposes, specifically to analyse 
the distribution of generative AI exposure across different occupations and demographic 
groups in the Australian workforce. The data and scripts are designed to support 
reproducible analysis, statistical modelling, and data visualisation to answer the 
research questions.

Assumptions

This analysis assumes that generative AI exposure scores are constant within each 
major occupation group and can be applied uniformly across all demographic subgroups.
It also assumes that ABS Census occupation categories can be accurately mapped to the 
occupation classification used in the Jobs and Skills Australia dataset. In addition, 
mean values are used to summarise occupational exposure scores, which assumes that 
average exposure adequately represents variation within occupations.

Limitations

The generative AI exposure measures used in this project are model-based estimates 
and do not represent actual AI usage or real-world employment outcomes. The ABS 
Census data reflects the 2021 labour market and may not capture more recent changes 
in occupational structure or employment patterns. Differences in classification 
systems between ABS and JSA required aggregation of occupations, which may reduce 
classification detail. Furthermore, within-occupation variation in AI exposure is 
not captured, and spatial data included in the dataset is used solely for visualisation 
purposes.

Reproducibility

All data processing steps are fully reproducible using the code provided in this 
project. Users can reproduce the analysis by following the download instructions 
for the raw datasets from the ABS and Jobs and Skills Australia sources, placing 
them in the raw_data/ folder, and running the provided code. The processed dataset 
will then be generated automatically in the processed_data/ folder.
