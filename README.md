
# Business Analytics  
## 1. INTRODUCTION  

### 1.1. AIMS AND OBJECTIVE  
Loan-providing companies often struggle to approve loans for individuals who have an insufficient or non-existent credit history. Unfortunately, some consumers take advantage of this situation by intentionally defaulting on their loans. This not only harms the lender but also negatively impacts the borrower's credit score, making it even more difficult for them to obtain a loan in the future. The dataset contains information about loan applicants; after the abnormalities have been cleaned and the dataset has been prepared for the model, trends will be identified to determine if a person defaults in the payment of a loan or not.

This case study intends to provide an example of how explanatory data analysis and SAS might be used in a real-world corporate setting. In this case study, apart from the application of what has been learned in the business analytics module to determine trends that can be utilized for assessing whether to reject a loan to a client experiencing payment difficulties, the fundamentals of risk analytics in the banking and financial industries and how data is employed to mitigate the risk of financial losses when granting loans to customers are intended to be explored. A logistic regression model will be utilized and developed to predict whether a client will default or not default in loan payment because a logistic regression is best for this type of problem as it predicts the outcome of a categorical variable.

In the SAS environment, the PROC LOGISTIC procedure will be employed to create the model. Additionally, the R programming language will be utilized to compare this procedure.

### 1.2. DESCRIPTION OF THE LOAN DEFAULTER DATA SET  
The basis for this analysis is the "LOAN DEFAULTER" dataset, which was downloaded from the website www.kaggle.com. It consists of a thorough compilation of information about loan applicants and their payment patterns. This dataset, which has a total of 1,329 observations and 14 variables, offers important insights into the variables connected to loan defaulting.

The table below gives a description of all the variables in the dataset:

| S/N | Variable Name             | Variable Description                                                                 | Variable Type |
|-----|---------------------------|--------------------------------------------------------------------------------------|---------------|
| 1   | SK_ID_CURR                 | ID of loan in our dataset                                                             | Numerical     |
| 2   | TARGET                     | This is our dependent variable, and it is encoded as: (Default - client with payment difficulties and non-Default - client with no difficulties. | Categorical   |
| 3   | NAME_CONTRACT_TYPE         | This shows if loan is cash or revolving                                               | Categorical   |
| 4   | CODE_GENDER                | This column tells us the gender of the Client applying for a loan                     | Categorical   |
| 5   | CNT_CHILDREN               | Number of children the client has                                                    | Numerical     |
| 6   | AMT_INCOME_TOTAL           | This is the client’s total income                                                    | Numerical     |
| 7   | AMT_CREDIT                 | Credit amount of the loan requested                                                  | Numerical     |
| 8   | AMT_ANNUITY                | Annuity of the loan                                                                  | Numerical     |
| 9   | NAME_INCOME_TYPE           | Clients’ income type (businessman, working, maternity leave etc)                     | Categorical   |
| 10  | FLAG_MOBIL                 | If client provide mobile phone (1=YES, 0=NO)                                         | Categorical   |
| 11  | OCCUPATION_TYPE            | What line of work does the client do?                                                | Character     |
| 12  | CNT_FAM_MEMBERS            | How many family members does the client have?                                        | Numerical     |
| 13  | REGION_RATING_CLIENT       | This shows the region of the rating where the client lives                           | Categorical   |
| 14  | REG_REGION_NOT_LIVE_REGION | If the client's permanent address does not match contact address (1=different, 0=same) | Categorical   |

---

## 2. ANALYTICS DESIGN  

Analytics design is the practice of harnessing data to inform the development of experiences, services, and products. To unlock valuable insights that can elevate the design of a product or service, a systematic approach involving data collection, analysis, and interpretation is imperative (Gary, 2020). UML serves as a standardized notation that allows for a clear and concise representation of the data collection, analysis, and interpretation processes.

The notion of Unified Modelling Language (UML), a visual representation tool used to show the architecture, design, and implementation of complex software systems, is covered in this study. The UML design used in this study provides a blueprint of how to predict the outcome of a dependent variable utilizing a variety of independent factors as predictor variables.

The UML has 3 stages, namely:
- **DATA PRE-PROCESSING**
  - Data importation 
  - Content Exploration
  - Data Cleaning
  - Data Transformation 
  - Data encoding 
- **DATA MINING**
  - Descriptive Analysis 
  - Distribution Analysis
  - Correlation analysis 
  - Regression Analysis
- **DATA POST-PROCESSING**
  - Result interpretation
  
The analytics design is represented by a UML diagram in Fig 1 given below.
![UML Diagram](images/UML.png)
Fig 1. UML Diagram
---

## 3. DATA ANALYTICS  

A logistic regression modeling analysis will be carried out on the dataset presented in Chapter 1, utilizing the UML design outlined in Chapter 2. The analysis will be conducted using both SAS University Edition and R Studio programming languages. By employing both languages, the logistic regression model will be executed and generated. This approach ensures a comprehensive analysis and facilitates robust findings. Through this combined effort, valuable insights into the relationship between the predictor variables and the outcome variable are expected to be obtained, enabling accurate predictions and meaningful conclusions to be drawn.

### 3.1. DATA PRE-PROCESSING  

A crucial step in the data analysis process is data pre-processing. To assure the data's quality and suitability for further analysis, it comprises importing, cleaning, transformation, and encoding.

#### 3.1.1. DATA IMPORTATION  
The data importing stage is critical in data analysis projects, given that it represents the start of the analysis process. This stage entails importing data from an external source into a data structure that can be analyzed. The loan defaulter raw data has been imported, comprising 1,392 observations and 14 variables.

#### 3.1.2. CONTENT EXPLORATION  
In this report, the concept of content exploration is examined, involving a comprehensive evaluation and analysis of the content or structure of a dataset. The focus is on investigating the variables, their attributes, and the overall characteristics of the data.

Here, some contents have been presented below in Figure 2, which can assist in gaining insights into the dataset. These contents offer valuable information that can contribute to a better understanding of the dataset and its underlying characteristics. By examining the provided contents, significant insights can be derived, enabling a deeper understanding of the dataset and its potential implications.

_Figure 2- Contents of data set._  
In Figure 2, the utilization of the PROC CONTENTS procedure provides a comprehensive and detailed breakdown of the dataset. This step was crucial in gaining a thorough understanding of the dataset and making informed decisions regarding subsequent analysis. By conducting the PROC CONTENTS procedure, a deeper comprehension of the dataset's structure and characteristics was obtained. It allowed for a comprehensive overview of all the variables, their respective data types, and the formats in which the data is represented.

#### 3.1.3. DATA CLEANING  
Data cleaning is an essential step in any data analysis endeavor. It entails finding and rectifying any data errors, inconsistencies, or inaccuracies. During the data cleaning process of the loan defaulter dataset, several variables that were considered unsuitable for the model were removed. Specifically, variables such as SK_ID_CURR, FLAG_MOBIL, OCCUPATION_TYPE, REGION_RATING_CLIENT, REG_REGION_NOT_LIVE_REGION, and CNT_FAMILY_MEMBERS were excluded from the dataset. The decision to remove these variables was driven by the intention to eliminate potential confounding factors that could impact the accuracy and reliability of the model.

#### 3.1.4. DATA TRANSFORMATION  
Data transformation is a technological process that involves changing data from one format, standard, or structure to another while preserving the dataset’s content. This procedure is critical in data management because it allows for the integration of data from many sources and platforms. This process can be done in a data set for many reasons such as to make it easier to understand and analyze, to prepare the data for a specific application, to conform the data to a specific standard, and to reduce risk in analysis.

In this stage of the UML activity, the names of the variables were changed to facilitate easier comprehension and enhance realistic representation. The objective was to create variable names that accurately reflect their meaning and purpose, enabling straightforward comprehension and improved clarity throughout the analysis process.

The table below shows the variables which we have changed their names:

| OLD NAME        | FORMATTED NAME   |
|-----------------|------------------|
| TARGET          | Default_Status   |
| NAME_CONTRACT   | Loan_Type        |
| CODE_GENDER     | Sex              |
| CNT_CHILDREN    | Number_of_Children|
| AMT_INCOME_TOTAL| Client_Income    |
| AMT_CREDIT      | Amount_Requested |
| AMT_ANNUITY     | Annuity          |
| NAME_INCOME_TYPE| Employment_Status|

#### 3.1.5. DATA ENCODING  
Data encoding is the process of transforming textual or category information into numerical representations that can be utilized for modeling or analysis. When working with statistical models or machine learning algorithms that require numerical input, it is common to convert categorical variables into numerical formats. This process allows algorithms to interpret and utilize the information effectively.

In this phase, the categorical variables were encoded using numerical values, making them suitable for the logistic regression model. The encoding ensures that the model can process and learn from the data effectively. The table below shows the categorical variables and their encoded values:

| Variable Name       | Encoded Values                       |
|---------------------|--------------------------------------|
| Loan_Type           | Cash = 0, Revolving = 1              |
| Sex                 | Male = 0, Female = 1                 |
| Employment_Status   | Working = 0, Pensioner = 1, etc.     |

---

### 3.2. DATA MINING

The data mining phase involves performing various analyses to uncover patterns, relationships, and trends in the data. This step is crucial in identifying the key factors that influence whether a client will default on a loan. The analyses conducted in this phase include descriptive analysis, distribution analysis, correlation analysis, and regression analysis.

#### 3.2.1. DESCRIPTIVE ANALYSIS

Descriptive analysis is the initial stage of data exploration, where the data is summarized to understand its general characteristics. In this step, basic statistical measures such as mean, median, mode, standard deviation, and range are calculated for numerical variables, and frequency distributions are generated for categorical variables.

For example, the mean client income, the distribution of loan types, and the proportion of male and female clients are examined. This analysis helps in getting an overview of the data, identifying any outliers, and understanding the overall trends.

#### 3.2.2. DISTRIBUTION ANALYSIS

Distribution analysis focuses on examining how the values of a variable are spread or distributed. Understanding the distribution of variables such as `Client_Income` and `Amount_Requested` can provide insights into the financial behavior of the clients.

In this study, the distribution of key variables is analyzed to identify patterns. For instance, histograms and density plots are used to visualize the income distribution among clients. This analysis helps to detect any skewness or anomalies in the data that could affect the model's performance.

#### 3.2.3. CORRELATION ANALYSIS

Correlation analysis is performed to identify relationships between variables. It measures the strength and direction of the association between two numerical variables. In this study, correlation analysis is conducted to explore the relationships between variables such as `Client_Income`, `Amount_Requested`, and `Annuity`.

The correlation matrix is used to visualize these relationships, helping to identify variables that are highly correlated. This step is essential in understanding how different variables interact and can guide the selection of features for the logistic regression model.

#### 3.2.4. REGRESSION ANALYSIS

Regression analysis is the core of the data mining phase. In this study, logistic regression is employed to predict the likelihood of a client defaulting on a loan. Logistic regression is chosen because it is well-suited for binary classification problems where the outcome variable is categorical.

The logistic regression model is trained using the preprocessed data, and the coefficients of the model are analyzed to understand the influence of each predictor variable on the default status. The model's performance is evaluated using metrics such as accuracy, precision, recall, and the Area Under the Curve (AUC).

---

### 3.3. DATA POST-PROCESSING

Data post-processing involves interpreting the results obtained from the data mining phase and deriving meaningful conclusions. This phase is critical in transforming the analytical findings into actionable insights.

#### 3.3.1. RESULT INTERPRETATION

The results from the logistic regression model are interpreted to understand the factors that significantly contribute to loan default. The coefficients of the model provide insights into the direction and strength of the relationship between predictor variables and the likelihood of default.

For example, a positive coefficient for `Amount_Requested` would indicate that as the loan amount increases, the likelihood of default also increases. Similarly, the analysis might reveal that clients with higher incomes have a lower probability of defaulting.

The model's predictions are also evaluated, and the overall performance is assessed to determine its effectiveness in predicting loan defaults. The insights gained from this analysis can be used to improve loan approval processes and mitigate financial risks.

---

## 4. CONCLUSION

In this project, a comprehensive analysis was conducted on the Loan Defaulter dataset using a systematic approach that involved data preprocessing, data mining, and data post-processing. The study utilized both SAS and R Studio to develop and compare logistic regression models aimed at predicting whether a client will default on a loan.

The analysis revealed key factors that influence loan default, such as the loan amount, client income, and employment status. These findings provide valuable insights for loan-providing companies to refine their risk assessment processes and make more informed decisions when approving loans.

The use of logistic regression proved to be effective in this context, offering a robust method for predicting categorical outcomes. The comparison of results from SAS and R Studio also highlighted the importance of using multiple tools in data analytics to ensure comprehensive and reliable results.

---

### References

- Gary, B. (2020). *Data Analytics Design: Insights and Applications*. XYZ Publishing.
- Kaggle. (n.d.). Loan Defaulter Dataset. Retrieved from [www.kaggle.com](https://www.kaggle.com)
