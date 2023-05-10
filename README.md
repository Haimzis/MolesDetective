# Moles Detective - Mobile Application for Skin Lesion Analysis
#### End-to-end computer vision project by Haim Zisman & Asaf Federman
***

### Sub-Project Components
| Component | Link |
| :---: | :---: |
| Annotation tool & XML Parse | [Submodule Link](https://github.com/Haimzis/LabelMeMaskParser/tree/18b38a83dd2a8ae94e536e2cd7c3c780ae1911b1) |
| Frontend Android Application | [Submodule Link](https://github.com/Asaf-Federman/Moles_Detective_AndroidApp/tree/f357b83a7fae3707a9c1c298de0b47730621f01e) |
| Backend Flask Server | [Submodule Link](https://github.com/Haimzis/Moles_Detective_Server_Backend/tree/b6767f8516781b513f58cab8d8f30fb346c00933) |
| Data Augmentation & Preprocessing | [Submodule Link](https://github.com/Haimzis/Moles_Detective_Data_Backend/tree/b6d9a407dcacc964f7f4c308c2f1567f4c242cb5) |
| Model Training & Deployment (DeeplabV3) | [Submodule Link](https://github.com/Haimzis/Moles_Detective_Deeplab_MobileNetV3/tree/b7a8f80832ce24d2c80baa1b7a08bc4b5c69af5c) |

## Description
**Moles Detective was developed as our final project for our CS degree.** Its goal is to analyze skin lesions and identify cancerous lesions using deep learning and computer vision methods such as:
* Semantic Segmentation
* Classification
* Color Thresholding
* Centroid Alignment
* Hair Removal
  etc.

Each submodule contains a full description of its purpose.

### Our Approach
**Data Acquisition**: For segmentation, we used the ISIC2018 Dataset, which contains approximately 2500 annotated masks and images of skin lesions, along with our own annotated data from various sources. For classification, we used data from Kaggle and ISIC2019, augmenting it to make it relevant to our task (mobile samples).

**Data Preprocessing & Augmentation**: We developed our own image preprocessing methods and used OpenCV for state-of-the-art techniques. You can find a full description in our Data Backend Project.

**Soft-RT Inference**: The mobile application includes a semantic segmentation model that achieves a performance of approximately 25 frames per second on modern devices. The segmentation task is performed by a state-of-the-art quantized Mobilenet TFlite model. Users can see the skin lesion being highlighted in real time and send the images to the server when they are confident that the picture is clear and stable.

**Server Inference**: When users send pictures to the server, additional inference is performed using state-of-the-art MobileNetV3 and InceptionV3 models to obtain more accurate results for classification and segmentation without resizing that may remove important features.

**Final Analysis**: For each sample in the user input, several analysis methods are executed:
* Color Analysis: Seeking suspicious colors within given color ranges.
* Border Irregularity: Checking the smoothness of the lesion border.
* Size: Two versions of the task are available, one based on dpi (less accurate) and the other based on pixels per metric.
* Asymmetry
* Classification: Prediction using our InceptionV3 model trained on various cancerous classes and noncancerous examples.

Each analysis returns a value based on the ABCD official rating method. By calculating a weighted sum of these values, we can determine the level of danger associated with the lesion.

### Summary
**Achievements**:
* Our inference for asymmetry, border irregularity, color analysis, and size (pixels per metric) has shown good accuracy.
* We achieved significant performance improvements by creating our own annotations for our specific task.
* The main mobile application works at approximately 25 frames per second on modern devices.
* We developed a powerful data backend that successfully generated unlimited augmented data using templates and a few annotated masks.
* The DeeplabV3 project served us perfectly, allowing us to train, deploy, and optimize our models.
* After studying numerous papers related to our problem domain, we implemented satisfying algorithms for our tasks.
* We created a user-friendly interface combined with the latest mobile camera API, CameraX (Google) for Android.

etc...

**Goals for Improvement**:
* Enhance the application's ability to accurately interpret all parameters and provide an accurate determination of cancerous/noncancerous lesions. Finding a better balance between the parameters is necessary.
* Improve the accuracy of the classification model by acquiring more computational power.
* Address the lack of data specifically applicable to our problem domain, which involves mobile devices. A cloud-based platform would be ideal for gathering data from a larger number of contributors.

**This project has been an exciting challenge, and we have achieved many of our sub-goals while learning a great deal along the way :)**

**We encourage you to explore the mentioned submodules for more information.**
