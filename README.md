#YOLOV5

YOLO an acronym for 'You only look once', is an object detection algorithm that divides images into a grid system. Each cell in the grid is responsible for detecting objects within itself.

YOLO is one of the most famous object detection algorithms due to its speed and accuracy.
YOLOv5 is a family of object detection architectures and models pretrained on the COCO dataset, and represents Ultralytics open-source research into future vision AI methods, incorporating lessons learned and best practices evolved over thousands of hours of research and development.
See the [YOLOv5 Docs](https://docs.ultralytics.com) for full documentation on training, testing and deployment.

![image](https://user-images.githubusercontent.com/61906871/185408179-aae7ba79-fbe9-43d5-a86a-fbf7bc4766bc.png)

![image](https://user-images.githubusercontent.com/61906871/185408226-869442b2-99e5-4370-8ef9-994c9a927724.png)

1. Explanation about the files in the ‘yolov5/important docs’ folder:
- Convert\_pascaltoyolo.ipynb: this script is to run on google colab, to convert the labels from pascal to yolo.
- Model Summary: contains all of the info, results, predictions of the model
- Best uae.pt: this is the best weights file for the model
- Best bhr.pt
- Replace.py: the script to run locally to changes words in the labels files if needed to
- training model using best.pt exp.docx: this is a documentation of some experiences conducted on the model
- hp tuning: to show the different experiences held to reach the optimal hyperparameters
- yolo-model-object-detection final notebook.ipynb: this is the notebook to run on Kaggle for faster results, to train the model and run inference.



1. How to use this model?

1) **Running the model**


Section 1

![image](https://user-images.githubusercontent.com/61906871/185402810-9f8c22b5-0e9e-488f-835d-ff5883a766e1.png)

![image](https://user-images.githubusercontent.com/61906871/185402875-05aa5bcb-aa2e-4eb9-807a-5f032e0a9536.png)

-open the notebook yolov5/important docs/ yolo-model-object-detection final notebook.ipynb

-if cloning from github, generate a key to add it next to the github link, since the key expires after 90 days, and the repo is private

-install all the requirements

-better to use Kaggle to implement it because it’s much faster






Section 2





-This section is to edit the data.yaml file, which we use to precise the number of classes and their names, whenever we need to add classes, we must edit this file and this section in the code is dedicated to edit it

\- here is an example of the data.yaml file, next to train and test we find their paths 
![image](https://user-images.githubusercontent.com/61906871/185403445-d3b4cb6f-adb7-4ef0-80eb-26dc24c58235.png)

NB: also we should edit the file yolov5/models/yolov5s.yaml and change the parameter nc, if we added new classes




`	`Section 3

![image](https://user-images.githubusercontent.com/61906871/185403502-547dd6d2-749c-4e6d-b246-e74e1b30df61.png)

![image](https://user-images.githubusercontent.com/61906871/185403532-dfd1fb23-e349-49bc-82bb-f9e67b9ba3fe.png)

-this is the part where we train the model, next to --cfg we choose which version of yolov5 we want to use, here we implemented yolov5s which is the small one, since the dataset is small

\- next to --weights, we leave it empty ‘ ‘ like this, if we are building the model from scratch, 

If we want to build over another model, we must put the best.pt file in here

-once we run this code, we will see this message, we must choose option 2 by writing it in the console

-this cell must be run twice for the changes to take effect

-Results will start to appear as shown below

![image](https://user-images.githubusercontent.com/61906871/185403565-03205a70-97cb-4fff-b3ee-4efc85f4e1a6.png)

- box\_loss: location loss based on IoU
- cls\_loss: classification loss based on binary cross-entropy for each class
- obj\_loss: objectness loss based on how confident there is an object in each bounding box
- P: Precision
- R: Recall
- mAP: mean Average Precision 

NB: To finetune to model, we can modify the hyperparameters by editing  data/hyps/hyp.scratch-low.yaml

![image](https://user-images.githubusercontent.com/61906871/185403726-26d403bc-41fb-45c6-beb4-d018db72d609.png)


At the end of the training, it will show where the results are saved and we will use this later on

Section 4


![image](https://user-images.githubusercontent.com/61906871/185403957-360329ab-d3c4-4df2-8186-232bb2658d9d.png)

- choose the confidence threshold for the predictions
- choose the weights generated by the previous cell
- we can display the images with the predictions

Section 5

![image](https://user-images.githubusercontent.com/61906871/185404010-6e4e6bc9-4de1-4eab-91ed-fea18cd0ab72.png)


-Save the best weights and download them 

Section 6

![image](https://user-images.githubusercontent.com/61906871/185404038-623ba58a-0170-48f2-8be2-cb0c96f0e124.png)

-finally, we can now load the model from any notebook and run predictions

![image](https://user-images.githubusercontent.com/61906871/185404063-92961c1c-943a-4b4d-8b31-8d607a44c89e.png)


\- if we want to build over this model, we put the best.pt next to – weights

-We can also freeze 10 layers for example and then add the parameter –freeze when training


##YOLOV7

Yolov7 is a real-time object detector currently revolutionizing the computer vision industry with its incredible features. The official YOLOv7 provides unbelievable speed and accuracy compared to its previous versions. Yolov7 weights are trained using Microsoft’s COCO dataset, and no pre-trained weights are used.

The paper states that the model can efficiently predict video inputs ranging from 5FPS to 160FPS. Among all real-time object detectors, YOLOv7 has the highest Average Precision (AP) score of 56.8% creating impressive records.

Yolov7 outperformed both transformer-based object detectors and convolutional-based object detectors. Some of the object detectors that Yolov7 outperformed were YOLOR, YOLOX, Scaled-YOLOv4, YOLOv5, DETR, Deformable DETR, DINO-5scale-R50, ViT-Adapter-B, etc.
![image](https://user-images.githubusercontent.com/61906871/185407059-c0f952f0-338c-444d-b4e0-5bf5f0da5fa4.png)

![image](https://user-images.githubusercontent.com/61906871/185407156-e48661a4-3ed9-4314-b68a-ca61ae935c92.png)

Implementation of paper - [YOLOv7: Trainable bag-of-freebies sets new state-of-the-art for real-time object detectors](https://arxiv.org/abs/2207.02696)
The word Bag of Freebies model refers to increasing the model accuracy by making improvements without actually increasing the training cost. Older versions like YOLOv4 also used the Bag of Freebies model. 


1. Explanation about the files in the ‘yolov7/important docs’ folder:
- Convert\_pascaltoyolo.ipynb: this script is to run on google colab, to convert the labels from pascal to yolo.
- Model summary yolov7\_uae: contains all of the info, results, predictions of the model
- best uae.pt: this is the best weights file for the model
- best bhr.pt
- best uae+bahrein
- replace.py: the script to run locally to changes words in the labels files if needed to
- yolo-obj-det-v7-uae: notebook to run on Kaggle to train the model and run inference.
- yolo-obj-det-v7-uae: notebook to run on Kaggle to train the model and run inference.

**How to implement Yolov7?**

1) **Running the model**


Section 1

![image](https://user-images.githubusercontent.com/61906871/185404217-a4acae8c-b0c0-447b-b83f-ea8e56dede6a.png)



-if cloning the github, generate a key to add it next to the github link, since the key expires after 30 days, and the repo is private

-install all the requirements

-better to use Kaggle to implement it because it’s much faster

Section 2

Install the requirements and set up the environment



Section 3

-This section is to edit the ./data/data.yaml file, which we use to precise the number of classes and their names, whenever we need to add classes, we must edit this file and this section in the code is dedicated to edit it

\- here is an example of the data.yaml file, next to train and test we find their paths 

![image](https://user-images.githubusercontent.com/61906871/185405182-5e0c53ab-9e90-478d-80a7-148e1eb003fa.png)



Section 4:

![image](https://user-images.githubusercontent.com/61906871/185405227-2ec1f349-9288-4361-898c-b8b89deb8b00.png)


-this is the part where we train the model, next to --cfg we choose which version of yolov5 we want to use, here we implemented yolov7-tiny which is the small one, since the dataset is small

\- next to --weights, we leave it empty ‘ ‘ like this, if we are building the model from scratch, 

If we want to build over another model, we must put the best.pt file in here

-Results will start to appear as shown below

![image](https://user-images.githubusercontent.com/61906871/185405302-3b8924d2-1ffe-467c-9fc4-d1958976ec8d.png)




- box\_loss: location loss based on IoU
- cls\_loss: classification loss based on binary cross-entropy for each class
- obj\_loss: objectness loss based on how confident there is an object in each bounding box
- P: Precision
- R: Recall
- mAP: mean Average Precision 

NB: To finetune to model, we can modify the hyperparameters by editing  data/hyp.scratch.p5.yaml
At the end of the training, it will show where the results are saved and we will use this later on





Section 5

- choose the confidence threshold for the predictions
- choose the weights generated by the previous cell
- we can display the images with the predictions

![image](https://user-images.githubusercontent.com/61906871/185405782-16326a67-7d8a-498d-baa4-1d93b3edbb0e.png)

Section 6:

-Save the best weights and download them 

![image](https://user-images.githubusercontent.com/61906871/185405811-10d0b34d-571c-4cc1-a046-349c43b658d5.png)


**NB:** 

**There are 2 files showcasing the difference between yolov5 and yolov7 tested on the datasets of Bahrein and uae, and we can find them in the main repo.**
