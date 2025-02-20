# NHANES Dataset Analysis Documentation
> Focus on cardiovascular biomarkers, frailty assessments, and neurological markers

## Table of Contents
- [Overview](#overview)
- [Dataset Information](#dataset-information)
- [Research Focus](#research-focus)
- [Methodologies](#methodologies)
- [Tools and Technologies](#tools-and-technologies)
- [Bibliography](#bibliography)

## Overview
This research project leverages the National Health and Nutrition Examination Survey (NHANES) dataset to investigate the relationships between cardiovascular biomarkers, frailty indicators, and neurological markers in the US population. The study aims to comprehensively analyze these health parameters by utilizing various statistical and analytical techniques.
The primary focus areas include:
- Analysis of cardiovascular biomarkers to assess heart health and disease risk
- Evaluation of frailty measurements and their correlations with other health indicators
- Investigation of neurological markers where available in the dataset
This documentation serves as a comprehensive record of the analytical methods, tools, and bibliographic resources used throughout the research process. The project emphasizes the technical aspects of data analysis, including statistical methodologies, programming approaches, and data processing techniques employed to extract meaningful insights from the NHANES dataset.

## Association Between Oral Health and Frailty Among American Older Adults

### Dataset Information
- 2011-2014
- 2368 community-dwelling adults aged 60 years and older

### Variables of Interest
#### Frailty Outcome
- Frailty was measured with the 49-item frailty index:
    1. cognition
    2. dependence
    3. depression
    4. comorbidities
    5. hospital utilization
    6. general health
    7. physical performance
    8. anthropometry
    9. laboratory values
- A value between 0 and 1 was assigned according to the severity of the deficit
- The frailty index value is expressed as the number of the acquired de cits by the participant divided by the total number of potential deficits

#### Explanatory Variables
- Number of teeth
- Periodontal disease (in this study was categorized into 2 groups,“No/Mild periodontitis” and“Moderate/Severe periodontitis.")

#### Covariates
- Gender
- Ethnicity
- Education
- Poverty-income ratio
- smoking status

### Research Focus
The research question of this study is whether oral health indicators, namely number of teeth and periodontal disease, are associated with frailty index among older American adults?

### Methodologies
#### Data Preprocessing
- excluding participants who did not have complete oral health examination or had missing data in any other covariate
-  All participants with fewer than 2 teeth were excluded from the periodontal disease analysis 
- If participants did not fall in any of
the definitions the authors used for perioodontitis, they were de ned in“no periodontitis” group
- They created a nutritional intake
variable by summing up the 13 micronutrient variables (0 indicates
adequate intake of all the nutrients, 13 indicates inadequate intake of all the nutrients)

#### Statistical Analysis
- Descriptive statistics were carried out stratified by frailty status
- **Negative binomial regression** was used to test the association between frailty index and each of the oral health indicators, namely number of teeth (0-32) and periodontitis (No/Mild versus Moderate/
Severe periodontitis).
- For each oral health indicator, 3 models were constructed: adjusted according to the covariates
- STATA version 16s

#### Machine Learning Approaches 
- no machine learning integration was performed

### Results and Findings
#### Key Outcomes
- This study demonstrated that in a nationally representative sample of older American adults, oral health indicated by tooth loss and periodontal disease was associated with frailty index. 
- The significant association between tooth loss and frailty persisted even after adjusting of important covariates.
- Oral health is associated with the frailty index, and nutritional intake appears to have a modest effect on the association. 
- Periodontal disease has a weaker association with frailty compared with number of teeth.  

#### Visualizations
- 3 tables with Mean, Max-Min range, p-value and rate ratio (RR):
    1. Demographic, Socioeconomic and Oral Health Caharacteristics
    2. Negative Binomial Regression Models Showing the Associations Between Number of Teeth and Frailty
    3. Negative Binomial Regression Models Showing the Associations Between Periodontal Disease and Frailty Index

## Periodontitis and low cognitive performance: A population-based study

### Dataset Information
- NHANES 2011-2014 database
- 2086 participants ≥60 anni
- Representative of 77.1 million US non-institutionalized adults

### Variables of Interest
#### Cognitive Performance Outcome
- Cognitive tests:
    1. CERAD-WL (Consortium to Establish a Registry for Alzheimer's diseas)
    2. AFT (animal fluency test)
    3. DSST (digit symbol substitution test)
    4. Global cognition score (Standardized sum of the preceding)

#### Explanatory Variables
- Periodontal state (none/mild, moderate, severe according to criteria CDC/AAP)
- Average PPD (probing pocket depth)
- Average CAL (clinical attack level)

#### Covariates
1. Age
2. Gender
3. Smoking status
4. Level of family poverty
5. Education level
6. Consumption of alcohol

### Mediators
- Diabetes
- Hypertension
- Cardiovascular/cerebrovascular disease
- Systemic inflammation marker (counts white blood cells and platelets)

### Research Focus
Study the association between periodontitis and low cognitive performance in elderly adults ( 60 years) in a representative USA sample.

### Methodologies
#### Data Preprocessing
- Excluding edentulous subjects
- Excluded subjects without complete periodontal examination
- Subjects who have not completed at least one cognitive test are excluded
- Dichotomized cognitive performance using the unweighted lower quartile
- Global cognition score calculation as the sum of the standardized z-scores of CERAD-WL, AFT and DSST

#### Statistical Analysis
- Continous variables expressed with mean and std, categorical variables expressed with proportions and standard error
- Simple and Multiple Regression to assess association between periodontitis and low cognitive performance
- Analysis adjusted for confounding a priori
- Logistic Regression for mediators analysis to study the role of each potential mediator
- Software: STATA BE v17.1

#### Machine Learning Approaches 
- no machine learning integration was performed

### Results and Findings
#### Key Outcomes
- Moderate and severe periodontitis significantly associate low DSST performance
- Stronger associations for the women
- Average CAL associated with low performance in global cognition, AFT and DSST

#### Visualizations
- 4 detailed tables with OR, IC95% and p-value
- 1 figure with cognitive test distributions per each periodontal state

## A systematic comparison of machine learning algorithms to develop and validate prediction model to predict heart failure risk in middle-aged and elderly patients with periodontitis (NHANES 2009 to 2014)

### Dataset Information
- NHANES 2009-2014
- Total 2876 participants with periodontitis
- Training set: 1980 subjects (2009-2012)
- Validation set: 896 subjects (2013-2014)

### Variables of Interest
#### Outcome
- Heart failure risk in middle-aged and elderly patients with periodontitis. Binary class.

#### Independent Variables
Key predictors identified: 
- Age
- Race
- Myocardial infarction status
- Diabetes mellitus status

#### Covariates
- Demographics: gender, education, marital status
- Clinical: BMI, waist circumference, hypertension, CHD
- Lifestyle: smoking status, alcohol consumption
- Socioeconomic: poverty-to-income ratio
- Health behaviors: sleep time, physical activity, sedentary time

### Research Focus
The goal of this study was to develop and validate a prediction model based on machine learning algorithms for the risk of heart failure in middle-aged and elderly participants with periodontitis.

### Methodologies
#### Data Preprocessing
- Patients with age > 40 years
- Patients with missing data were excluded
- Categorization of variables:
    - smoking status
    - alcohol consumption
    - Diabetes

#### Statistical Analysis
-  Description and logistic regression analysis to achieve nationally representative values
    - The t test was used to compare continuous variables between the 2 groups.
    - The chi-square test or Fisher exact test was used to determine the differences between groups when comparing categorical variables between the 2 groups.
    - Odds ratio (OR) and 95% confidence intervals (CI) were utilized as effect estimates and P < .05 was considered statistically significant. 
- Univariate and multivariate logistic regression analysis to identify the independent risk factors for heart failure 
- R software (version 4.3.0)

#### Machine Learning Approaches 
Machine Learning Models Compared:
1. Logistic regression
2. K-nearest neighbor
3. Support vector machine
4. Random forest
5. Gradient boosting machine
6. Multilayer perceptron

Validation Approach:
- 10-fold cross-validation on training set
- External validation on 2013-2014 dataset
- Performance evaluated using ROC curves and AUC

### Results and Findings
#### Key Outcomes
1. The independent predictors of the risk of heart failure in participants with periodontitis were age, race, myocardial infarction, and diabetes mellitus status.
2. Training set (10-fold cross-validation):
    - K-nearest neighbor: 0.936 (best performing)
    - GBM: 0.927
    - Random forest: 0.889
    - SVM: 0.859
    - Logistic regression: 0.848
    - MLP: 0.666
3. External validation:
    - K-nearest neighbor: 0.949 (best performing)
    - Random forest: 0.933
    - Logistic regression: 0.854
    - GBM: 0.855
    - MLP: 0.74
    - SVM: 0.647
4. Variable importance ranked in descending order:
    - Myocardial infarction
    - Age
    - Diabetes
    - Race

#### Visualizations
- Receiver operating characteristic curve analysis is used in the external validation set to check the performance of each model.
- Tables for demographic information, univariate and multivariate logistic regression analysis


## Prognostic significance of subjective oral dysfunction on the all-­cause mortality

### Dataset Information
- NHANES database 1999-2002
- Total of 7827 participants who completed oral functions data
- Follow-up period: from baseline to death or December 31, 2006

### Variables of Interest
#### Primary Outcome
- All-cause mortality

#### Subjective Oral Dysfunction Components
Three key components assessed via self-reported questionnaire:
- Limited eating ability
- Dry mouth
- Difficult swallowing

#### Covariables
- Socio-demographic: age, sex, race, smoking history
- Medical comorbidities
- Recreational activity
- Biochemistry profiles:
    - Creatinine
    - Alanine aminotransferase
    - Serum fasting glucose
    - Total cholesterol
    - Total calcium
- Muscle measurements:
    - Muscle strength (quadriceps)
    - Appendicular skeletal muscle mass

### Research Focus
To examine the association between subjective oral dysfunction and all-cause mortality in the US population. 

Honorable mention for this paper for a well-done introduction: the different indices to evaluate frailty are well exposed and it is mentioned the longitudinal study in Japan that defined oral frailty as containing 3 or more of 6 characteristics (included the number of natural teeth, tongue pressure, articulatory skill, chewing ability and perceived eating and swallowing difficulties). 

"Each frailty scale focused on different domains such as biological, physical, cognitive and deficit accumulation."

"Oral hypofunction was defined by the Japanese Society of Gerodontology (JSG) including seven components: oral dryness, poor oral hygiene, decreased occlusal force, decreased tongue pressure, reduced tongue-­lips motor function, decreased chewing and swallowing function."

### Methodologies
#### Data Preprocessing
- They excluded individuals who lacked data for covariables
- It appears to be a complete case analysis where they simply excluded participants with missing data on key variables.
- They classified study population into 4 groups:
    - group 1 (without any components of subjective oral dysfunction), 
    - group 2 (with one component of subjective oral dysfunction), 
    - group 3 (with two components of subjective oral dysfunction), 
    - group 4 (with 3 components of subjective oral dysfunction).

#### Study Design
- Cross-sectional observational study

#### Assessment Methods
- Subjective oral dysfunction assessment:
    1. Limited eating ability: "always, very often and often" responses
    2. Dry mouth: "yes" responses
    3. Difficult swallowing: "yes" responses
- Muscle strength: Isokinetic strength testing of right quadriceps
- Muscle mass: Dual-energy X-ray absorptiometry (DEXA)

#### Statistical Analysis
- SPSS version 18
- One-way ANOVA and chi-square test were applied for analysing socio-­demographic characteristics, laboratory variables and medical comorbidities. 
- Kaplan-Meier survival curves
- Cox proportional hazard models to assess the relationship between subjective oral dysfunction and all-­ cause mortality 
- Three covariate-adjusted models:
    1. Model 1: unadjusted
    2. Model 2: adjusted for basic variables
    3. Model 3: fully adjusted model

#### Machine Learning Approaches 
- No Machine Learning algorithms implemented in this research.

### Results and Findings
#### Key Outcomes
- Significant relationship between subjective oral dysfunction and all-cause mortality in fully adjusted model
- Dose-dependent effect: more components of dysfunction associated with worse mortality risk
- HRs in fully adjusted model:
    - Group 2 (one component): 1.269
    - Group 3 (two components): 1.649
    - Group 4 (three components): 3.185
- Limited eating ability inversely associated with muscle strength

#### Visualizations
- Three Kaplan-Meier curves showing cumulative survival classified by each component of subjective oral dysfunction
- Tables showing:
    - Population characteristics
    - Hazard ratios of all-cause mortality
    - Associations between muscle strength/mass and oral dysfunction components


## Paper Title

### Dataset Information
- List of specific NHANES cycles analyzed
- Sample size and demographic information
- Data collection periods

### Variables of Interest
#### Frailty Outcome
- Frailty indices used

#### Variables used

### Research Focus
Detailed description of research questions and hypotheses.

### Methodologies
#### Data Preprocessing
- Data cleaning procedures
- Missing data handling
- Outlier detection and treatment

#### Statistical Analysis
- Statistical methods employed
- Software packages and versions
- Analysis pipelines

#### Machine Learning Approaches 
- Algorithms used
- Feature selection methods
- Model validation techniques

### Results and Findings
#### Key Outcomes
- Major findings
- Statistical significance
- Clinical relevance

#### Visualizations
- Key figures and plots
- Data interpretation
- Meaningful patterns

## Bibliography
```
[1] Faisal F. Hakeem MSc a, b, *, Eduardo Bernabé PhD a, Wael Sabbah PhD a. (2020). Association Between Oral Health and Frailty Among American Older Adults. JAMDA. https://doi.org/10.1016/j.jamda.2020.07.023
```
```
[2] Crystal Marruganti, Giacomo Baima, Mario Aimetti, Simone Grandini, Mariano Sanz, Mario Romandini (2023). Periodontitis and low cognitive performance: A population-based study. J Clin Periodontol. https://doi.org/10.1111/jcpe.13779
```
```
[3] Yicheng Wang, Yuan Xiao, Yan Zhang (2023) A systematic comparison of machine learning algorithms to develop and validate prediction model to predict heart failure risk in middle-aged and elderly patients with periodontitis (NHANES 2009 to 2014). Medicine (Baltimore). 10.1097/MD.0000000000034878
```
```
[4] Zhe-­Yu Yang, Wei-­ Liang Chen (2021) Prognostic significance of subjective oral dysfunction on the all-­cause mortality. Wiley, J Oral Rehabilitation. 10.1111/joor.13281
```

--------------------------------------

## Notes
- Last updated: [11/02/2025]
- Contact: [silvano.quarto@gmail.com]
- Project Status: [fourth paper added]