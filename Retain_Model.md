# Continuous learning and model evaluation


Because model deployment is not a one-time event, you can use IBM Data Science Experience to retrain a model with new data. To do this, you use the IBM Watson™ Machine Learning continuous learning system, which provides automated monitoring of model performance, retraining, and redeployment to ensure prediction quality.


## Prerequisites
Before you begin to set up continuous learning model evaluation, depending on the type of data and model, you must have the following resources:

- a model
- an IBM Watson Machine Learning instance
- an Apache Spark service
- a Db2 Warehouse on Cloud instance to store the feedback data for batch predictions


**Procedure**

## 1. Load datasets

1) Download the following two datasets to your local machine. (Right click and select `Save Link as...`)
  - [drug_train_data_2.csv](https://raw.githubusercontent.com/mlhubca/learn/master/data/drug_train_data_2.csv)
  - [drug_feedback_data_2.csv](https://raw.githubusercontent.com/mlhubca/learn/master/data/drug_feedback_data_2.csv)

2) Sign in to IBM Data Science Experiece (DSX), and create a new project.
3) Load dataset `drug_train_data_2.csv` to the project.

## 2. Set up feedback data store

To retrain data, you must create a feedback data store. To send new records to the feedback store you must define a data connection by using Db2® Warehouse on Cloud, which is currently supported as a feedback data store for batch predictions. If the feedback table does not exist, the service creates it. If the table exists, the schema is verified to match that of the training table.

1) Create a Db2 Warehouse on Cloud instance if you don't have one already
  - 



## 3. Create a model using model builder



## Set up continuous learning model evaluation

You can create a performance monitoring system for your predictive models. Create an evaluation instance and then define metrics and triggers for the automatic retraining and deploying of the new model.

**Optional**: While you can use the following steps, and the user interface that they explain, to upload feedback data and kick off evaluation, you can also call the available continuous learning REST API end-points directly to provide feedback data and kick off evaluation activities. For more information about the REST APIs, see REST API for Spark and Python models and REST API for SPSS models. You can integrate feedback APIs directly within your application, rather than performing model evaluation through the use of the following steps.

Open a project and select a model.
From the Evaluation tab, in the Performance Monitoring section, click Edit configuration.
Select a Spark service.
Select a prediction type. If the type is known, it is automatically selected, otherwise in the Prediction type box select the type.
In the Metric details section, you can choose the specific metrics that you want to track, and you can enter threshold values that can be used to trigger automatic retraining and redeployment activities
Feedback data connection, click Select source.
On the Select feedback data source page, choose values for the Connection, Schema, and Table options.
In the Record count required for re-evaluation box, type the minimum number of new records to trigger retraining or leave blank to use the default value of 1000.
In the Auto retrain box, select one of the following options:

To start automatic retraining whenever model performance is below the threshold that you set, select when model performance is below threshold.
To prohibit automatic retraining, select never.
To start automatic retraining regardless of performance, select always.
In the Auto deploy box, select one of the following options:

To start automatic deployment whenever model performance is better than the previous version, select when model performance is better than previous version.
To prohibit automatic deployment, select never.
To start automatic deployment regardless of performance, select always.
Click Save.

Click Add feedback data, select a data file, and click Open.
Click Begin evaluation.
After automatic evaluation and retraining begins, a chart appears with the updated model performance metrics. You can use the chart controls to switch metrics or to view the results as a chart or as a table.

