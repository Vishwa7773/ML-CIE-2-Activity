# Machine Learning CIE 2: Unit I – Foundations and Data Preparation

## Project Overview

This project is part of the Machine Learning CIE 2 activity. The objective is to inspect a real world dataset, identify data quality issues, handle missing values, perform Exploratory Data Analysis (EDA), and prepare the dataset for future machine learning applications.

The activity focuses on understanding and preprocessing data rather than building a prediction model.

## Dataset Information

**Dataset Name:** San Francisco Building Permits

**Source:** [Kaggle: Building Permit Applications Data](https://www.kaggle.com/datasets/aparnashastry/building-permit-applications-data)

**Original File Name:** Building_Permits.csv

**File Type:** CSV

**Original Dataset Dimensions:**
- Rows: 198,900
- Columns: 43

The dataset contains information about building permit applications in San Francisco. It includes permit details, construction information, estimated costs, building usage, neighbourhoods, locations and permit status.

## Tools and Libraries Used

The project was implemented using Python in Google Colab.

The following libraries were used:

1. **Pandas:** Data loading, manipulation and preprocessing.
2. **NumPy:** Numerical operations.
3. **Matplotlib:** Data visualization.
4. **Seaborn:** Statistical visualization.
5. **Scikit learn:** Encoding and feature scaling.

## Work Completed

### 1. Dataset Loading and Inspection

The dataset was downloaded using KaggleHub and loaded into a Pandas DataFrame.

Initial inspection included:
- Displaying sample records.
- Checking dataset dimensions.
- Examining column names and data types.
- Separating numerical and categorical columns.
- Reviewing the structure of the dataset.

### 2. Missing Value Analysis and Handling

Missing values were identified using `isnull().sum()` and their percentages were calculated for each column.

Several columns contained a significant number of missing values.

The following preprocessing steps were performed:

- Removed columns with excessive missing values or limited analytical usefulness, including Street Number Suffix, Unit, Unit Suffix, Completed Date, Structural Notification, Voluntary Soft Story Retrofit, Fire Only Permit, TIDF Compliance and Site Permit.
- Filled missing categorical values using the mode.
- Filled missing numerical values using the median.
- Converted selected categorical columns into appropriate data types.
- Verified missing values after imputation.

### 3. Outlier Detection and Duplicate Checking

Box plots and the Interquartile Range (IQR) method were used to examine outliers.

An IQR based filter was applied to the Record ID column.

Duplicate records were checked using Pandas. No duplicate rows were found in the dataset at the duplicate checking stage.

### 4. Exploratory Data Analysis (EDA)

Basic statistical analysis and visualizations were performed to understand the dataset.

The analysis included:

- Descriptive statistics of numerical columns.
- Correlation heatmap of numerical features.
- Bar plot comparing Estimated Cost across Permit Types.
- Examination of relationships between numerical variables.

**Key Observations:**

1. Permit Type 1 showed the highest estimated cost in the bar plot.
2. The numerical correlation heatmap showed relationships between several numerical features.
3. Estimated Cost and Revised Cost showed substantial variation, indicating differences in the costs associated with building permit applications.

### 5. Categorical Encoding

Categorical variables were converted into numerical representations for future machine learning applications.

The following methods were used:

- **One Hot Encoding:** Applied to Permit Type Definition, Street Suffix, Current Status, Existing Use, Proposed Use, Existing Construction Type Description and Proposed Construction Type Description.
- **Neighbourhood Encoding:** San Francisco neighbourhoods were mapped to numerical tiers using a manually defined dictionary.
- **Date Feature Extraction:** Permit Creation Date was separated into day, month, year and quarter.
- **Target Encoding:** Block and Lot columns were encoded using Estimated Cost as the target variable.

Columns considered unnecessary for the intended analysis were removed, including Permit Number, Description, Street Name, Location and selected date columns.

### 6. Feature Scaling

Standardisation was performed using Scikit learn's `StandardScaler`.

The target variable, Estimated Cost, was separated from the input features before scaling.

The StandardScaler transformation was applied to the feature matrix to bring numerical features onto a comparable scale.

### 7. Saving the Prepared Dataset

The processed DataFrame was exported as a separate CSV file.

**Output File:** `SA_Building_Permit_Application_Cleaned.csv`

**Final Dataset Dimensions:**
- Rows: 161,995
- Columns: 261

The final dataset contains encoded categorical features and processed numerical features.

## Project Structure

```text
Unit 1/
│
├── ML_ACT_1.ipynb
│
├── SA_Building_Permit_Application_Cleaned.csv
│
└── README.md
```

## How to Run the Project

1. Clone or download this repository.
2. Open `ML_ACT_1.ipynb` using Google Colab or Jupyter Notebook.
3. Install the required Python libraries if they are not already available.
4. Run the notebook cells in sequence.
5. The notebook downloads the original dataset using KaggleHub.
6. Execute the preprocessing and analysis steps to generate the cleaned CSV file.

## Conclusion

This activity provided practical experience in data inspection, cleaning and preparation for machine learning workflows.

The San Francisco Building Permits dataset initially contained 198,900 records and 43 columns, with missing values across several numerical and categorical features.

Missing values were handled using mode and median imputation, unnecessary columns were removed, outliers were examined, and duplicate records were checked. Exploratory Data Analysis helped identify patterns and relationships in the data.

Categorical features were encoded using One Hot Encoding, neighbourhood mapping and target encoding. Date features were extracted, and numerical input features were standardised using StandardScaler.

The final prepared DataFrame contained 161,995 records and 261 columns and was saved as a separate CSV file.

No prediction model was trained as the activity focused on the foundations of data preparation and exploratory analysis.

## Courtesy

**Data:** [Aparna Shastry - Kaggle Building Permit Applications Data](https://www.kaggle.com/datasets/aparnashastry/building-permit-applications-data)
**Coding Platform:** [Google Colab](https://colab.google.com)

## Faculty Profile and Acknowledgement

Faculty Reference: [Princy2129 GitHub Profile](https://github.com/Princy2129)

This project was completed as part of the Machine Learning CIE 2 activity. Faculty reference and Machine Learning learning resources: [https://github.com/Princy2129](https://github.com/Princy2129).

## Author

**Name:** Vishwajeet Baing

**Roll Number:** AD3110

**Class:** TY AI-DA A

**Course:** Machine Learning

**Activity:** CIE 2, Unit I: Foundations and Data Preparation
