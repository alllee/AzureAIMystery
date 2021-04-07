# Cluedo

## Create a Custom Vision Project

 #### 1. In a new browser tab, open the Custom Vision portal at https://customvision.ai and sign in using the MIcrosoft account associated with your Azure subscription
 #### 2. Select New Project
 
 ![image](https://user-images.githubusercontent.com/32169182/113877961-160eb400-97b1-11eb-9fc2-69a25b8b7686.png)


 #### 3. Create New Project with the followeirng settings:
-   Name: CluedoCustomVision
    
-   Description: Train an Object Detection model to identify the location of murder weapons within an image of a room
    
-   Resource: cluedocogservice
    
-   Project Types: Object Detection
    
-   Domains: General [A1]

#### 4. Click Create Project. Wait for the project to be created and opened in the browser.

![image](https://user-images.githubusercontent.com/32169182/113878016-245cd000-97b1-11eb-963b-3cabe1fac02a.png)

---

## Add and Tag Images
To train an object detection model, you need to upload images that contain the classes you want the model to identify, and tag them to indicate bounding boxes for each object instance.
1.  Download and extract the training images from INSERT FOLDER HERE. (Please help me upload this [folder](https://microsoft-my.sharepoint.com/:f:/p/alllee/EuIRFWVcF9xDqvPr2BEtwZEBok4OoCjJutJdMk7zvMf27w?e=rp24dn)). The extracted folder contains a collection of images of weapons scattered in a room.
    

2.  In the Custom Vision portal, in your object detection project, select Add Images and upload all of the images in the extracted folder.
    

3.  After the images have been uploaded, select the first one to open it.
    

4.  Hold the mouse over any object in the image until an automatically detected region is displayed like the image below. Then select the object, and if necessary resize the region to surround it.
