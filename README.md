# Melanoma Prediction Using Images  

This repository aims to predict melanoma using dermoscopic images. It is based on the model architecture proposed by [Ha, Qishen, Bo Liu, and Fuxu Liu](https://arxiv.org/pdf/2010.05351v1). Our work builds upon their research by placing Squeeze-and-Excitation (SE) blocks after each main layer of the SE ResNet and adding self-attention layer before the final pooling stage. In addition, we added `anomaly_score` feature, which detects abnormal records. This was made using isolation forests by treating the "unkown" diagnosis as unlabeled data. Lastly, since the dataset is highly imbalanced, we combined the model’s results with an XGBoost model, which is known for its ability to handle imbalanced data effectively. We used both CNN and XGBoost because each model excels at different things—CNN excels at understanding image features, while XGBoost effectively detects patterns in additional data and handles imbalanced data. By combining them, we created a more intelligent system that dynamically determines when to rely on each, making the final predictions more accurate.



## Dataset  

The dataset used in this project is sourced from the [SIIM-ISIC Melanoma Classification Challenge](https://www.kaggle.com/competitions/siim-isic-melanoma-classification/overview) on Kaggle. It consists of approximately 44,000 records, divided into training and test subsets:  

- **Training set:** ~33,000 records  
- **Test set:** ~10,000 records  

Each record corresponds to a patient. It is possible for a patient to appear multiple times if they had multiple dermoscopic images. The data includes:

- **File path of dermoscopic image**  
- **Age**  
- **Sex**  
- **Anatomical site of the imaged region**  
- **Diagnosis** (available only in the training set)  

The dataset contains **seven features** in total. Our goal is to predict whether a given record is diagnosed as melanoma or not.

## Project Structure  

- **`Analysis.ipynb`** – Contains exploratory data analysis (EDA) of the dataset, including data distribution and feature exploration.  
- **`melanoma_classification.ipynb`** – Implements the melanoma prediction model.  

## Required Files  

Some files are not included in this repository and must be downloaded manually:  

- **`kaggle.json` file** – Required to access Kaggle datasets via the API. You can obtain one from your [Kaggle account settings](https://www.kaggle.com/settings).  
- **`siim-isic-melanoma-classification.zip` file** – Contains the dataset (images, train, and test CSV files). Download it manually from the [SIIM-ISIC Melanoma Classification Challenge page on Kaggle](https://www.kaggle.com/competitions/siim-isic-melanoma-classification/data).  

