<h1>INM701: Introduction to AI - Coursework Project</h1>

<p>
This project is part of the coursework for the <strong>INM701: Introduction to AI</strong> module, completed by
<span style="font-size: 1.5em; color: blue;">
  <a href="https://anndischeh.github.io/" target="_blank" style="text-decoration: none; color: blue;">Anndischeh Mostafavi</a>
</span>
and
<span style="font-size: 1.5em; color: green;">
  <a href="https://github.com/StylianosIoannou" target="_blank" style="text-decoration: none; color: green;">Stylianos Ioannou</a>
</span>
as contributors.
</p>



<h2>Repository Structure</h2>

<ul>
  <li style="background-color: #f0f8ff; padding: 10px; border-radius: 5px;">
    <strong style="font-size: 18px; color: #0056b3;">Anndischeh and Stylianos:</strong>  
    <a href="https://github.com/Anndischeh/Introduction-to-AI-Coursework/blob/main/Final_code.ipynb" target="_blank" style="color: #0000ff; font-weight: bold; font-size: 16px;">final_code.ipynb</a><br>
    This file is the final collaborative work of both Anndischeh and Stylianos.
    <br>
    It was submitted as the final project file through the university's system.
  </li>

  <li style="background-color: #f0f8ff; padding: 10px; border-radius: 5px;">
    <strong style="font-size: 18px; color: #0056b3;">Anndischeh:</strong>  
    <a href="https://github.com/Anndischeh/Introduction-to-AI-Coursework/tree/main/feature/coded-by-anndischeh" target="_blank" style="color: #0000ff; font-weight: bold; font-size: 16px;">`feature/coded-by-anndischeh` branch</a><br>
    Contains Anndischeh's contributions, including her code and her individual written reflection evaluating her work.  
  </li>

  <li style="background-color: #f0f8ff; padding: 10px; border-radius: 5px;">
    <strong style="font-size: 18px; color: #0056b3;">Stylianos:</strong>  
    <a href="https://github.com/Anndischeh/Introduction-to-AI-Coursework/blob/main/Untitled.ipynb" target="_blank" style="color: #008000; font-weight: bold; font-size: 16px;">untitled.ipynb</a><br>
    This file contains the individual contributions of Stylianos.  
  </li>

  <li style="background-color: #f0f8ff; padding: 10px; border-radius: 5px;">
    <strong style="font-size: 18px; color: #0056b3;">Stylianos:</strong>  
    <a href="https://github.com/Anndischeh/Introduction-to-AI-Coursework/tree/main/.ipynb_checkpoints" target="_blank" style="color: #008000; font-weight: bold; font-size: 16px;">.ipynb_checkpoints</a><br>
    Contains checkpoints related to the individual work of Stylianos.  
  </li>
</ul>




## Dataset Overview

In this classification project, the dataset [diabetes_012_health_indicators_BRFSS2015.csv](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset?select=diabetes_012_health_indicators_BRFSS2015.csv) is utilized. This dataset comprises **253,680 clean survey responses** collected from the CDC's 2015 Behavioral Risk Factor Surveillance System (BRFSS).

### Target Variable: `Diabetes_012`
The dataset's target variable consists of three classes:
- **0**: No diabetes or only during pregnancy  
- **1**: Prediabetes  
- **2**: Diabetes  

## Workflow and Steps

The project involves the following key steps:

1. **Import Required Libraries**  
2. **Load Dataset**  
3. **Data Exploratory Analysis (DEA)**  
4. **Data Visualization**  
5. **Data Preprocessing** 
 #### 1. Checking for Missing Values 
 #### 2. Removing Outliers 
 #### 3. Scaling Numeric Features 
 #### 4. Balancing the Classes Using SMOTE

6. **Model Selection and Training**  

 <ul>
                <li>Split the data into training, validation, and test sets.</li>
                <li>Train different machine learning models, including:
                    <ul>
                        <li>Decision Tree</li>
                        <li>Random Forest</li>
                        <li>K-Nearest Neighbors (KNN)</li>
                    </ul>
                </li>
                <li>Tune hyperparameters using GridSearchCV and RandomizedSearchCV.</li>
            </ul>
        </div>

7. **Model Evaluation**
Decision Tree Model Evaluation
Random Forest Model Evaluation
KNN Model Evaluation