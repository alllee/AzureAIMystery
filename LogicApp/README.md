# Instructions for creating a logic app to analyse suspect statements

## Getting the suspect statements into your subscription

#### Downloading the suspect statements

Prior to creating a logic app to analyse the suspect statements we first need to get the statements into your Azure subscription. 
To Download the suspect statement files click here: ADD LINK

#### Uploading the suspect statements

Once downloaded, you will need to upload the files to an Azure storage account in your subscription. You can upload the files using the Microsoft Azure Storage Explorer.

If you do not currently have a storage account with a blob container in your subscription then click the button below and this will start the deployment process for you.

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
