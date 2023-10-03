# Predict-Customer-Churn-With-Machine-Learning

![](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/customer_churn_3.jpg)
---

## Using Decision Tree Model, Random Forest, and XG Boosting to predict Customer Churn for Y Bank


![](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Rf%20tree.png)


## INTRODUCTION
A machine learning project to determine the probability of customer churn at Y bank using an already existing dataset for analysis and a new customer dataset for prediction Then prepare a visualization to present findings to stakeholders on factors that contribute to customer churn and customers who are at the risk of churning for appropriate immediate action.

**_Disclaimer_**: _All datasets and reports do not represent any company, but just a dummy dataset to perform machine learning algorithms and showcase several functionalities of Python Libraries and Power BI._ 

The dataset can be downloaded below
- [Customer churn raw data](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/churn%20raw%20data.txt)
- [New Customer Dataset](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/new%20unseen%20data.txt)

## PROBLEM STATEMENT 
1.	Use existing dataset to determine factors that caused a customer to churn
2.	Predict customers who are at risk of churning with the new dataset



## SKILLS / CONCEPT DEMONSTRATED
Python and Power BI skills were used for this project
The following Python Libraries were used
-	Pandas, Numpy, matplotlib, seaborn
-	Exploratory Data Analysis
-	Standardization, Creating dummies
-	Machine learning models: Decision Tree, Random Forest, XGBoost.

The following Power BI concepts were put in place
-	Implicit Measures
-	Data Modelling
-	Filters


## Python Documentation
The full Python document can be found on the jupyter notebook [here](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Churn_With_Decison_Tree.ipynb)

However I'll be giving a brief summary of the processes involved in this analysis.
- Imported the Necessary Libraries needed for the analysis
- Loaded the CSV file
#### EXPLORATORY DATA ANALYSIS 
      - Checked for the size of the data
      - Number of unique values (distinct values)
      - Checked for any missing values and ofcourse datatype
      - Checked for correlation between variables using heatmap (didn't find any promising result)
      - Then I checked using a pair plot and could gather some insights from it (Age&Creditscore),(Age&EstimatedSalary),(Balance&EstimatedSalary)
      - Checked to see how categorical variables varied with the customer churn feature
 
#### MODEL PREPROCESSING 
- Created dummy variables for categorical values
- Performed a MinMax scaling to standardize certain features to avoid overfitting of data - Now the dataset was ready for modeling
- Split dataset into train and test data

#### MODEL DESIGN
  Since the dataset had an output/target variable that was binary and several input variables, machine learning models that was quite best fit for this data would include:
  - Decision Tree
  - Random Forest
1. DECISION TREE MODEL
   - Created variable for decision tree
   - Chose required features for the model with a depth of 4
   - Tried to import Graphviz and pydotplus in order to visualize decision tree, but there seemed to be an issue with the PATH of installation on my system, do try it, it could work on yours
   - Next, I calculated feature importnace for each feature, trying to see the how each feature had an impact on the target variable(Customer Churn)
   - Age, No of Products and IsActiveMember seem to be the top 3 features that had more impact on the target variable
   - Now, I checked for accuracy of the model which was quite impressive with a result of 85.1% on the test data
   - Then I plotted the confusion matrix to see how many percent of churn was predicted correctly, and only 42% was predicted corrected
   -![Screenshot (575)](https://user-images.githubusercontent.com/87811793/227467576-f036d4d8-b1d2-4500-846f-94edc1e2d076.png)
   
   _Definitely this model needs improving_ 
   THUS !!
   
   #### RANDOM FOREST
   - Called out the random forest model, initialized a variable
   - Set up features and set the number of trees to 200 and criterion to entropy
   - Checked for accuracy of the model with was 100% for train and an improved 86.6% for a test model, better than the one gotten from decision tree
   - Checked confusion matrix and model was able to predict correctly 50% of churn  _much more better!!_
   -![Screenshot (577)](https://user-images.githubusercontent.com/87811793/227468879-aeb38fe2-a6fe-45c3-9434-f1f119f4a6b7.png)
       
      Tunning the model for a much more improved result was the way forward: could we see an improvement in the confusion matrix?
      ##### TUNNING RANDOM FOREST MODEL
      - Set up features by selecting the number of forests to 200 
      - Number of features between 1, sqrt and log2
      - Depth between None, 2, 3, 4, 5.
      - Created a for loop to print out accuracy and plot confusion matrix -which it did, but apparently there was no improved result to the initial model.
      - Thus XG Boosting

  #### XG BOOSTING
  I tried to install XGBoost, but issues with GPU denied me, but it didn't stop the analysis
  - Determined the best parameter needed for the model
  - Created a variable finall_model to run the best parameter
  - I tried the model and plotted the confusion matrix, but I only got 45% of churn correctly
    ![Screenshot (579)](https://user-images.githubusercontent.com/87811793/227476355-28da488f-3fe0-428d-80be-0d678cc73270.png)



Having tried these methods, I had to go for the model that produced the best result for me which was the initial Rnadom forest model without tunning.

### MODEL DEPLOYMENT
- Loaded new customer dataset
- Used model to predict churn and the probability of churn.
- Exported dataset to be used for visualization


### VISUALIZATION
![](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/first_page.png)
![](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Trailing_page.png)
---
Used Power BI for visualization showing
- Number of Customers
- Number of Possible Churns
- Relationship between AGE and creditScore, NumberOfProducts,  Balance, ActiveMembers (_Used Feature Importance justify showcasing this Viz_)
- Showcased Prediction churn by location
- Table to with conditional formatting to show the customer who are at the risk of churning.

You can download PDF version of the report [here](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Churn%20Prediction%20Dashboad.pdf)
Check out the Power BI report [here](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Churn%20Prediction%20Dashboad.pbix)

## RECOMMENDATION AND CONCLUSION
- From the report, it is clear that customers between the ages of 40 and 60 are most likely to churn.
- Customers who have three or four Number of Products with the bank are very likely to churn, and customers with one product but between the ages of 40 and 60 are also likely to churn.
- Customers who have a balance between $100k and $200k in the age bracket of 40 to 60 are likely to churn.
- Most churn customers are from Germany and most loyal customers are from France
- Customers who are not active are definitely going to churn.
- Customers below 30 and above 60 are loyal customers
- So, in order to improve this, a strategy has to be put in place to entice target customers (ages 40–60) to stay with the bank, like a low interest rate on loans.

## Thank You
![](https://github.com/charlezvictor/Sales_Analysis_Viz/blob/main/Thank%20you.jpg)




### I'm available to answer any questions and receive any recommendations you have concerning this project.
#### Let's connect on [Linkedin](https://www.linkedin.com/in/victor-onyeaghala-08a909167/) and on [Twitter](https://www.twitter.com/_char_lez)

Credits: Data 360 YP (YouTube Channel)
100% Data Science educational channel
