# Road-Damge-Detection

## Introduction

Detecting road damage is a resource-intensive task that can be costly and draining on manpower.  To address this challenge, we propose building a road damage detection system capable of both identifying and classifying various types of road damages.

## Data

The dataset used for this project is the Road Damage Detection (RDD2022) dataset, which includes 47,420 road images annotated with 55,000 labeled road instances. These images were taken in 5 countries, namely, Japan, India, the United States, Czech Republic, Norway, and China. Images taken in China were further segregated by the method employed to capture the images, namely motorbike and drone. Here we trained our models only using images from Japan, the United States, Czech Republic, and China motorbike. These countries were selected due to their high image quality and robust variations of road damage classes. 

![image](https://github.com/pengyumu/Road-Damge-Detection/assets/174324735/2ca845f0-61f4-4913-ab27-830f6853067a)

The selected dataset contains 20,117 images with 42,440 instances of road damage across eight classes. By analyzing the data distribution across different countries, we can ensure that our model can generalize well across diverse scenarios. For instance, Japan's dataset has the most balanced distribution across different damage types and is also the only dataset that includes crosswalk blur, white line blur, and manhole cover. In contrast, the images from the Czech Republic, the United States, and China show a clear prevalence of longitudinal, transverse, and alligator cracks. Additionally, the dataset from China includes a considerable number of repairs, reflecting a diverse range of damage types. Visualizations of these distributions help us understand the variety and prevalence of different road damage categories, highlighting the potential challenges our detection system might face in different environments. 

![image](https://github.com/pengyumu/Road-Damge-Detection/assets/174324735/4d6de4ba-dec6-4a56-b593-be2402b76585)
