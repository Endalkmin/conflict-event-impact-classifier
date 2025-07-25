# Predicting Severity of Impact from Conflict Events in Kenya.

![kofa-boyah-St-6SCwofGo-unsplash](https://github.com/user-attachments/assets/0af78136-52f9-4de2-9677-a2dc9196194b)

## Problem Statement
Using historical data from the Armed Conflict Location & Event Data research (ACLED), this research develops a predictive model to categorise conflict incidents in Kenya into four severity levels (Low, Moderate, High, and Critical). By achieving the accuracy, precision, F1-score and confusion matrix the approach assists government agencies, peacekeeping forces and humanitarian organisations in better allocating resources and prioritising response activities.

## 1.  Business Understanding
Kenya has had a lot of protests in recent years, motivated by social, political, and economic issues. These incidents frequently intensify quickly and have different effects on the community. Decision-makers do not currently have access to efficient real-time tools for anticipating possible outcomes.

Objectives :

a) Establish a predictive model that divides conflict incidents into four tiers of severity.

b) Using past ACLED data, to create a Community Impact Score (CIS).

c) Assist stakeholders in allocating resources and setting priorities for response activities.

## 2. Data Understanding
The project makes use of information from the Armed Conflict Location & Event Data initiative (ACLED), which offers comprehensive logs of events connected to conflicts throughout Africa. More than 431,000 records from 1997 to 2025 are included in the raw dataset, with 17,812 events occurring in Kenya alone.

Significant factors consist of:
- Fatalities.
- Actors Involved.
- Event type (Protests, Battles, Explosions/Remote violence, etc.).
- Civilian targeting.
- Narrative descriptions.
- Geographic coordinates.

## 3. Data Wrangling
Here we will work on : 
- Filtering Kenya-specific data (17,812 events).
- Handling missing values (imputation and column dropping).
- Text data cleaning (removing special characters, lowercasing).
- Feature engineering:
  
      -Combined actor columns.
  
      -Created Community Impact Score (CIS).
  
      -Mapped CIS to severity levels.
- Date parsing.

which ensures that we have a clean, structured, and suitable format for analysis and modeling.

## 4. Exploratory Data Analysis(EDA)

The graph illustrates the distribution of conflict severity levels in Kenya, with the biggest number of occurrences falling under the "Low" severity category, followed by "Moderate," "High," and "Critical." This suggests that although disputes occur frequently, the majority are not very serious, though a significant number do.
<img width="790" height="490" alt="Distribution of Conflict Severity levels" src="https://github.com/user-attachments/assets/fb759102-f542-4a61-82e9-d590b55cd3d0" />

Violence and battles drive most high-severity conflicts, while protests and strategic events typically remain low-risk. These patterns validate the Community Impact Score's severity weightings.
<img width="1189" height="590" alt="Event type vs Severity level" src="https://github.com/user-attachments/assets/3cec46e1-4873-468d-880b-79dc9c7e15df" />

Mandera and Garissa show the highest fatalities, indicating these regions experience the most lethal conflicts. Urban areas like Nairobi and Mombasa also appear prominently, reflecting both political and intercommunal violence.
<img width="1190" height="590" alt="Fatalities by Location" src="https://github.com/user-attachments/assets/ebc445d9-8821-4450-9628-617576d07022" />

Conflict severity fluctuates over time, with noticeable spikes during election years (e.g., 2007, 2017). This pattern underscores the link between political instability and increased violence.
<img width="1190" height="590" alt="Severity level Trends over Time" src="https://github.com/user-attachments/assets/762de25a-812f-4bbf-99ba-a0ca962d372c" />


## 5. Data Processing
To prevent data leaking, only features that were accessible prior to or during a conflict occurrence were employed to prepare the data for modelling.  These comprised important numerical and categorical information (e.g., year, month, latitude, longitude) as well as event type, actors, and location.

 To ensure class balance, stratified sampling was used to divide the data into training and testing sets.  Numerical features were standardised for consistency, while categorical features were one-hot encoded.

 SMOTE was used to improve model fairness and oversample minority classes in order to address class imbalance in the target variable (severity_level).

## 6. Modelling and Evaluation

The project framed conflict severity prediction as a multi-class classification problem with four levels: Low, Moderate, High, and Critical. Several models were tested:

Logistic Regression: Served as a reliable baseline.

Random Forest & XGBoost: Delivered improved performance, especially on imbalanced classes.

Voting Ensemble: Combined Logistic Regression, Random Forest, and XGBoost, achieving the highest overall accuracy of 86%.

The Community Impact Score (CIS) was engineered to label severity, and class imbalance was addressed using SMOTE. The ensemble model consistently outperformed others in predicting both frequent and rare classes, making it ideal for early warning systems.


## 7. Conclusion

This project demonstrated that conflict event severity in Kenya can be effectively predicted using historical ACLED data. By creating a Community Impact Score and categorizing severity into four levels, a robust multi-class model was developed. The best results came from XGBoost and a Voting Ensemble, both achieving 86% accuracy and strong performance on harder-to-predict classes like "Moderate" and "Critical."

Key factors influencing severity included event type, civilian targeting, and primary actors. Visual analysis showed a clear link between severe events and political cycles, with hotspots in Nairobi, Kisumu, and Turkana.

## 8. Recommendations

Deploy Predictive Models: Integrate the XGBoost or Ensemble model into early warning systems to support real-time conflict risk assessment.

Prioritize High-Risk Areas: Focus intervention and monitoring efforts on regions with recurring severe conflict events.

Enhance Feature Set: Incorporate contextual data like socioeconomic indicators and social media signals to improve model performance.

Improve Minority Class Recall: Explore advanced techniques such as cost-sensitive learning or data augmentation to better detect rare but critical events.

## Contributors:

| Name             | GitHub Profile |
|:-----------------|:---------------|
| Endalkachew Dessalegne     | https://github.com/Endalkmin/ |
| Danton Kipngeno            |  |
| Zeena Karari               |  |
| Noel Seda                  | https://github.com/Noel-cyber |
| James Gatonye              |  |
