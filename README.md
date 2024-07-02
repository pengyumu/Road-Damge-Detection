# Road-Damge-Detection

## Problem Statement

Detecting road damage is a resource-intensive task that can be costly and draining on manpower.  To address this challenge, we propose building a road damage detection system capable of both identifying and classifying various types of road damages.

## Data

The dataset used for this project is the Road Damage Detection (RDD2022) dataset, which includes 47,420 road images annotated with 55,000 labeled road instances (Arya et al., 2022). These images were taken in 5 countries, namely, Japan, India, the United States, Czech Republic, Norway, and China. Images taken in China were further segregated by the method employed to capture the images, namely motorbike and drone. Driven by the need to maintain quality and relevance to the local context, we trained our models only using images from Japan, the United States, Czech Republic, and China motorbike. These countries were selected due to their similar road features to Singapore, high image quality, and robust variations of road damage classes. In contrast, the sandy and snowy road conditions in India and Norway respectively are not applicable to Singapore, and using drones to capture road conditions in Singapore is not practical due to potential danger to aviation and the public, especially in Singapore’s busy airspace and urban landscape. Therefore, the exclusion was necessary to ensure that our model is trained on data that closely represents the types of road conditions in Singapore.
 Figure 1: Sample images from the dataset for each country.

Understanding the distribution of this data is crucial for building a robust model. The dataset contains 20,117 images with 42,440 instances of road damage across eight classes. By analyzing the data distribution across different countries (Figure 2), we can ensure that our model can generalize well across diverse scenarios. For instance, Japan's dataset has the most balanced distribution across different damage types and is also the only dataset that includes crosswalk blur, white line blur, and manhole cover. In contrast, the images from the Czech Republic, the United States, and China show a clear prevalence of longitudinal, transverse, and alligator cracks. Additionally, the dataset from China includes a considerable number of repairs, reflecting a diverse range of damage types. Visualizations of these distributions help us understand the variety and prevalence of different road damage categories, highlighting the potential challenges our detection system might face in different environments. This comprehensive analysis ensures that our model is well-prepared to handle a wide range of real-world scenarios, making it a robust tool for enhancing road maintenance efforts in Singapore.
