# support2-eda

## Project Overview

This repository contains a comprehensive exploratory data analysis (EDA) of the SUPPORT2 critical care dataset. The dataset records clinical and demographic information for over 9,000 adult patients admitted to intensive care units, together with short- and long-term outcomes. Our aim is to understand the characteristics of the cohort, assess data quality and uncover relationships between severity scores, demographics and mortality.

## Data

The SUPPORT2 dataset includes 9,105 patients and 48 variables, spanning demographic variables (age, sex, race), physiological measurements (e.g. blood pressure, lab results), functional scores (e.g. SCOMA, APS, SPS) and outcome indicators (hospital death, 180-day death, costs). Variables are a mix of numeric and categorical data. Many clinical variables exhibit missingness, particularly laboratory and functional measurements.

## Methodology

The analysis proceeds through several stages:

- **Initial assessment:** inspection of variable types, identification of numeric vs categorical variables and check for duplicate records (none were found).
- **Descriptive statistics:** calculation of summary statistics for continuous variables (mean, median, standard deviation) and frequency counts for categorical variables.
- **Missing data analysis:** quantification of missing values per variable, identification of high-missingness variables such as ADL scores, urine output, glucose and BUN, and discussion of how missingness may affect analyses.
- **Outlier detection:** exploration of distributions for age, physiological measurements and cost variables; age has a few outliers above 100 years, while cost variables and length of stay are heavily right-skewed with many high-value outliers.
- **Exploratory visualisations:** histograms, boxplots and pair plots to examine the distribution of key variables. Age is concentrated between 50-80 years; charges and length of stay are right-skewed; dementia is rare; around 75% of patients survive to hospital discharge.
- **Bivariate and multivariate analyses:** correlations among severity scores (SCOMA, APS, SPS), age and outcome variables. Severity scores are strongly correlated with mortality and with each other, while age is a weaker predictor. Pair plots show that patients who die by 180 days tend to be older with higher SCOMA and APS scores.
- **Skewness and kurtosis:** assessment of distribution shape; cost variables and length of stay show extreme skewness and heavy tails, whereas age is slightly left-skewed.
- **Cross-tabulations and hypothesis testing:** mortality rates by sex, disease class and race. ARF/MOSF (acute respiratory failure/multiple organ system failure) and cancer groups have higher death rates. Differences between race groups are noted but interpreted cautiously.
- **Variable cleaning:** some variables (e.g. `sfdm2`) combine numeric codes and descriptive labels; these were converted to numeric codes where possible. Remaining unidentified values were left missing.

## Key Findings

- Severity scores (SCOMA, APS and SPS) are the most informative predictors of survival; higher scores are strongly associated with hospital and 180-day mortality.
- Age shows a mild association with mortality but is a weak discriminator compared with severity scores.
- The cost and length-of-stay variables are highly skewed; a small number of patients incur extremely high costs.
- Missing values are common in functional and laboratory measures. Recognising patterns of missingness is crucial before fitting predictive models.
- Mortality differs markedly by disease class and to a lesser extent by sex and race; ARF/MOSF and cancer patients have worse outcomes.

## Repository Structure

```
support2-eda/
├── AP_CI7340_Coursework2.ipynb  # J# Jupyter notebook with the full analysis (personal info removed)
├── requirements_support2.txt                     # Python packages required to run the notebook
├── README.md                                     # Project overview and analysis summary
└── LICENSE                                       # MIT Licence
```

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/Ayesha-code-arch/support2-eda.git
   cd support2-eda
   ```
2. Create a virtual environment and install the dependencies:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements_support2.txt
   ```
3. Launch Jupyter Notebook and open the sanitised notebook:
   ```bash
   jupyter notebook
   ```
   The notebook walks through data loading, cleaning and EDA. You can rerun each cell or modify the analysis for your own purposes.

## Licence

This project is licensed under the MIT Licence; see the LICENSE file for details.

## Acknowledgements

The SUPPORT2 dataset was originally collected as part of the Study to Understand Prognoses and Preferences for Outcomes and Risks of Treatments. This repository is for academic purposes only.
