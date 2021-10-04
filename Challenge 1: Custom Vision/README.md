


# Cluedo

Hello Detective! You have been given some images from the crime scene but you need a way to analyse them and identify potential murder weapons. 

In this challenge, you will be building an Object Detection Model. Firstly, you will train your model using sample Training Images of the objects you wish to detect. Then, you will test your model using the Crime Scene Images. 

Make note of which Weapon was detected in which Room. YOu will need this information later!

Good luck!

## Create a Custom Vision Project

  1. In a new browser tab, open the Custom Vision portal at https://customvision.ai and sign in using the Microsoft account associated with your Azure subscription
  2. Select New Project
 
 ![image](https://user-images.githubusercontent.com/32169182/113877961-160eb400-97b1-11eb-9fc2-69a25b8b7686.png)


 #### 3. Create New Project with the followeirng settings:
-   Name: CluedoCustomVision
    
-   Description: Train an Object Detection model to identify the location of murder weapons within an image of a room
    
-   Resource: cluedocogservice_youralias_
    
-   Project Types: Object Detection
    
-   Domains: General [A1]

#### 4. Click Create Project. Wait for the project to be created and opened in the browser.

![image](https://user-images.githubusercontent.com/32169182/113878016-245cd000-97b1-11eb-963b-3cabe1fac02a.png)

---

## Add and Tag Images
To train an object detection model, you need to upload images that contain the classes you want the model to identify, and tag them to indicate bounding boxes for each object instance.
1.  Download and extract the [Training Images](https://github.com/alllee/AzureMurderMystery/blob/main/Challenge%201:%20Custom%20Vision/Training%20Images.zip). The extracted zip folder contains a collection of images of weapons scattered in a room.
    

2.  In the Custom Vision portal, in your object detection project, select Add Images and upload all of the images in the extracted folder.
    

3.  After the images have been uploaded, select the first one to open it.
    

4.  Hold the mouse over any object in the image until an automatically detected region is displayed like the image below. Then select the object, and if necessary resize the region to surround it.

![image](https://user-images.githubusercontent.com/32169182/113878612-ad740700-97b1-11eb-924d-a4f4c0bddb81.png)

5. Alternatively, you can simply drag around the object to create a region. When the region surrounds the object, add a new tag with the appropriate object type (Lead Pipe, Dagger, Rope, Wrench, Revolver, Candlestick) as shown here: 

![image](https://user-images.githubusercontent.com/32169182/113878814-dac0b500-97b1-11eb-8c5a-57e41f29369c.png)

6. Select and tag each other object in the image, resizing the regions and adding new tags as required

![image](https://user-images.githubusercontent.com/32169182/113878936-f4fa9300-97b1-11eb-9b43-26762514b9aa.png)

7.  Use the > link on the right to go to the next image, and tag its objects. Then just keep working through the entire image collection, tagging each Lead Pipe, Dagger, Rope, Wrench, Revolver, Candlestick.

8.  When you have finished tagging the last image, close the Image Detail editor and on the Training Images page, under Tags, select Tagged to see all of your tagged images:

---

## Train and Test a Model
1.  In the Custom Vision project, click Train to train an object detection model using the tagged images. Select the Quick Training option.
    
2.  Wait for training to complete (it might take ten minutes or so), and then review the Precision, Recall, and mAP performance metrics - these measure the prediction accuracy of the classification model. Take note of the performance per tag – which weapon has the highest precision?

3. Download and extract the zip file [Crime Scene Images](https://github.com/alllee/AzureMurderMystery/blob/main/Challenge%201:%20Custom%20Vision/Crime%20Scene%20Images.zip). On the custom vision page, at the top right of the page, click Quick Test, and then upload an image from the extracted zip folder and view the prediction that is generated. Increase the threshold to 90%  and observe the results. What weapons have been identified in which rooms?


## OPTIONAL: Additional Steps
1. Source your own additional images for each murder weapon. Use your search engine of choice to search for and download 2-3 images of each murder weapon. 

2. Upload and tag your images on Custom Vision as you have done previously.

3. Retrain your model. How has the additional training data affected your model performance?

---

## Resources

[Custom Vision Documentation](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/)
