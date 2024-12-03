# Diabetes Health Indicators Dataset Prediction
## Introduction
In this classification project, the dataset [diabetes_012_health_indicators_BRFSS2015.csv](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset?select=diabetes_012_health_indicators_BRFSS2015.csv) is utilized, which contains 253,680 clean survey responses from the CDC's 2015 Behavioral Risk Factor Surveillance System (BRFSS).

The target variable, Diabetes_012, consists of three classes:

- **0**: No diabetes or only during pregnancy  
- **1**: Prediabetes  
- **2**: Diabetes

Additionally, the dataset comprises 21 feature variables. Several steps will be followed to select and optimize models for high performance and accuracy.

<h1 style="color:pink;">1. Import Required Libraries</h1>

<h1 style="color:pink;">2. Load Dataset</h1>

To load the dataset into a pandas DataFrame and preview the first few rows

<h1 style="color:pink;">3. Data Exploratory Analysis (DEA) </h1>

The code provides an overview of the dataset, including its size (rows and columns), structure (column names, data types, and non-null counts), and a statistical summary with descriptive statistics for numerical columns, such as count, mean, standard deviation, and percentiles.

<h1 style="color:pink;">4. Data Visualization</h1>

1. **Distribution of Diabetes Categories**  
   This plot illustrates the distribution of the three diabetes categories (`0: No Diabetes, 1: Prediabetes, 2: Diabetes`) using a count plot. It provides an overview of the sample distribution for each category, aiding in understanding dataset balance.

2. **Correlation Heatmap**  
   A heatmap visualizes the correlation matrix of dataset features, highlighting relationships between variables. The color intensity indicates the strength and direction of correlations, useful for feature selection or understanding data structure.

3. **Proportion of HighBP and HighChol by Diabetes Status**  
   A grouped bar plot shows the average proportions of High Blood Pressure (HighBP) and High Cholesterol (HighChol) for each diabetes category. This visualization helps compare these conditions across diabetes statuses.

4. **BMI Distribution by Diabetes Status**  
   A histogram with kernel density estimation (KDE) displays the distribution of Body Mass Index (BMI) for different diabetes categories. It highlights variations in BMI patterns among the categories.

5. **Age Distribution by Diabetes Status**  
   A boxplot visualizes the distribution of age (categorized by groups) across diabetes statuses. It reveals age trends or variations linked to each category, emphasizing differences in age demographics.

6. **Histograms of All Attributes**  
   This visualization provides histograms for all attributes in the dataset, offering a quick glance at the individual distributions and data ranges for each feature.

7. **Pairplot of Selected Attributes**  
   A pairplot visualizes pairwise relationships and distributions among selected features (`BMI`, `HighBP`, `HighChol`, `PhysActivity`, `Age`, and `Diabetes_012`). It provides insights into feature interdependencies and category separability.

<h1 style="color:pink;">5. Data Preprocessing</h1>

### Data Preprocessing Section

1. **Checking for Missing Values**  
   This step checks for any missing values in the dataset. If missing values are found, the rows containing them are removed to ensure a clean dataset for further analysis.

2. **Handling Outliers in Numerical Columns**  
   Outliers in the dataset are addressed using the Interquartile Range (IQR) method. A custom function removes values outside the lower and upper bounds for the specified numerical column (e.g., `BMI`) to improve data quality and model performance.

3. **Encoding Categorical Variables**  
   Since the dataset already uses numeric encoding for categorical variables, no additional encoding is required at this step.

4. **Scaling Numeric Features**  
   Numeric features (`BMI`, `MentHlth`, `PhysHlth`, `Age`) are scaled using the `StandardScaler` to standardize their values. This helps ensure all features contribute equally to the machine learning model.

5. **Handling Class Imbalance**  
   To address class imbalance in the target variable (`Diabetes_012`), the SMOTE (Synthetic Minority Oversampling Technique) method is applied. SMOTE generates synthetic samples for the minority classes, balancing the dataset and improving model performance.

6. **Splitting Data into Training and Testing Sets**  
   After balancing the classes, the data is split into training and testing sets using an 80-20 ratio to train and evaluate the machine learning model.

7. **Preprocessing Summary**  
   A summary dictionary is generated to capture key preprocessing details, including:
   - Total missing values before and after cleaning.
   - Original and balanced class distributions.
   - List of numeric features that were scaled.  

   This provides a concise overview of the preprocessing steps applied to the dataset.

   <h1 style="color:pink;">6. Model Selection and Training</h1>

This section involves selecting various machine learning models and training them using the preprocessed data.

1. **Logistic Regression**  
   Logistic Regression is used as a baseline model for classification tasks. It is trained on the training data (`X_train` and `y_train`) using `LogisticRegression` from `sklearn.linear_model`. The hyperparameters such as regularization strength (`C`), penalty type (`l2`), and solver (`liblinear`) are set before fitting the model.

2. **Random Forest Classifier**  
   Random Forest, an ensemble model, is used to improve classification performance by combining multiple decision trees. A `GridSearchCV` is used for hyperparameter tuning, where different values for `n_estimators` are evaluated to find the optimal model. The best model is selected using cross-validation (`cv=3`) and scoring by accuracy.

3. **Decision Tree Classifier**  
   A Decision Tree Classifier is trained using a `GridSearchCV` to find the best hyperparameters. The `criterion` hyperparameter, which determines the function to measure the quality of a split (either "gini" or "entropy"), is tuned. Cross-validation (`cv=5`) is applied for model evaluation.

4. **K-Nearest Neighbors (KNN)**  
   KNN is a non-parametric method used for classification tasks. A `GridSearchCV` is applied to tune the `n_neighbors` hyperparameter, which controls the number of neighbors used for classification. The model is trained on a train-validation split to evaluate its performance and choose the best model based on accuracy.

5. **Stacking Classifier**: Combines the predictions of multiple models—Logistic Regression, Random Forest, Decision Tree, and KNN—using a final Logistic Regression model for the ensemble.
  
6. **Support Vector Machine (SVM)**  
   An SVM classifier is trained using a `GridSearchCV` for hyperparameter tuning. The regularization parameter (`C`) is tuned, and the best model is selected using cross-validation (`cv=5`) based on accuracy. SVMs are particularly useful for binary classification tasks, and they are effective in high-dimensional spaces.

Each model is trained using the training data and its respective best hyperparameters selected through grid search, ensuring that the most suitable model is chosen for the classification task.

## 7. Model Evaluation

This section involves evaluating the performance of the trained models using various metrics and visualizing the results to compare the models.

1. **Evaluation Function**  
   The `evaluate_model` function is responsible for training and evaluating each model. It performs the following steps:
   - **Training:** The model is trained on the training data (`X_train`, `y_train`).
   - **Predictions:** The model makes predictions on both the training and test datasets (`y_train_pred` and `y_test_pred`).
   - **Evaluation Metrics:** The following metrics are calculated to assess model performance:
     - **Accuracy:** Measures the proportion of correctly classified instances.
     - **Precision:** The proportion of true positives out of all predicted positives, calculated with weighted averaging.
     - **Recall:** The proportion of true positives out of all actual positives, again calculated with weighted averaging.
     - **F1 Score:** The harmonic mean of precision and recall.
     - **ROC-AUC Score:** The Area Under the Receiver Operating Characteristic curve, if the model supports probability prediction (`predict_proba`).
   - **Classification Report:** A detailed classification report is printed for further insight into precision, recall, and F1-score for each class.
   - **Return Metrics:** The function returns a dictionary containing the model name and its evaluation metrics for comparison.

2. **Model Definitions and Evaluation**  
   Several machine learning models are evaluated using the `evaluate_model` function:
   - **Logistic Regression**  
     A logistic regression model is trained with the parameters `C=1`, `penalty='l2'`, and `solver='liblinear'`.
   - **Random Forest Classifier**  
     A Random Forest model is evaluated with `n_estimators=30`, `max_depth=20`, and `min_samples_split=5`.
   - **Decision Tree Classifier**  
     A Decision Tree model is trained with `max_depth=15` and `min_samples_split=10`.
   - **(Optional) K-Nearest Neighbors (KNN) and Support Vector Machine (SVM)**  
     These models are available but commented out for the evaluation.

   For each model, the `evaluate_model` function is applied, and the results are stored in a list.

3. **Comparison of Models**  
   The results of the evaluation are displayed using bar plots for four evaluation metrics: accuracy, precision, recall, and F1 score. The models are compared by plotting their performance across these metrics, which helps visualize which models perform best in each category.

4. **ROC Curve Comparison**  
   If a model supports probability prediction (`predict_proba`), the ROC curve is plotted to compare the performance of models. The curve plots the True Positive Rate (TPR) against the False Positive Rate (FPR) and shows the AUC score for each model. This visualization is helpful for understanding the trade-off between sensitivity and specificity.

By evaluating and comparing the models, this section aims to identify the most suitable model for the dataset and task.









