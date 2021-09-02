# **Introduction**

This repository contains workshops and content for the *Azure AI Mystery* workshop.

## Who it's for

This workshop is aimed at individuals with an interest in Artificial Intelligence but with no experience of the cloud artificial intelligence platform and services, who would like some experience deploying and consuming AI services in no-code environments on Azure. 

The outcome is hopefully to boost knowledge of confidence in starting to use these components.

## Infrastructure

To get you started, we have put together a template containing the resources you will need to complete each of the challenges. Please click on the button below to start the deployment process for you:


[![Deploy To Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Falllee%2FAzureMurderMystery%2Fmain%2Ftemplate.json)

![Deployment of Template Page](https://user-images.githubusercontent.com/77331292/121039271-db24fe80-c7a8-11eb-9599-814c9c079c22.png)


#### Fill in the custom deployment page with the details below:
-   **Resource Group**> Create New > MurderMystery
   
-   **Storage Accounts_mysterystorage_name**: mysterystorageyouralias
  
-   **Accounts_mysterycogservice_name**: mysterycogserviceyouralias
  
-   **Logic App**: Keep it how it is
  
When done, click review + create at the bottom of the page and then select create once the validation has passed. Finally, wait for your deployment to complete.

If successful, you should be able to see a list of the 3 resources deployed within your resource group
 
**You are now ready to begin your first challenge!**
