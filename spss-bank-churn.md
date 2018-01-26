
## Creating a model using SPSS Modeler on DSX

*Machine learning flow is a graphical representation of data, by using the Flow Editor to prepare or shape data, train or deploy a model, or transform data and export it back to a database table or file in object storage.*

![](https://github.com/mlhubca/lab/blob/master/bank-churn/images/bank-churn-flow.png)
  
**Technology:** SPSS Modeler, feature selection, auto classifier, data audit, field operations, data visualization 

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

#### Creating a new flow
1) Add a new flow using `New flow` button or from the "Add to project" dropdown, select "SPSS Modeler flow"
2) On the Create Flow page,
    - Specify a name, e.g. `Bank Churn Flow`
    - **Select `IBM SPSS Modeler` Runtime**
    - Click "Create Flow"

#### Loading data
3) Drag and drop node `bank-churn.csv` from the Files list to the flow
4) Click Palette icon (first icon on the toolbar) to show node palette

#### Checking data quality
5) Add `Data Audit` node from the `Outputs` list on the palette
6) Connect file `bank-churn.csv` node to `Data Audit` node
7) Run `Data Audit` node to generate output

#### Filtering data
8) Add `Filter` node from the `Field Operations` list on the palette
9) Connect file `bank-churn.csv` node to `Filter` node
10) Open `Filter` node, select columns `CUST_ID`, `TwitterID` and `CHURN_LABLE` (to be filtered)

#### Setting metadata
11) Add node `Type` node from the `Field Operations` list on the palette
12) Connect file `Filter` node to `Type` node
13) Open `Type` node, add all columns to the Types list
14) Locate `CHURN` field, and
     - Change Measure from `Range` to `Flag`
     - Change Role from `Input` to `Target`

#### Selecting features
15) Add `Feature Selection` node from the `Modeling` list on the palette
16) Connect `Feature Selection` node to node "Type" (note that the Feature Selection node name is being changed to CHURN)
17) Run node `CHURN` (Feature Selection). When the execution completes, a new model node `CHURN` is created 
18) Add `Data Audit` node from the `Outputs` list on the palette
19) Connect the new model node `CHURN` to `Data Audit` node
20) Run `Data Audit` node to generate output

#### Splitting data
21) Add `Partition` node from the `Field Operations` list on the palette
22) Connect the new model node `CHURN` to `Partition` node
23) Open `Partition` node, change the Training and Test partition to the ratio of 80/20.

#### Building model - Auto classifier
24) Add `Auto Classifier` node from the `Modeling` list on the palette
25) Connect `Auto Classifier` to node `Partition`(note that the Auto Classifier node name is being changed to CHURN automatically)
26) Run node `CHURN` (Auto Classifier). When the execution completes, a new model node `CHURN` is created automatically. 

#### Aanlyzing model performance
27) Add `Analysis` node from the `Outputs` list on the palette
28) Connect the new model nodel `CHURN` to `Analysis` node
29) Run `Analysis` node to generate output

#### Executing the flow
30) Run the whole flow by clicking the `Run` button on the toolbar
