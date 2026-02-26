# 🚗 AWS-used-car-price-prediction-xgboost
## 📌 Project Overview

This project demonstrates an end-to-end Machine Learning workflow on AWS SageMaker, including:
1. Local data preprocessing using Jupyter Notebook
2. Uploading processed data to Amazon S3
3. Training a Machine Learning model using SageMaker Built-in XGBoost
4. Saving trained model artifact to S3
5. ❌ Endpoint NOT deployed (as per assignment requirement)

## 🎯 Objective

Build a regression model to predict used car prices using AWS SageMaker.

## 📂 Dataset

Source: Kaggle Used Car Dataset Link : https://www.kaggle.com/code/ashishghimire101/used-car-price-prediction-and-visualization 

*  Rows: 4,009

*  Columns: 12

*  Target Variable: price

## 🧱 Project Structure
AWS-used-car-price-prediction-xgboost/

│   ├── 01_local_preprocessing.ipynb

│   ├── 02_sagemaker_training.ipynb

│   ├── used_cars.csv

│   ├── train.csv

│   ├── test.csv

|   ├── README.md

## ⚙️ System Architecture
<img width="1207" height="467" alt="image" src="https://github.com/user-attachments/assets/6b6c91d3-8aa3-4d5a-89ab-9923c4ca5341" />

<img width="1198" height="494" alt="image" src="https://github.com/user-attachments/assets/732f35d9-a874-4ee9-8f03-54f366a8f3f4" />

## 🧪 Step 1: Local Data Preprocessing

Notebook:
*  01_local_preprocessing.ipynb

### Step 1.1 Load Dataset
used_cars.csv
<img width="1210" height="578" alt="image" src="https://github.com/user-attachments/assets/e0586d43-6938-4829-bde8-fc6e7c1ecea3" />

### Step 1.2 Data Cleaning
Performed:

*  Removed $ from price

*  Removed mi. from milage

*  Converted text to numeric

*  Handled missing values
<img width="1215" height="537" alt="image" src="https://github.com/user-attachments/assets/3efdb09e-509f-4db0-9c5c-88215086e304" />

### Step 1.3 Feature Engineering
Created new feature:
* car_age = current_year − model_year

#### Dropped:
1. brand
2. model
3. ext_col
4. int_col
<img width="1214" height="602" alt="image" src="https://github.com/user-attachments/assets/9501c370-870a-43cb-8ffe-893a05aae30e" />

### Step 1.4 Encoding
*  Used: LabelEncoder
<img width="1216" height="602" alt="image" src="https://github.com/user-attachments/assets/d2cf568b-945b-4bf4-a7e9-f26174c58f79" />

### Step 1.5 Train Test Split
#### Exported:
*  train.csv
*  test.csv
<img width="1214" height="598" alt="image" src="https://github.com/user-attachments/assets/4a81b371-00e2-4dfc-bad6-43fbda0a54ef" />

## ☁️ Step 2: Upload Data to AWS S3
### Uploaded:
<img width="1338" height="551" alt="image" src="https://github.com/user-attachments/assets/dcdf4f7d-5a33-4e29-b774-3c359cc6453f" />

## 🔐 Step 3: IAM Role Configuration
An IAM role was created to allow SageMaker to access AWS resources securely.
### Role Name

*  Ali-SageMakerExecutionRole

### Attached Policy

*  AmazonSageMakerExecutionRole

### Purpose of This Role

The IAM role allows:

*  SageMaker Notebook to read training data from Amazon S3

*  SageMaker Training Job to write model artifacts to S3

*  SageMaker to launch and manage training instances

*  This role was selected while creating the SageMaker Notebook instance.

## 🤖 Step 4: Launch SageMaker Notebook Instance
### Created Notebook Instance:
*  Instance type: ml.t3.medium
<img width="1332" height="559" alt="image" src="https://github.com/user-attachments/assets/5a496582-92fb-43c9-82da-d5f042d3995b" />

## 🧠 Step 5: Model Training using SageMaker XGBoost
### Notebook:
*  Ali_sagemaker_.jpynb
  
<img width="1364" height="627" alt="Screenshot 2026-02-26 004736" src="https://github.com/user-attachments/assets/75096057-87f3-4368-8949-81eea9acac9b" />

### Training Configuration

#### Instance:
* ml.t3.medium

<img width="1352" height="437" alt="image" src="https://github.com/user-attachments/assets/c9da7277-4d97-4cf9-a49f-6375c9276015" />

#### Algorithm:

* XGBoost (Built-in SageMaker)

<img width="1365" height="633" alt="Screenshot 2026-02-26 004807" src="https://github.com/user-attachments/assets/0b6434de-ce9d-4d1e-ad94-666562b3ece7" />

### 📊 Training Result

| Metric          | Value   |
| --------------- | ------- |
| Training RMSE   | $9,681  |
| Validation RMSE | $18,887 |
| Training Time   | 135 sec |

<img width="1365" height="637" alt="Screenshot 2026-02-26 004859" src="https://github.com/user-attachments/assets/2e8babab-7af3-4059-8a60-4ace1c2aafba" />

## 📦 Step 5: Model Saved to S3
### Output:
* model.tar.gz
### Location:
*  S3 Output Bucket
<img width="1347" height="544" alt="image" src="https://github.com/user-attachments/assets/0f45dc98-317d-4c12-93ab-de02b5acfc93" />

## ⛔ Step 6: Endpoint NOT Deployed
As per assignment instructions:
*  Endpoint was NOT deployed
*  Notebook instance was STOPPED to avoid charges.
<img width="1348" height="547" alt="image" src="https://github.com/user-attachments/assets/b48460cd-ede3-4d40-a212-63b6c17e7a57" />

## 🧰 Technologies Used

| Tool             | Purpose          |
| ---------------- | ---------------- |
| Python           | Programming      |
| Jupyter Notebook | Development      |
| Pandas           | Data Processing  |
| Scikit-Learn     | Preprocessing    |
| AWS S3           | Storage          |
| AWS SageMaker    | Model Training   |
| XGBoost          | Machine Learning |

## 📈 Workflow Summary
Local Preprocessing

↓

Upload to S3

↓

Train Model on SageMaker

↓

Save Model to S3

↓

Stop Notebook

## 🚀 How to Run This Project
### Step 1
Clone repo
* git clone https://github.com/yourusername/AWS-used-car-price-prediction-xgboost
### Step 2
Run:
*  01_local_preprocessing.ipynb
### Step 3
Upload files to S3
### Step 4
Run:
02_sagemaker_training.ipynb
## 📌 Final Output
*  model.tar.gz









