
# Bank Marketing Prediction using Azure Machine Learning

## Project Overview

This project focuses on building and comparing two machine learning pipelines using Azure Machine Learning to predict whether a client will subscribe to a term deposit. The dataset used is the Bank Marketing dataset.

Two approaches were implemented. The first approach uses HyperDrive with Logistic Regression. The second approach uses Automated Machine Learning (AutoML) to automatically select the best model.

The objective is to evaluate both approaches and register the best-performing model.

---

## Project Architecture

<p align="center">
  <img src="images/Diagram.png" width="500"/>  
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

Used to optimize a Logistic Regression model by exploring different combinations of hyperparameters. A parameter sampling strategy (Random Sampling) was applied to efficiently search the hyperparameter space and increase the likelihood of identifying an optimal configuration.

An early termination policy (BanditPolicy) was implemented to stop underperforming runs early. This reduces computational cost and allows resources to be allocated to more promising experiments, improving overall efficiency.

The following hyperparameters were tuned:
- Regularization parameter (C)  
- Maximum number of iterations (max_iter)

This approach balances exploration and efficiency, making HyperDrive suitable for controlled and scalable model optimization.

The results of the HyperDrive experiment are shown below:

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

## Resource Management

To ensure efficient use of cloud resources and avoid unnecessary costs, the compute cluster used in this project was deleted after completing all experiments. This follows best practices in cloud-based machine learning by managing resource lifecycle effectively.

----

## Conclusion

HyperDrive improved the performance of the Logistic Regression model through hyperparameter tuning. However, AutoML identified a more optimal model, XGBoost, which achieved better overall performance.

The final model was successfully registered and is ready for deployment.

---

## Future Improvements 

Future improvements could include:

- Applying advanced feature engineering techniques (e.g., interaction features and feature scaling) to enhance model performance  
- Expanding the HyperDrive search space and experimenting with different sampling strategies to achieve better optimization  
- Implementing more robust cross-validation techniques (e.g., k-fold cross-validation) to improve model generalization  
- Exploring advanced ensemble methods such as stacking and blending beyond AutoML defaults  
- Deploying the model as a web service and monitoring performance over time to detect data drift and ensure model reliability in production  

---

## Author:

# Rawan Alhammad
Azure Machine Learning Project 

