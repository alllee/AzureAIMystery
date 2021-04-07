# Instructions for creating a logic app to analyse suspect statements

## Gettin the suspect statements into your subscription

Prior to creating a logic app to analyse the suspect statements we first need to get the statements into your Azure subscription. 
To Download the suspect statement files click here: ADD LINK

Once downloaded, you will need to upload the files to an Azure storage account in your subscription. You can upload the files using the Microsoft Azure Storage Explorer.

If you do not currently have a storage account with a blob container in your subscription then click the button below and this will start the deployment process for you.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Falllee%2Fcluedo%2Fmain%2FLogicApp%2Fazuredeploy.json)

* Select the resource group that you want to deploy this to, the resource group you used earlier for the custom vision section would be ideal, and then give the storage account and container names. 
* Try and use a region which is close to you geographically. 
* When done, click review + create at the bottom of the page and then select create once the validation has passed. 
* Finally, wait for your deployment to complete.


