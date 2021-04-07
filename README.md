

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

![image](https://user-images.githubusercontent.com/32169182/113878612-ad740700-97b1-11eb-924d-a4f4c0bddb81.png)

5. Alternatively, you can simply drag around the object to create a region. When the region surrounds the object, add a new tag with the appropriate object type (Lead Pipe, Dagger, Rope, Wrench, Revolver, Candlestick) as shown here: 

![image](https://user-images.githubusercontent.com/32169182/113878814-dac0b500-97b1-11eb-8c5a-57e41f29369c.png)

6. Select and tag each other object in the image, resizing the regions and adding new tags as required

![image](https://user-images.githubusercontent.com/32169182/113878936-f4fa9300-97b1-11eb-9b43-26762514b9aa.png)



