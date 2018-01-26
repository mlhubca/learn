## Creating a model using DSX model builder

*The model builder uses the power of Watson Machine Learning to automatically prepare data and build models.*

**Technology**

Watson Machine Learning, Auto data preparation (ADP), Cognitive Assistant for Data Scientists (CADS)

![](https://github.com/mlhubca/lab/blob/master/bank-churn/images/bank-churn-auto-model.png)

### Prerequisites

1. Sign up to IBM Data Science Experience (DSX): https://datascience.ibm.com/
2. Sign in to DSX
3. On DSX, create a new project
    - Click `Projects`, and select `View All Projects`
    - Click the `New` button to create a new project
    - On the `New Project` page, input `Bank Churn` as the project name
    - In the `Target container` field, input `churn` as the container name
    - Click the `Create` button
4. Download dataset `bank-churn.csv` from Github
    - Use a new browser tab to access dataset: https://github.com/mlhubca/lab/blob/master/bank-churn/bank-churn.csv
    - Right-click the `Raw` button on the toolbar, and select `Save Link As...` or `Save Content As...` (depending on your browser)
5. Upload dataset `bank-churn.csv` to your project
    - On DSX, open your project
    - Click the `Add to project` dropdown and select `Data asset` from the dropdown menu
    - On your right-hand panel, select the `Load` tab
    - Drop file `bank-churn.csv` to the box or browse file `bank-churn.csv` and add the file to the project


**Steps**

1) Add a new model using `New model` button or from the `Add to project` dropdown, select `Model`
2) On the `New model` page
    - Specify a model name, e.g. Bank Churn Model
    - Select a Machine Learning Service. 
       *If you don't have a machine learning service, follow the instructions to provision a machine learning service. Press the `Reload` button after you provision a new machine learning service*
     - Select a Spark Service or use the default service
     - Use the default `Automatic` method
     - Click `Create` button
3) In the `Select Data` stage, select data asset `bank-churn.csv`
4) In the `Train` stage, 
     - Select `CHURN (Integer)` as the Label col
     - Select `All (default)` as the Feature columns
     - Select technique `Binary Classification`
     - Use the default Validation split (Train: 60, Test: 20, Holdout:20)
5) In the `Evaluate` stage, save the model
6) Review the model details
7) On the Deployments tab, add an Online deployment, specify a name as `Bank Churn Online`
8) View the details of the online deployment



## Exercise 4 (Optional): Creating a model using model builder in manual mode

*The model builder in manual model allows you to select and evaluate multiple machine learning models*

![](https://github.com/mlhubca/lab/blob/master/bank-churn/images/bank-churn-model.png)

**Steps**

1) Add a new model using `New model` button or from the `Add to project` dropdown, select `Model`
2) On the `New model` page
    - Specify a model name, e.g. Bank Churn Model
    - *Select a Machine Learning Service. If you don't have a machine learning service, follow the instructions to provision a machine learning service. Press the `Reload` button after you provision a new machine learning server*
     - Select a Spark Service or use the default service
     - Use the default `Manual` method
     - Click `Create` button
3) In the `Select Data` stage, select data asset `bank-churn.csv`
4) In the `Train` stage, 
     - Select `CHURN (Integer)` as the Label col
     - Select the following columns as the Feature columns (excluding CUST_ID, TwitterID, EDUCATION_GROUP and CHURN_LABEL columns) :
     SEX (String), 
     AGE (Integer), 
     EDUCATION (Integer), 
     INVESTMENT (Integer), 
     INCOME (Integer), 
     ACTIVITY (Integer), 
     YRLY_AMT (Decimal), 
     AVG_DAILY_TX (Decimal), 
     YRLY_TX (Integer), 
     AVG_TX_AMT (Decimal), 
     NEGTWEETS (Integer), 
     STATE (String)
     
     - Use suggested technique `Binary Classification`
     - Use default Validation split (Train: 60, Test: 20, Holdout:20)
     - Click `Add Estimators` to add following estimators (machine learning algorithms)
        - Logistic Regression
        - Decision Tree Classifier
        - Random Forest Classifier
5) In the `Evaluate` stage, select the estimator that has the best performance and save the model
6) Review the model details


