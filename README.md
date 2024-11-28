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

5. **Support Vector Machine (SVM)**  
   An SVM classifier is trained using a `GridSearchCV` for hyperparameter tuning. The regularization parameter (`C`) is tuned, and the best model is selected using cross-validation (`cv=5`) based on accuracy. SVMs are particularly useful for binary classification tasks, and they are effective in high-dimensional spaces.

Each model is trained using the training data and its respective best hyperparameters selected through grid search, ensuring that the most suitable model is chosen for the classification task.











