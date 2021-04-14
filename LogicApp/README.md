# Instructions for creating a logic app to analyse suspect statements

## Getting the suspect statements into your subscription

#### Downloading the suspect statements

Prior to designing a logic app to analyse the suspect statements we first need to get the statements into your Azure subscription. 
To Download the suspect statement files click here: ADD LINK

#### Uploading the suspect statements

Once downloaded, you will need to upload the files to an Azure storage account in your subscription. There are a couple of options to upload the suspect statements. If you already have the Microsoft Azure Storage Explorer downloaded you can then use that to upload the files to your storage account. If not, then more simply, you can upload the files through the Azure Portal.

##### Upload files via Azure Portal

* Head over to your storage account resource in the Azure Portal
* Click on the containers section
* Select your suspect statements container
* Click the upload button at the top and select the files you wish to upload.

![uploadStatementsPortal](https://user-images.githubusercontent.com/73177811/114716732-3c41d000-9d2c-11eb-8204-8978deac28ad.png)


[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Falllee%2Fcluedo%2Fmain%2FLogicApp%2Fazuredeploy.json)

* Select the resource group that you want to deploy this to, the resource group you used earlier for the custom vision section would be ideal, and then give the storage account and container names. 
* Try and use a region which is close to you geographically. 
* When done, click review + create at the bottom of the page and then select create once the validation has passed. 
* Finally, wait for your deployment to complete.

![createStorageAccount](https://user-images.githubusercontent.com/73177811/114023014-48301c80-986a-11eb-9ad2-241a1f619bfc.png)

Once this is deployed, you can now try uploading the suspect statements via the storage explorer previously mentioned.

![uploadStatements](https://user-images.githubusercontent.com/73177811/114023663-0fdd0e00-986b-11eb-9ab3-c78f2a60ce4e.png)

In the explorer:
* Add your Azure Account and you should see all your storage accounts appear in the left column. 
* Select the account which you created earlier and then select your container. 
* Click on the Upload button and add the downloaded suspect statements to the container. 
* Once done, check in the Azure Portal that the files have been added. 

## Creating a Logic App

Now that we have the data in your subscription, we can start to use it to find out who the murderer is! To become the detective you’ve always wanted to be, we will need the assistance of a Logic App... 

#### Deploy the logic app via the portal

* Head over to the Azure Portal and click on the create a resource button at the top of the page.
* Search for "Logic App" and then select the "create" button.

![createLA](https://user-images.githubusercontent.com/73177811/114717342-ddc92180-9d2c-11eb-8c31-e1d08622fef4.png)

* Fill out the logic app creation form with these details:
  *   Subscription: Select your Visual Studio Enterprise Subscription (Or other subscription if not using MSDN)
  *   Respurce group: Select the resource group created earlier from the computer vision section
  *   Logic App name: AnalyseSuspectStatements (You can name it this or something similar)
  *   Region: UK South (Any region close to you)
  *   Leave everything else as default and then click Review + Create

![createLAForm](https://user-images.githubusercontent.com/73177811/114718179-aa3ac700-9d2d-11eb-97a3-fb70fcb678d9.png)

Your deployment page should look similar to the above.

## Designing your logic app

Once the logic app is deployed you can click on the resource and get started with the design process. There are many different logic app templates which can be used to provide a starting point for developers, such as: "Recurrence" and "When a new tweet is posted". Today you will be using the "When a HTTP request is received" trigger template which causes the logic app to be run when it receives a HTTP request. Below is a screenshot from the logic app designer page prior to a flow being created. You should select the HTTP trigger which is highlighted.

![httpCommonTrigger](https://user-images.githubusercontent.com/73177811/114719907-6fd22980-9d2f-11eb-897f-8734a449a0ed.png)

#### Bringing suspect statements into your logic app

To ensure we can analyse the statements we first need to bring the suspect statements into the logic app, In the logic apps designer:

* Select the "+ New Step" button after the HTTP request trigger.
* Search for Azure Blob Storage and then select it.
![BlobConnector](https://user-images.githubusercontent.com/73177811/114722500-c2144a00-9d31-11eb-8a61-0a6f4b099364.png)
* Select the "List Blobs" action. This will allow you to see the suspect statements which are in your subscription.
![listBlobs](https://user-images.githubusercontent.com/73177811/114723956-05bb8380-9d33-11eb-81b8-a24a5e603b31.png)
* In the "List blobs" box, for the "Folder" field select the folder where your suspect statements are stored, and leave the other fields as they are.
![selectFolder](https://user-images.githubusercontent.com/73177811/114724146-2c79ba00-9d33-11eb-8905-d4413f5e5ed8.png)
* Click save and test run your logic app by clicking on the "Run" button at the top of the designer. You should see be able to see all the suspect statments and scroll through them. Your results from the run should look similar to the screenshot below:
![listBlobsResults](https://user-images.githubusercontent.com/73177811/114723614-b412f900-9d32-11eb-9b4f-0a5ae4f36023.png)  

