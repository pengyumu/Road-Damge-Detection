
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
For object detection training, we employ a model called YOLOv8, which is one of the latest versions of YOLO, providing enhanced performance and versatility. to identify and classify road damage. 
### Testing
The trained models are then tested on the reserved test dataset to assess their performance. The primary performance metric used is the F1-score, which considers both precision and recall, providing a balanced measure of model accuracy. Additionally, we conducted error analysis to identify common failure modes and areas for improvement. This step is crucial for understanding the model's weaknesses and refining the training process to enhance overall performance.
### Model Considerations
Throughout this process, the primary considerations are achieving high accuracy and detailed detection of various road damage types. By leveraging multiple advanced object detection models and thorough testing, we aim to develop a reliable and efficient road damage detection system suitable for deployment in Singapore's public transport network and LTA-owned vehicles.


## Results

We started training with YOLOv8s using pre-trained parameters: confidence threshold = 0.25, IOU threshold = 0.7, image size = 640. The training process began by filtering out images without annotations, allowing 10% of the dataset to include background images. The training was conducted on an NVIDIA Tesla V100 GPU. The model is trained for a total of 10 epochs, with a warmup period of 5% of the total epochs (1 epoch) to stabilize the training process, using a batch size of 32, and employing a cosine learning rate scheduler (cos_lr=True) for adaptive learning rate adjustment.

In our exploration of YOLOv8's hyperparameters, we focused on the mosaic augmentation parameter to improve the model's generalization.  Initially, YOLOv8s was trained without mosaic augmentation, resulting in an F1 score of 0.547. Then we introduced mosaic augmentation set to 0.2 (20% training images using mosaic augmentation). With mosaic augmentation applied, the model displayed improved performance metrics with an F1 score of 0.574, Next, we examined the impact of model complexity by experimenting with different versions: nano (YOLOv8n), small (YOLOv8s), and medium (YOLOv8m). YOLOv8n, despite its quick convergence, showed limitations in capturing detailed features, resulting in a lower F1 score of 0.540. In contrast, the YOLOv8m model, while offering greater capacity and potential for higher accuracy, demonstrated issues with overfitting on our dataset and had the worst F1 score of 0.487. After comprehensive evaluation, YOLOv8s proved to be the optimal choice, balancing model size, computational efficiency, and performance. These findings highlight the importance of careful hyperparameter tuning and model complexity consideration to achieve the best results in practical deployment scenarios.

![image](https://github.com/pengyumu/Road-Damge-Detection/assets/174324735/ff72dd60-f347-4a62-90cd-04a01d389630)

The YOLOv8s model can successfully identify different types of cracks but struggles to detect cracks that are further away, obscured by shadows, or have similar background textures. Additionally, the model fails to accurately detect repairs and shows an issue with duplicate detections, indicating areas needing improvement. These limitations highlight the need for further tuning and refinement to enhance detection capabilities under varied real-world conditions. According to the results obtained so far, YOLOv8 demonstrates good performance in detecting specific classes such as D00 (Longitudinal cracks) and D10 (Transverse cracks), however, its overall performance must be evaluated and optimized to achieve consistent improvements.

![image](https://github.com/pengyumu/Road-Damge-Detection/assets/174324735/f27a5092-5856-46d2-86ce-e93ea05f7e18)

