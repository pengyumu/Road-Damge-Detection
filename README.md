# Road-Damge-Detection

## Introduction

Detecting road damage is a resource-intensive task that can be costly and draining on manpower.  To address this challenge, we propose building a road damage detection system capable of both identifying and classifying various types of road damages.

## Dataset

The dataset used for this project is the Road Damage Detection (RDD2022) dataset, which includes 47,420 road images annotated with 55,000 labeled road instances. These images were taken in 5 countries, namely, Japan, India, the United States, Czech Republic, Norway, and China. Images taken in China were further segregated by the method employed to capture the images, namely motorbike and drone. Here we trained our models only using images from Japan, the United States, Czech Republic, and China motorbike. These countries were selected due to their high image quality and robust variations of road damage classes. 

![image](https://github.com/pengyumu/Road-Damge-Detection/assets/174324735/2ca845f0-61f4-4913-ab27-830f6853067a)

The selected dataset contains 20,117 images with 42,440 instances of road damage across eight classes. By analyzing the data distribution across different countries, we can ensure that our model can generalize well across diverse scenarios. For instance, Japan's dataset has the most balanced distribution across different damage types and is also the only dataset that includes crosswalk blur, white line blur, and manhole cover. In contrast, the images from the Czech Republic, the United States, and China show a clear prevalence of longitudinal, transverse, and alligator cracks. Additionally, the dataset from China includes a considerable number of repairs, reflecting a diverse range of damage types. Visualizations of these distributions help us understand the variety and prevalence of different road damage categories, highlighting the potential challenges our detection system might face in different environments. 

![image](https://github.com/pengyumu/Road-Damge-Detection/assets/174324735/4d6de4ba-dec6-4a56-b593-be2402b76585)

## Methodology 

### Data Preparation
The dataset was split into training, validation, and test sets with a ratio of 70:20:10, stratified by country to ensure a representative sample from each region. This stratification helps maintain the distribution of road damage types across the different subsets, which is crucial for training a robust model. By normalizing and resizing the images, we provide a consistent input format that facilitates effective training and inference. This preprocessing step ensures that the model receives data in a standardized form, improving its ability to learn and generalize from the training data.
### Object Detection Training
For object detection training, we employ several state-of-the-art models to identify and classify road damage. These models include:
•	Faster R-CNN: A region-based convolutional neural network that excels at object detection and localization.
•	SSD with MobileNet: Single Shot Multibox Detector (SSD) with MobileNet backbone, offering a good trade-off between speed and accuracy.
•	YOLOv5: You Only Look Once (YOLO) version 5, known for its real-time object detection capabilities.
•	YOLOv8: One of the latest versions of YOLO, providing enhanced performance and versatility.
•	RetinaNet: Utilizes a focal loss function to address class imbalance, making it suitable for detecting rare road damage types.
### Testing
The trained models are then tested on the reserved test dataset to assess their performance. The primary performance metric used is the F1-score, which considers both precision and recall, providing a balanced measure of model accuracy. Additionally, we conducted error analysis to identify common failure modes and areas for improvement. This step is crucial for understanding the model's weaknesses and refining the training process to enhance overall performance.
### Data Augmentation on the Best Model
Based on the performance metrics and error analysis, the best-performing model is selected for further refinement. The selected model is retrained and evaluated with data augmentation techniques, such as varying weather conditions, to test its robustness and generalization capabilities. This ensures that the model can maintain high accuracy and detailed detection across diverse and challenging real-world scenarios.
### Model Considerations
Throughout this process, the primary considerations are achieving high accuracy and detailed detection of various road damage types. By leveraging multiple advanced object detection models and thorough testing, we aim to develop a reliable and efficient road damage detection system suitable for deployment in Singapore's public transport network and LTA-owned vehicles.

