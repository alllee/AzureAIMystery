# Instructions for creating a logic app to analyse suspect statements

## Getting the suspect statements into your subscription

#### 1. Downloading the suspect statements

Prior to designing a logic app to analyse the suspect statements we first need to upload the statements into your Azure subscription. 
To Download the suspect statement files click here: [Suspect Statements](https://github.com/alllee/Cluedo/blob/main/LogicApp/Suspect%20Statements/SuspectStatementsZip.zip) and then click the download button.

#### 2. Uploading the suspect statements

Once downloaded, you will need to upload the files to an Azure storage account in your subscription. There are a couple of options to upload the suspect statements.

##### Upload files via Azure Portal

* Head over to your storage account resource in the Azure Portal. It should be called "mysterystorage<youralias>"
* Navigate to Data Storage > Containers
<p align="center">
  <img src="https://user-images.githubusercontent.com/77331292/132716136-9b445bc2-9c03-4685-a9d2-e1c95f673561.png" width="200" />
</p>  
  
*  Click on the + container button at the top and add a private container called "suspectstatements". Select your suspect statements container
<p align="center">
  <img src="https://user-images.githubusercontent.com/77331292/132716556-a667276b-0687-4589-b41e-cc30e5c11dc0.png" width="300" />
</p> 
  
* Click the upload button at the top and select all files you wish to upload. Your uploaded statements in the container should look like the screenshot below.
<p align="center">
  <img src="https://user-images.githubusercontent.com/77331292/132718420-d212312f-4c53-42a2-829c-1d9e013e02a0.png" width="500" />
</p> 
  
##### Upload files via Microsoft Azure Storage Explorer

If you have the storage explorer downloaded then you can also use this method to upload the suspect statements.

In the explorer:
* Add your Azure Account and you should see all your storage accounts appear in the left column. 
* Select the account which you created earlier and then select your container. 
* Click on the Upload button and add the downloaded suspect statements to the container. 
* Once done, check in the Azure Portal that the files have been added. 

![uploadStatements](https://user-images.githubusercontent.com/73177811/114023663-0fdd0e00-986b-11eb-9ab3-c78f2a60ce4e.png)


## Designing your logic app

Before commencing with designing your logic app, make sure that the logic app deployed from the ARM template at the start of the lab has deployed successfully. You will be using that logic app for analysing the suspect statements.

To help people get started there are many different logic app templates which can be used to provide a starting point for developers, such as: "Recurrence" and "When a new tweet is posted". Today you will be using the "When a HTTP request is received" trigger template which causes the logic app to be run when it receives a HTTP request. 

#### 1. Starting with a HTTP Request Trigger

* Below is a screenshot from the logic app designer page prior to a flow being created. You should select the HTTP trigger which is highlighted.

![httpCommonTrigger](https://user-images.githubusercontent.com/73177811/114719907-6fd22980-9d2f-11eb-897f-8734a449a0ed.png)

#### 2. Bringing suspect statements into your logic app

To ensure we can analyse the statements we first need to bring the suspect statements into the logic app, In the logic apps designer:

* Select the "+ New Step" button after the HTTP request trigger.
* Search for Azure Blob Storage and then select it.

![BlobConnector](https://user-images.githubusercontent.com/73177811/114741082-571f3f00-9d42-11eb-9239-e563287d4721.png)

* Select the "List Blobs" action. This will allow you to see the suspect statements which are in your subscription.

![listBlobs](https://user-images.githubusercontent.com/73177811/114723956-05bb8380-9d33-11eb-81b8-a24a5e603b31.png)

* You will now be prompted for an authentication key to connect to your storage where your statements are uploaded. 
  Fill in the blanks with the details below:
  -   *Connection Name*: sotrageconnection
  -   *Authentication Type*: Access Key
  -   *Azure Storage Account name*: mysterystorage<youralias>
  -   *Azure Storage Account Access Key*: Follow instructions below!
  
* To get your access key 
  1. Go to your storage account and navigate to Security + Networking > Access Keys 
  <p align="center">
   <img src="https://user-images.githubusercontent.com/77331292/132727858-8396f6af-8c39-46da-8e7a-70e30c699e4b.png" />
  </p>  
  2. Click on "Show Keys"
  <p align="left">
   <img src="https://user-images.githubusercontent.com/77331292/132728290-dce7a20b-153a-4b87-bbc6-7098ba3f2639.png" />
  </p>
  3. Select a key and copy to clipboard
  <p align="left">
   <img src="https://user-images.githubusercontent.com/77331292/132728711-48b38b8b-ddd4-406f-9c34-d701921a4452.png" />
  </p>
  4. Navigate back to your Logic App. Paste Key in "Azure Storage Account Access Key"
  
  
* In the "List blobs" box, for the "Folder" field select the folder where your suspect statements are stored, and leave the other fields as default.

![selectFolder](https://user-images.githubusercontent.com/73177811/114724146-2c79ba00-9d33-11eb-8905-d4413f5e5ed8.png)

* Click save and test run your logic app by clicking on the "Run" button at the top of the designer. You should see be able to see all the suspect statments and scroll through them. Your results from the run should look similar to the screenshot below:

![listBlobsResults](https://user-images.githubusercontent.com/73177811/114723614-b412f900-9d32-11eb-9b4f-0a5ae4f36023.png)  

#### 3. Selecting each statement to analyse

It's great that we can see the statements and they are all present, but now we need to look at each statement individually so that we can analyse it with the Text Analytics service.

As we have the all the statements together we need to loop through them so that we can look at one statement at a time. To do this in logic apps you use the "For each" control operation.

* Add a new step in the designer and search for the "Control" operation. In there, select the "For each" action.

![forEach](https://user-images.githubusercontent.com/73177811/114725447-69927c00-9d34-11eb-8dbc-b03f746e322d.png)

* In the "For each" step add the "value" from the list blobs dynamic content pop up box as the output from previous step. 

![valueDynamicContent](https://user-images.githubusercontent.com/73177811/114725844-c2faab00-9d34-11eb-92df-de2fe204e814.png)

* Then, for choosing the next operation, search for "Azure Blob Storage" and then select the "Get blob content" action. Selet "id" as the Blob and have "Infer Content Type" as "Yes".

![getBlobContent](https://user-images.githubusercontent.com/73177811/114727688-54b6e800-9d36-11eb-883c-6833cca6725e.png)

#### 4. Analyse each statement's sentiment

* Add a new step and search for "Text Analytics". Then select "Sentiment (V3.0)(preview)" as the action. This action will allow you to analyse the sentiment of the suspect statement. If their statement is negative then this action will send back a low score and if the statement is positive then you will receive a high score. The scores range from 0 to 1.

![textAnalytics](https://user-images.githubusercontent.com/73177811/114728147-bd05c980-9d36-11eb-8148-f5425cc50089.png)

* To allow you to perform the sentiment analysis on the correct statements you will need to make sure the text analytics service in the logic app is connected to your cognitive service resource which you created earlier.
   * Connection name: Analyse Sentiment
   * Account Key: Your key from your cognitive services resource. Can be Key 1 or Key 2. Obtain this from the "keys and Endpoint" tab in your cognitive services resource.
   * Site URL: Your cognitive service endpoint.
   
![textAnalyticsConnection](https://user-images.githubusercontent.com/73177811/114729341-cc394700-9d37-11eb-996e-7ebdab2d8fb7.png)

* Once you are connected to your resource you can perfomr the sentiment analysis on each suspect statement. Select "Id" for the "documents id - 1" and then "File Content" for "documents text - 1". This brings in the individual suspect statement. Enter "en" for the "documents language - 1" to specify that the statements are in English.

![connectSentiment](https://user-images.githubusercontent.com/73177811/114729901-4cf84300-9d38-11eb-8734-50476ce7c9b5.png)

#### 5. Save and test your logic app

You now have everything necessary to start analysing suspect statements! Make sure you have saved your logic app and then click "Run". You should be able to select through each suspect statement and look at the sentiment results.

You can also trigger your logic app from an API call. You can perform a HTTP GET request to the URL of your logic app to initiate the logic app. Try this method if you would like to learn more about APIs and making HTTP requests.

## Optional extra steps

In this section of the task, try to explore the other actions in the text analytics connector. There will be no guided tutorial for this but do ask your coach if you get stuck.

#### 1. Extract Key Phrases from the suspect statements

#### 2. Perform Entity Recognition

## Resources

* [Logic App Documentation](https://docs.microsoft.com/en-gb/azure/logic-apps/)
* [Intro to Logic Apps Learn Module](https://docs.microsoft.com/en-gb/learn/modules/intro-to-logic-apps/)
* [Text Analytics Learn Module](https://docs.microsoft.com/en-gb/learn/modules/analyze-text-with-text-analytics-service/)
