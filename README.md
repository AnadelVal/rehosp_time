# Objective: 
Prediction of time between rehospitalizations of patients registered in MIMIC-III database, based on the severity of the illness, the diagnoses, the prescriptions and the doctor notes. 

# Context: 
The EHR dataset is organized by hospitalization, not by patient, assuming independence between items. The distribution of the admission and discharge times are described in 58976 hospitalizations of 46520 patients. Not all of them contain doctor notes, resulting in 39166 hospitalizations of 30423 patients for the model design, and 39641 rows. 

# Methodology: 
The severity depends on the number of admissions, number of ICU stays and the outcome of the illness (alive or death). There are two possible values: Low and High.
The diagnoses are originally expressed in ICD9 code. It is considered that the same hospitalization can be diagnosed with several illnesses. Only the most frequent diagnoses are considered in the model, including Rheumatoid Arthritis.
The prescriptions administered in each admission are also filtered by the most frequent values in order to avoid complexity.
Both the diagnoses and prescriptions have been encoded and transformed to columns following the one-hot encoding technique.
The doctor notes contain information about the clinical history of the patients and the information at the time of discharge. These notes have been modeled implementing Word2Vec technique, transforming the text to vectors of 96 elements. These vectors, in turn, have also been transformed to columns of the dataset. 
The models are trained based on cross-validation technique. The labeled data conform the 23.71% of the available data, using 80% for training.
The models implemented are regressors: Random Forest Regressor, Bayesian Ridge, Support Vector Regression and Decision tree regressor.

