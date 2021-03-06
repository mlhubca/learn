 # Machine Learning Batch Deployment
 
 ![](https://github.com/mlhubca/lab/blob/master/tennis/images/tennis.jpeg)
 
## Introduction

In this tutorial, I will show you how to deploy your model through batch deployment. I am using the model created in the tennis exercise
for this tutorial.

## Start

1. First thing to do is open up the original data excel file (tennis.csv). When you open it, what you want to do is remove all the data except for the header and input your own data (except for the play column). If you want you can remove the play column header to make the final document look a little better. 

2. Next thing you want to do is save it as a new file, as an example PlayTennisData and make sure that the file type is csv (Comma Delimited File Type). 

3. Next what you want to do is create a new excel document. Leave this document blank (because anything on it will be overwritten) and save it also as a csv file (an example name; PlayTennisResults). 

4. Next open your project Play Tennis and add the two new csv files into the assests folder (done through pushing the file button and drag and drop the files).

5. Next go to your assets and open up your model. From there click "Deployments" and add a new deployment. 

6. For this deployment select the "Batch Prediction". Give the deployment any name and description that you want and select a spark service.

7. Next scroll down and click the button "Select Source". From there select the file "PlayTennisData.csv" and push the "Select" button on the bottom right.

8. Next what you want to do is push the "New Connections" text in the paragraph below the Spark Service section. From there you want to select the Cloud Object Storage service. Here you can enter a name for it on the left then enter the following details. To get all these details you want to hover over the 'i' icon beside each detail and follow the instructions. Once you do this push the "Create" button on the bottom left. 

9. Once done, go back to the deployment creation page and push the "Select Target" button. From here you push the "Connections" tab and click on your newly created connection. Click the next folder then select the "PlayTennisResults.csv" file, then push the "Select" button on the bottom right.

10. Beneath the "Select Target" button, enter a name that you will give to the results, but make sure you add ".csv" at the end (as an example, "results.csv"). 

11. Now push save on the deployment creation page. This will bring you to all of your deployments for the project. From here refresh the page until the status of your new deployment goes to "COMPLETED".

12. Congrats your deployment is done and you can now look at the results. To look at the results open up the bar on the left by pushing the 3 horizontal lines on the top left. Next when the bar opens up push the "Dashboard" button. 

13. From here scroll down to "Services" and select "cloud-object-storage-id". Next under buckets, select your project's bucket (it has the project's name before the 'donotdelete' and all the numbers).

14. Now find your "Results.csv" file and click the 3 dots beside it and click download.

15. Once you open it, there will be the original data that you created, but also there will a "nodeADP_class" column which says the prediction of the row based on your model. 

16. Thats it, you deployed your model using a batch deployment. Thanks for reading. :-)
