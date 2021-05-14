# ***Moles Detective - Mobile Application for Skin Lesion Analyze***
#### ***End to end computer vision project - By Haim Zisman & Asaf Federman***
***

### **Sub-Projects Components**
| Component | Link 
| :---: | :---: | 
| Annotation tool & Xml Parse | [Submodule Link](https://github.com/Haimzis/LabelMeMaskParser/tree/18b38a83dd2a8ae94e536e2cd7c3c780ae1911b1) |
| Frontend Android Application | [Submodule Link](https://github.com/Asaf-Federman/Moles_Detective_AndroidApp/tree/f357b83a7fae3707a9c1c298de0b47730621f01e) | |
| Backend Flask Server | [Submodule Link](https://github.com/Haimzis/Moles_Detective_Server_Backend/tree/b6767f8516781b513f58cab8d8f30fb346c00933) | |
| Data Augmentation & Preprocess | [Submodule Link](https://github.com/Haimzis/Moles_Detective_Data_Backend/tree/b6d9a407dcacc964f7f4c308c2f1567f4c242cb5) | |
| Model Training & Deployment (DeeplabV3)  | [Submodule Link](https://github.com/Haimzis/Moles_Detective_Deeplab_MobileNetV3/tree/b7a8f80832ce24d2c80baa1b7a08bc4b5c69af5c) | |

## Description
**Moles Detective was developed as a final project of our CS degree**  
its goal is to analyze skin lesions and even identify cancerous lesions,  
with personal Mobile devices - by using Deep learning, and some Computer vision methods such as:
* Semantic Segmentation
* Classification
* Color Threshold
* Centroid Alignment
* Hair Removal   
  etc..
  
Each Submodule contains full description of its purpose. 
  
### Our approach
**Data Acquisition**: for Segmentation, we have used ISIC2018 Dataset, it contains ~2500 annotated masks and images of skin lesions + our own annotated Data - from our social, google, etc..   
for Classification, We have used Data from Kaggle and ISIC2019 + our own augmentation for making this Data relevant to our task. (Mobile Samples)

**Data Preprocess & Augmentation**: We have build our own image preprocess methods, and used OpenCV for state-of-art methods.
full description can be found in our Data Backend Project.

**Soft-real Inference**: there is a semantic segmentation model on the actual mobile - the performance are ~25fps on nowadays devices.
the segmentation task itself done by a state-of-art quantized Mobilenet TFlite model.
the user can actually see the skin lesion getting lighted in real time, and sending them to the server when he sure that the picture is clear and stable.

**Server Inference**: when user sends pictures to the server, additional inference is done by state-of-art MobileNetV3 & InceptionV3 - for more accurate results of classification and segmentation (without resize that may cause important features removal).

**Final Analyzing**: for each sample in user input, some analyzing methods are running:
* Color Analyzing - seeking for a suspicious colors in a given ranges of color.
* Border irregularity - checks the smoothing in the border of the lesion.
* Size - there are 2 version of tasks, one is based on dpi (not so accurate as we want to ), the second is based on pixel-per-metric. 
* asymmetric
* classification - prediction of our InceptionV3 Model, trained on many cancerous classes and Noncancerous examples.

each one returns value that based on ABCD official rating method - with weighted sum of the calculations, we have an idea for how much this lesion is dangerous.

### Summary
**Achievements**:
* our asymmetric, border, color, size(pixels per metric) inference has a good accuracy.
* we reached a significant performance improvement with a self-made annotations for our own task.
* the main Application for mobile works at ~25 fps on nowadays devices.
* we developed a great Data backend that successfully generated unlimited augmented Data with templates, and a few annotated masks. 
* the deeplabV3 project has served us perfectly, and we managed to train/deploy and optimize the trained models that we have created by it.
* after reading many papers about our problem domain, we managed to implement a satisfying algorithms for our tasks.
* we managed to develop a friendly user interface, combined with the newest mobile camera API, CameraX(Google) for Android. 

etc...

**Would like to achieve**
* the application still can't take all the parameters and interpret them into an accurate answer of  
  cancerous/noncancerous, we should find a better balance between the parameters.
* the classification model isn't accurate enough - more computational power is required.
* we still have a lack of Data that can use us in our problem domain - Mobile devices.
a better way to grab data will be a cloud based platform for a much more contributors than we had.


**it was a great challenge. we succeed many of our sub-goals and learned many things through this project :)**

**We Encourage you to take a look on the mentioned submodules**
