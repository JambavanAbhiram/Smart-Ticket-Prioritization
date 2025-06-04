# Smart-Ticket-Prioritization

This project demonstrates a model that predicts the priority of any IT ticket based on the reassignment count, reopen count, status of the SLA, impact, urgency and a few other parameters that determine the priority of the ticket. The model is tested using two different algorithms, Naive Bayes and the XGBoost to compare the accuracy of the data. The sailent features of the model are furthered explained below. 

## Dataset
The dataset used to train this model has been borrowed from Kaggle. **Source [IT_incident_log_Dataset](https://www.kaggle.com/datasets/shamiulislamshifat/it-incident-log-dataset)

## Preprocessing
The dataset contained 141712 tuples, and 36 attributes before preprocessing. It also has a lot of string values. 
1. Dropped the irrelevant features and reduced the number of attributes to **23** meaningful columns.
2. Cleaned and handled the string values using **lambda function** and the **regular expressions**.
3. Handled categorical variables with limited unique values using **Label Encoding**.
4. The missing values are handled by **median imputation**.
5. The data was split, taking 20% of the data as test size.
6. Applied **SMOTE** to synthetically balance under-represented ticket classes.

## Modeling
Considering the size of the dataset, I preferred Machine Learning approaches to solve the problem. Also keeping the biasness in the data in mind, I opted SMOTE algorithm for handling the class imbalance.
### Naive Bayes
1. As the problem is categorical multiclass classification, Naive Bayes was chosen.
2. Implemented Gaussian Naive Bayes and achieved an accuracy of 91.63%.
### XGBoost
1. As the data is structured and well-defined, XGBoost was chosen.
2. Implemented XGBoost classifier with softprob objective and achieved an accuracy of 99.9%.

## Observations 
### Real-world Challenges
Perfect predicitions were not achievable despite the SMOTE application as the data lacks semantic context and noisy. 
**Impact:** The model struggled to coorectly predict 'High' and 'Low' priority tickets.
### Proposed solution
1.  Explore and implement Word Embeddings (e.g, BERT, GloVe) and implement text-based features.
2.  Use **cost-sensitive learning** or **focal loss** to handle imbalance without over-sampling.
3.  Add interpretability tools (e.g., SHAP) for understanding feature impact.

## Installation

``` bash
git clone https://github.com/JambavanAbhiram/smart-ticket-prioritization.git
cd smart-ticket-prioritization
pip install -r requirements.txt
   
