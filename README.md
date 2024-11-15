# Classification Machine Learning Modeling for Heart Attack Prediction

## Objective

The goal of this project is to build machine learning models to determine which patients have a higher likelihood of a heart attack given certain health characteristics.
By utilizing these models, patients can learn whether they are at a high risk to help identify potential lifestyle changes. Doctors can also use these models to help validate or cross-reference any suspicions of potential heart attack or coronary artery disease by putting in the patients' medical information and running the model against the point. We will use several different machine learning models, and use the best of them to find which features are the biggest determinants in predicting heart attack.

## Dataset

The data used is provided by Kaggle, titled 'Heart Attack Analysis and Prediction Dataset'. It provides 13 different health factors such as age, sex, cholesterol, etc., and also an output variable which indicates whether the individual was at a raised risk for heart attack or not. I have provided more detailed descriptions of each individual health point down below in the 'About this Dataset' portion of the notebook. The link to the dataset can be found here: \
https://www.kaggle.com/datasets/rashikrahmanpritom/heart-attack-analysis-prediction-dataset

### About this Dataset

age: Age of the patient

sex: Sex of the patient (0 = female, 1 = male)

cp: Chest pain type (0 = Typical angina, 1 = Atypical angina, 2 = Non-anginal pain, 3 = Asymptomatic)
*angina is defined as a type of chest pain caused by reduced blood flow to the heart

trtbps: Resting blood pressure (in mm Hg)

chol: Cholesterol in mg/dl

fbs: 1 (True) if fasting blood sugar > 120 mg/dl, 0 (False) if not

restecg: Resting electrocardiographic results (0 = normal, 1 = ST-T wave normality, 2 = Left ventricular hypertrophy)

thalachh: Maximum heart rate achieved

oldpeak: Defined as 'ST depression induced by exercise relative to rest'

slp: Slope

caa: Number of major vessels

thall: Thallium stress result (0 = Normal blood flow, 1 = Abnormal blood flow during exercise, 2 = Low blood flow at rest, 3 = No thallium visible)

exng: Exercise induced angina (1 = Yes, 0 = No)

output: Target variable to predict if a person is prone to heart attack or not (1 = More prone, 0 = Not)

### Findings from Data Analysis

1. Amongst the numerical variables, the only significant finding was that distribution of age for those not likely to be prone to heart attack was higher than the distribution of age for those who were. This is intuitive, as people with higher probability for heart attack likely have accompanying negative health factors, leading to a lower average age.

2. There were twice as many males than females in this dataset. Females were 3.5x more likely to be prone to heart attack than not in this dataset, whereas males were more even this regard.

3. Individuals with typical angina were 2.5x less likely to be prone to heart attack than not. However, those with anything but typical angina (atypical angina, non-anginal pain, asymptomatic) were very likely to be prone to heart attack.

4. Having a value of 1 on the resting electrocardiographic results, signifying ST-T wave abnormality, or a value of 2 for slope, is a big indicator of being prone to heart attack.

5. Individuals with at least 1 major vessel are far less likely to be prone to heart attack than those with 0 major blood vessels.

6. Counterintuitively, those with a value of 3 in the Thallium stress test (no thallium visible) are less prone to heart attacks than individuals with low blood flow during rest. This may be because those with no thallium visible indicates that they have already had a prior heart attack. Moreover, we see that there are virtually no individuals with scores of 0. This means that the vast majority of individuals in this dataset have some sort of coronary artery disease.

7. Another counterintuitive finding was that those without exercise-induced angina are almost 2.5x more likely to be prone to heart attacks, whereas those that do have it are 4x less likely to have a heart attack.


### Evaluation

While all three models were able to beat the baseline score provided by the DummyClassifier(), it is clear through the test accuracies and confusion matrices that SVM had the best performing model, with KNN being a close second. Because of this, we will use these two models and drop the decision tree algorithm to determine the most important features, cross-referencing them against each other to find which health characteristics are most crucial in deciding whether an individual is prone to heart attacks.

# Summary of Findings

According to the top 5 features found by the KNN and SVM models, they have both identified oldpeak (ST depression induced by exercise relative to rest) and thalachh (maximum heart rate achieved) as the most impactful features for predicting likelihood of heart attack. Both models also identified chest pain and caa (number of major vessels), although they differ on which category within each factor is most indicative of heart attack likelihood. 

Additional factors that the two models chose were exercise-induced angina and age from the SVM and KNN model respectively. These are also intuitive factors, as older individuals are at more risk to have heart-related issues, and exercise-induced angina is a warning sign of coronary heart disease. 
