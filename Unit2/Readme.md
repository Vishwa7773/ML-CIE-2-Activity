# Pune House Rent Prediction Using Linear Regression

## Machine Learning – CIE 2 | Unit II: Supervised Learning – Regression

This project implements a **Linear Regression model** to predict house rental prices in Pune, Maharashtra, using property-related features. It demonstrates the complete machine learning workflow, including data collection, exploratory data analysis, preprocessing, feature engineering, model training, prediction, and evaluation.

---

## 1. Project Overview

| Detail | Description |
|---|---|
| Project Name | Pune House Rent Prediction |
| Subject | Machine Learning |
| Activity | CIE 2 |
| Unit | Unit II – Supervised Learning: Regression |
| Algorithm | Linear Regression |
| Problem Type | Supervised Learning – Regression |
| Programming Language | Python |
| Environment | Jupyter Notebook / Google Colab |
| Target Variable | `rent` |
| Dataset | Rental Price of India's IT Capital – Pune, MH, India |

### Objective

To develop a Linear Regression model capable of predicting the monthly rental price of a property in Pune based on its characteristics, such as area, bedrooms, bathrooms, parking, furnishing, property age, and locality.

---

## 2. Dataset Information

**Dataset Name:** Rental Price of India's IT Capital - Pune, MH, India

**Source:** Kaggle

**Dataset Link:**  
https://www.kaggle.com/datasets/anantsakhare/rental-price-of-indias-it-capital-pune-mh-ind

**Description:**

The dataset contains residential property rental information from Pune, Maharashtra. It includes property characteristics and amenities that can influence rental prices.

Some of the important attributes include:

- `bedroom` – Number of bedrooms.
- `bathrooms` – Number of bathrooms.
- `area` – Property area.
- `furnishing` – Furnishing status.
- `address` – Property locality.
- `floor_number` – Floor on which the property is located.
- `parking` – Parking availability.
- `propertyage` – Age of the property.
- `deposit_amt` – Security deposit amount.
- `rent` – Monthly rental price (target variable).

The target variable, `rent`, is numerical and continuous, making it suitable for a regression problem.

---

## 3. Technologies and Libraries Used

The following Python libraries were used:

- **Pandas:** Data loading, manipulation, and cleaning.
- **NumPy:** Numerical operations.
- **Matplotlib:** Data visualization.
- **Seaborn:** Statistical visualization.
- **Scikit-learn:** Data preprocessing, model training, splitting, and evaluation.
- **KaggleHub:** Downloading the dataset from Kaggle.

---

## 4. Project Workflow

### Step 1: Data Loading and Inspection

The dataset was downloaded using KaggleHub and loaded into a Pandas DataFrame.

Initial dataset dimensions:

- Rows: 10,884
- Columns: 30

The dataset was inspected using:

- `head()` – To examine sample records.
- `shape` – To identify dataset dimensions.
- `info()` – To understand column names and data types.
- `describe()` – To examine statistical summaries.
- `isnull().sum()` – To identify missing values.

### Step 2: Data Cleaning

The following preprocessing operations were performed:

1. Removed `wheelchairadption` and `petfacility` because they contained a large percentage of missing values.
2. Filled missing values in `avalable_for` using its mode.
3. Renamed `avalable_for` to `available_for`.
4. Removed records with invalid or zero property area.
5. Applied the Interquartile Range (IQR) method to remove outliers from the `area` column.
6. Removed extreme rental-price observations above ₹1,50,000 for model preparation.

After removing area outliers, the dataset contained 6,571 records.

### Step 3: Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed to understand the dataset and identify relationships between property characteristics and rental prices.

Visualizations included:

- Boxplots for identifying numerical outliers.
- Correlation heatmap for examining relationships between numerical variables.
- Barplot for comparing average rent across parking categories.
- Scatter plot for examining the relationship between property area and rent.

### Step 4: Feature Engineering and Encoding

The dataset contained both numerical and categorical features.

The following transformations were performed:

- Applied One-Hot Encoding using `pd.get_dummies()` to categorical variables such as furnishing, availability, facing, floor type, gated community, and corner property.
- Extracted locality information from the address column.
- Converted property age into a numerical representation.
- Created an encoded locality feature based on locality categories.
- Removed the `maintenance_amt` column.

### Step 5: Feature and Target Selection

The target variable was:

- **Y = `rent`**

The input features consisted of the remaining cleaned and transformed property-related columns.

Multiple features were used to predict rental prices rather than relying on a single numerical feature.

### Step 6: Data Visualization

A scatter plot was created to examine the relationship between property area and monthly rent.

- X-axis: Area (square feet)
- Y-axis: Monthly Rent (INR)

The visualization helps examine how property size relates to rental prices.

A visible relationship does not necessarily establish causation, as rental prices can also depend on location, furnishing, amenities, and other factors.

### Step 7: Train-Test Split

The dataset was divided into training and testing sets using Scikit-learn's `train_test_split()`.

| Parameter | Value |
|---|---|
| Training Data | 75% |
| Testing Data | 25% |
| Random State | 42 |

The training dataset was used to learn the model parameters, while the testing dataset was kept separate to evaluate performance on unseen observations.

### Step 8: Feature Scaling

StandardScaler was applied to the input features.

The scaler was fitted only on the training data and then used to transform both training and testing data.

This prevents information from the testing dataset from influencing the scaling parameters learned during training.

### Step 9: Model Training

Linear Regression from Scikit-learn was selected as the regression algorithm.

The model was trained using the scaled training features and corresponding rental prices.

The model learns coefficients and an intercept to estimate rental prices from the selected property features.

### Step 10: Model Evaluation

The model was evaluated using the testing dataset.

The following regression metrics are included in the evaluation:

- **MAE (Mean Absolute Error):** Measures the average absolute difference between actual and predicted rental prices.
- **MSE (Mean Squared Error):** Measures the average squared prediction error.
- **RMSE (Root Mean Squared Error):** Represents prediction error in the same units as the rental price.
- **R² Score:** Measures how well the model explains variations in the target variable compared with a mean-based baseline.

The notebook currently reports the following test-set result:

| Evaluation Metric | Result |
|---|---:|
| R² Score | 0.6654 |
| MAE | Pending correction |
| MSE | Pending correction |
| RMSE | Pending correction |

An R² score of approximately 0.6654 indicates that the model explains around 66.54% of the variation in the test-set rental prices.

### Step 11: Actual vs Predicted Visualization

A scatter plot was created to compare actual rental prices with the values predicted by the trained Linear Regression model.

A reference line represents perfect predictions, where predicted values equal actual values.

Points closer to the reference line indicate more accurate predictions, while points farther away indicate larger prediction errors.

### Step 12: Prediction

The trained model was used to generate a prediction for a test observation.

The predicted rental price was compared with the corresponding actual rental price to examine the model's prediction performance.

The prediction is expressed in Indian Rupees (INR).

---

## 5. Key Results

- Successfully loaded and explored a Pune property rental dataset containing 10,884 initial records.
- Performed missing-value handling and outlier removal.
- Applied categorical encoding and numerical feature engineering.
- Used multiple property-related features for prediction.
- Implemented an 75:25 training-testing split.
- Trained a Linear Regression model.
- Obtained a test R² score of approximately **0.6654**.
- Visualized actual versus predicted rental prices.

---

## 6. Limitations

- Rental prices depend on several factors that may not be fully represented in the dataset.
- Locality, property condition, nearby facilities, and market demand can influence rental prices.
- Outlier removal may exclude some genuine high-value properties.
- Linear Regression assumes a linear relationship between input features and the target.
- The model may not accurately capture complex relationships between property characteristics and rental prices.

---

## 7. Conclusion

This project demonstrates the application of Supervised Learning through Linear Regression to predict residential rental prices in Pune.

The dataset was explored, cleaned, transformed, and used to train a regression model. The model achieved an R² score of approximately 0.6654 on the testing dataset.

The activity provided practical experience in data preprocessing, exploratory data analysis, feature engineering, model training, prediction, and regression evaluation.

Although the model provides a useful starting point for rental-price prediction, incorporating additional property and locality information could potentially improve its accuracy.

---

## 8. Repository Structure

```text
ML-CIE-2-Linear-Regression/
│
├── ML_ACT_2(1).ipynb
│
└── README.md
```

---

## 9. How to Run the Project

1. Clone this repository:

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
```

2. Navigate to the project directory:

```bash
cd YOUR_REPOSITORY_NAME
```

3. Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn kagglehub
```

4. Open the Jupyter Notebook:

```bash
jupyter notebook
```

5. Open `ML_ACT_2(1).ipynb` and execute the notebook cells sequentially.

**Note:** KaggleHub may require Kaggle authentication or API configuration to download the dataset.

---

## 10. Faculty Reference and Acknowledgement

This project was completed as part of the Machine Learning CIE 2 activity.

**Faculty Profile:** [Princy2129 – GitHub](https://github.com/Princy2129)

**Acknowledgement:**

"This project was completed as part of the Machine Learning CIE 2 activity. Faculty reference and Machine Learning learning resources: https://github.com/Princy2129"

---

## 11. Author

**Student Name:** Vishwajeet Baing 
**Roll Number:** AD3110 
**Class:** TY AI-DS A
**Subject:** Machine Learning  
**Activity:** CIE 2 – Linear Regression

---

*This repository is maintained as part of the academic submission for the Machine Learning CIE 2 activity.*
