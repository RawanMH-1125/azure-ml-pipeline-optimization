
# Bank Marketing Prediction using Azure Machine Learning

## Project Overview

This project focuses on building and comparing two machine learning pipelines using Azure Machine Learning to predict whether a client will subscribe to a term deposit. The dataset used is the Bank Marketing dataset.

Two approaches were implemented. The first approach uses HyperDrive with Logistic Regression. The second approach uses Automated Machine Learning (AutoML) to automatically select the best model.

The objective is to evaluate both approaches and register the best-performing model.

---

## Project Architecture

<p align="center">
  <img src="images/Digram.png" width="500"/>  
</p>

---

## Compute Setup

A CPU-based compute cluster was created and used to execute all experiments in Azure Machine Learning.

<p align="center">
  <img src="images/cpu_cluster.png" width="600"/>
</p>

---

## Data Preprocessing

The following preprocessing steps were applied to the dataset:

- Label encoding for categorical variables  
- Feature scaling using StandardScaler  
- Splitting the dataset into training and testing sets  

---

## HyperDrive Pipeline

A Logistic Regression model was trained using HyperDrive to optimize hyperparameters.

The following parameters were tuned:

- Regularization parameter C  
- Maximum number of iterations  

The tuning strategy included random sampling and early stopping to efficiently explore the parameter space.

Results are shown below:

<p align="center">
  <img src="images/hyperdrive_metric.png" width="800"/>  
</p>
<p align="center">
  <img src="images/hyperdrive_summary.png" width="800"/>  
</p>

The best model achieved an accuracy of approximately 0.9138.

---

## AutoML Pipeline

AutoML was used to automate model selection and training. Multiple algorithms were evaluated, and the best-performing model was selected automatically.

The best model identified was XGBoost.

Results are shown below:

<p align="center">
  <img src="images/automl_best_model.png" width="700"/>  
</p> 

The best model achieved an AUC of approximately 0.945.

---

## Model Evaluation

The models were evaluated using several performance metrics including accuracy, precision, recall, and AUC.

Evaluation results are shown below:

![AutoML Metrics](images/automl_metrics.png)  
![Additional Metrics](images/automl_metrics1.png)

The results demonstrate strong model performance with good balance between precision and recall.

---

## Model Comparison

HyperDrive achieved an accuracy of approximately 0.913.  
AutoML achieved a higher performance with an AUC of approximately 0.945.

Based on these results, the AutoML model was selected as the best model.

---

## Model Registration

The best AutoML model was registered using MLflow.

<p align="center">
  <img src="images/registered_model.png" width="700"/>  
</p> 

Model details:

- Model name: automl-best-model  
- Version: 1  
- Type: MLflow  

---

## Conclusion

HyperDrive improved the performance of the Logistic Regression model through hyperparameter tuning. However, AutoML identified a more optimal model, XGBoost, which achieved better overall performance.

The final model was successfully registered and is ready for deployment.

---

## Future Work

Possible improvements include deploying the model as a real-time endpoint, performing feature importance analysis, and optimizing the model further based on business requirements.


## Author:

# Rawan Alhammad  
Azure Machine Learning Project 

