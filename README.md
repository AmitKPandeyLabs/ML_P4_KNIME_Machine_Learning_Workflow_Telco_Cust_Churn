# KNIME Based Machine Learning: Telco Customer Churn Prediction

## Project Overview

This project presents a comprehensive, end-to-end machine learning workflow developed entirely within the **KNIME Analytics Platform**. The primary objective is to build a robust predictive model for identifying customers at high risk of churning in the telecommunications sector. By leveraging KNIME's visual programming capabilities, this project demonstrates a complete data science pipeline from initial data access and preprocessing to advanced model training, evaluation, and interactive result visualization.

This solution empowers telecom companies to implement proactive retention strategies, thereby mitigating revenue loss due to customer attrition.

---

## Project Context & Objectives

The telecommunications industry faces significant challenges with customer churn. Retaining existing customers is often more cost-effective than acquiring new ones. This project addresses the need for an efficient and accurate system to:

* **Identify potential churners:** Pinpoint customers exhibiting characteristics commonly associated with churn.
* **Understand churn drivers:** Gain insights into which factors most influence a customer's decision to leave.
* **Enable proactive intervention:** Provide actionable predictions to support targeted customer retention campaigns.

This project focuses on building a robust, interpretable, and maintainable predictive model using a visual, no-code/low-code approach provided by KNIME.

---

## Key Features & Deliverables

* **Visually Driven ML Workflow:** An intuitive, end-to-end machine learning pipeline for churn prediction.
* **Comprehensive Data Preparation:** Includes data access, initial exploration, cleaning, and sophisticated feature engineering.
* **Multiple Classification Models:** Implementation and comparative evaluation of various advanced machine learning algorithms.
* **Model Performance & Interpretability:** Detailed analysis of model accuracy, robustness, and insights into feature importance.
* **Interactive Data Exploration:** Integrated interactive visualizations for deeper data understanding and result presentation.

---

## Data Source

The dataset utilized for this project is `Telco_Customer_Churn.xlsx`. It comprises various customer attributes from a telecommunications company, including:

* **Demographic Information:** Gender, Senior Citizen status, Partner, Dependents.
* **Account Information:** Tenure (months customer has stayed), Phone Service, Multiple Lines, Internet Service, Online Security, Online Backup, Device Protection, Tech Support, Streaming TV, Streaming Movies, Contract Type, Paperless Billing, Payment Method, Monthly Charges, Total Charges.
* **Churn Status (Target Variable):** Indicates whether the customer churned (`Yes`) or not (`No`).

---

## Methodology

The entire project workflow is meticulously crafted within the KNIME Analytics Platform, following a structured approach:

### 1. Data Access & Initial Exploration

This initial phase involves reading the raw data and performing preliminary checks.

* **Step 1.1: Access the Data from File(s)**
    Receiving the data from the source as a CSV file containing database tables and building the workflow by accessing the data source file.
    ![Step 1.1 Access Data](assets/1_Access_Visualize_Dataset.png)
    *Reads the `Telco_Customer_Churn.xlsx` file using the CSV Reader node.*

* **Step 2.1: Visualization and Statistics of the Data**
    Exploring data statistics and filtering irrelevant data accordingly.
    ![Step 2.1 Visualization and Statistics](assets/1_Access_Visualize_Dataset.png)
    *Visualizes the dataset using the Data Explorer and explores summary statistics using the Statistics View. Irrelevant data is filtered using a Row Filter.*

### 2. Data Cleaning & Preprocessing

This crucial stage focuses on ensuring data quality and preparing it for modeling.

* **Step 2.2: Clean the Data**
    Filtering unwanted columns and handling missing values.
    ![Step 2.2 Clean Data](assets/2_Clean_Data.png)
    *Unwanted columns are filtered using the `Column Filter`. Missing values are explored and replaced with mean values in numerical columns using the `Missing Value` node, and columns with more than 5% missing values are removed.*

* **Step 2.3: Transform the Data**
    Converting categorical features into numerical formats suitable for machine learning algorithms and feature engineering.
    ![Step 2.3 Transform Data](assets/3_Transform_Data.png)
    *Categorical 'Yes/No' columns are converted to 0/1 numerical using `Category to Number` (Label Encoding). Other nominal features are converted using `One to Many` (One-Hot Encoding). A new feature, 'Tenure to Total Charges Ratio', is added using `Math Formula`. Finally, numerical columns are scaled using `Normalizer` (z-score normalization) to avoid bias.*

### 3. Exploratory Data Analysis (EDA) & Visualization

Gaining deeper insights into the data and preparing interactive components.

* **Step 3.1: EDA**
    Creating different visualizations and using a Correlation Matrix to uncover relationships between variables.
    ![Step 3.1 EDA](assets/4_0_EDA_Main.png)
    *Visualizations are created using various features, leading to the creation of an interactive dashboard. The Correlation Matrix node is used to understand variable relationships.*

    *Further components for interactive dashboards include detailed data processing and visual outputs:*
    ![Data Processing Component](assets/4_1_EDA_Module_Inside.png)
    ![Grouped Data Processing Component](assets/4_2_EDA_Module_Inside_Data_Processing.png)
    ![Interactive Bar Charts](assets/4_3_EDA_Module_Inside_Visuals3.png)

### 4. Machine Learning Model Development & Evaluation

This is the core of the predictive analysis, involving multiple model training and comparison.

* **Step 4.1: Model Training and Selection**
    The workflow partitions the dataset into training (70%) and testing sets, addressing class imbalance using SMOTE. It then trains and evaluates multiple classification models.
    ![Model Training and Evaluation](assets/5_Machine_Learning_Models_Training_Prediction_Eval.png)

    * **Class Imbalance Handling:** SMOTE (Synthetic Minority Oversampling Technique) is applied to the training data to avoid bias towards the majority class.
    * **Model Selection:**
        * **Logistic Regression Model:** Parameter optimization and cross-validation.
        * **Random Forest Model:** Parameter optimization, cross-validation, and feature importance calculation.
        * **XGBoost Tree Ensemble Model:** Parameter optimization, cross-validation, and feature importance calculation.
        * **SVM Model:** Parameter optimization and cross-validation.
    * **Model Comparison:** Results from cross-validation for all models are compiled, concatenated, and visualized (e.g., Scatter Plot for cross-validation results, Bar Chart for accuracy values) for comprehensive comparison.

---

## Results & Key Findings

After rigorous training and evaluation across various models:

* The **XGBoost Tree Ensemble Model** demonstrated superior performance, achieving an AUC-ROC score of **[e.g., 0.88]** and an accuracy of **[e.g., 85%]** on the unseen test set.
* **Key Churn Drivers:** Feature importance analysis (from Random Forest and XGBoost) highlighted that `Contract Type` (month-to-month contracts), `Tenure` (shorter tenure), `Monthly Charges` (higher charges), and `Internet Service (Fiber Optic)` are the most significant predictors of customer churn.
* The project provides a robust, data-driven framework for telecom operators to:
    * Proactively identify customers at high risk of churning.
    * Tailor retention strategies (e.g., targeted offers, personalized customer support).
    * Optimize resource allocation for marketing and customer service efforts.

*(**Action:** **CRITICAL:** Please fill in your actual model metrics and specific key findings here from your project/PPT to make this section accurate and compelling.)*

---

<h2 id="how-to-use-workflow">How to Use This Workflow:</h2>

To explore, understand, and run this project, you will need the **KNIME Analytics Platform** installed on your machine.

1.  **Download KNIME Analytics Platform:**
    * If you don't have KNIME installed, download it for free from the official website: [**Download KNIME**](https://www.knime.com/downloads)

2.  **Download the Workflow File (.knwf):**
    * Click the link below to download the workflow file directly:
        [**Download KNIME_ML_Telco_Cust_Churn_Workflow.knwf**](https://github.com/AmitKPandeyLabs/ML_P4_KNIME_Machine_Learning_Workflow_Telco_Cust_Churn/raw/main/KNIME_ML_Telco_Cust_Churn_Workflow.knwf)

    *(Note: The `raw/main` path ensures a direct download rather than viewing the file's content in the browser.)*

3.  **Download Additional Project Files (Optional but Recommended):**
    * **Project Requirements Document:** [Download Requirements.pdf](https://github.com/AmitKPandeyLabs/ML_P4_KNIME_Machine_Learning_Workflow_Telco_Cust_Churn/raw/main/Telco_Churn_Project_Requirements.pdf)
    * **Project Presentation:** [Download Presentation.pptx](https://github.com/AmitKPandeyLabs/ML_P4_KNIME_Machine_Learning_Workflow_Telco_Cust_Churn/raw/main/Telco_Churn_Project_Presentation.pptx)

    *(**Action:** Make sure these PPT/PDF files are in the `main` branch of your repo and update the links with their correct filenames and paths if different.)*

4.  **Import the Workflow into KNIME:**
    * Open KNIME Analytics Platform.
    * Go to `File > Import KNIME Workflow...`.
    * Select `Select archive file` and browse to the `.knwf` file you just downloaded.
    * Click `Finish`.

5.  **Explore and Run the Workflow:**
    * Once imported, the workflow will appear in your KNIME Explorer.
    * Double-click to open it.
    * You can execute the entire workflow (right-click on the workflow and select `Execute`) or run individual nodes/sections.

---

## Technologies Used

* **KNIME Analytics Platform:** Core platform for workflow development.
* **KNIME Extensions:** (If applicable, e.g., "KNIME Analytics Platform for Data Scientists," "KNIME Machine Learning Extension," "KNIME Interactive Reporting").
    *(**Action:** List any specific KNIME extensions that were critical for your project.)*

---

## Author

**[Your Name]** - Data Scientist | Machine Learning Engineer
* [Your LinkedIn Profile Link]
* [Your Portfolio Website Link]
* [Your GitHub Profile Link]

---

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details. *(**Action:** If you have a license file, ensure it's named `LICENSE.md` in your repo.)*
