# Brain health assessment in cardiometabolic diseases

Hi everyone, I'm a Researcher and Data Scientist at the Healthcare hospital in Bari. I'm working on the PNRR project "Brain health assessment in cardiometabolic diseases: impact of frailty and biomarkers on healthcare management". I perform statistical analysis and data science initiatives to uncover patterns in brain health and cardiometabolic disease data.

This would be a readme file about some interesting and useful readings about some topics I'm working on during my job:

1. "Blood biomarkers of Alzheimer’s disease in the community: Variation by chronic diseases and inflammatory status" [here](https://alz-journals.onlinelibrary.wiley.com/doi/full/10.1002/alz.13860)
2. "Explainable machine learning model for pre‐frailty risk assessment in community‐dwelling older adults" [here](https://onlinelibrary.wiley.com/doi/full/10.1002/hcs2.120)

## Explainable machine learning model for pre‐frailty risk assessment in community‐dwelling older adults

This paper presents an innovative machine learning framework called **PACIFIC** (interPretable ACcurate and effICient pre-FraIlty Classification) to assess the risk of pre-frailty in community-dwelling older adults. This study, based on data from the China Health and Retirement Longitudinal Study (CHARLS), analyzed 3,141 adults aged 60 years and older.
The authors have well represented the framework in figure 1 which I will try to summarize as follows.

(a) Dataset:
- Show the data stream from the CHARLS Dataset
- Data is organized into seven key dimensions:
    1. Laboratory Measurements 
    2. Physical Factors 
    3. Demographics 
    4. Health Behaviors 
    5. Comorbidity and Medical Histories 
    6. Healthcare Service Utilization 
    7. Environmental Factors
- Selection of features is done through literature reviews and expert consultations
- Output is labelled using the Physical Frailty Phenotype (you can find it [here](https://en.wikipedia.org/wiki/Frailty_syndrome)).

(b) Model:
- Shows two main components:
    1. Recursive Feature Elimination (a LighGBM, with fast training and high accuracy, allows thme to obtain 57 features from itial 80 ones)
    2. Staking-CatBoost Distillation Module (with a compromise between predictive power and inference time; moreover very efficienct in handling high cardinal features)
        - They first trained several different tree-based models with k-fold bagging as base model,
        - They used Random Search with 100 iterations and 5 fold cross-validation to find best hyperparameters for each model,
        - They stacked them using ensemble selection,
        - The stacking model is distilled into a CatBoost model

(d) Interpretation of the pre-frailty classifier:
- For eXplainability module, they used Tree Explainer, SHAP (SHapley Additive exPlanations) values, SAGE (Shapley Additive Global Explanation) values.
- View how the model interprets and classifies risks
- Shows the global importance of different features
- They found out that the living city, BMI, and peak expiratory flow (PEF) were the three most significant contributors to the risk of pre‐frailty.

(e) Pre-frailty Risk Score:
- They also presented individual explanation with an example of Pre-frailty Risk Score Calculator
- The output value is the risk score for the individual. The base value is the mean risk score.

The PACIFIC framework's explainability approach offers several key advantages for both clinical practice and research:
1. Provides transparent and interpretable risk assessments
2. Enables clinicians to understand the specific factors contributing to an individual's pre-frailty risk
3. Supports evidence-based decision making through clear visualization of risk factors.
4. Quantifies the relative importance of different risk dimensions
5. Allows for targeted intervention strategies based on individual risk profiles
6. Enables monitoring of intervention effectiveness through clear metrics
7. Provides insights into population-level risk factors

This comprehensive approach not only improves the accuracy of pre-frailty risk assessment but also makes the results actionable and meaningful for both healthcare providers and patients, bridging the gap between complex machine learning models and practical clinical application.

## Predicting mortality and re-hospitalization for heart failure: a machine-learning and cluster analysis on frailty and comorbidity

This paper presents a comprehensive analysis using machine learning techniques and cluster analysis to predict adverse outcomes in older adults with heart failure, with a particular focus on integrating frailty and comorbidity assessments. The study, conducted at a tertiary care center in Italy, analyzed 571 patients aged 65 years and older who were discharged after acute decompensated heart failure (ADHF).

(a) Study Design and Data Collection:

- Single-center, prospective study of patients discharged from a geriatric unit with diagnosed ADHF
- All patients underwent a comprehensive geriatric assessment (CGA) at hospital admission
- Key assessments included:
    1. Cognitive evaluation using Short Portable Mental Status Questionnaire (SPMSQ)
    2. Basic (ADL) and instrumental (IADL) activities of daily living
    3. Comorbidity burden evaluated through Charlson Comorbidity Index (CCI)
    4. Frailty degree assessed using Clinical Frailty Scale (CFS)
    5. Blood tests including creatinine and brain natriuretic peptide (BNP)
- Primary **outcome** was a composite of re-hospitalization for heart failure or all-cause death within six months following discharge.

(b) Statistical Analysis Approach:

- Cox Regression Analysis:
    - Identified clinical and biochemical factors associated with 6-month mortality or re-hospitalization
    - Univariate and multivariate analyses revealed that BNP, CFS, and CCI were independent determinants of adverse outcomes
    - CFS showed stronger predictive capacity (AUC 0.702) compared to CCI (0.581) and BNP (0.597)
- Random Forest Analysis:
    - Used for feature selection with 70% training and 30% testing split
    - Identified the most important predictors of adverse outcomes
    - BNP (importance value 23.10), age (20.65), CFS (19.82), CCI (12.53), and creatinine (9.13) emerged as the most influential predictors
    - Achieved an impressive out-of-bag error rate of only 2.26%
- K-means Clustering:
    - Applied to stratify patients based on frailty (CFS), comorbidity burden (CCI), and BNP levels
    - Used silhouette approach to determine the optimal number of clusters (four)
    - Created distinct phenogroups with different risk profiles
    - Verified results with hierarchical agglomerative clustering as a secondary analysis

(c) Cluster Phenogroups Identified:

- Cluster 1 (Very Frail)
- Cluster 2 (Pre-frail with Low BNP)
- Cluster 3 (Pre-frail with High BNP)
- Cluster 4 (Non-frail):

(d) Clinical Implications:

- Frailty assessment using CFS provides substantial prognostic value beyond traditional risk factors
- The integration of frailty, comorbidity, and BNP levels allows for more targeted risk stratification
- Machine learning approaches can identify distinct phenotypes among older heart failure patients
- The identified clusters demonstrate significantly different risk profiles that could guide personalized care:
    - Cluster 1 and 3 patients might benefit from more intensive monitoring and support
    - Cluster 2 patients (pre-frail) could potentially benefit from interventions to improve functional status
    - Cluster 4 patients have relatively good prognosis with standard care

This study demonstrates the value of incorporating frailty assessment into heart failure risk models and shows how machine learning techniques can identify clinically meaningful patient subgroups with different risk profiles. The findings suggest that tailoring treatment strategies based on these phenotypes could potentially improve outcomes in older adults with heart failure.