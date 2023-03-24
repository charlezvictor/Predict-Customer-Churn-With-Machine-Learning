# Predict-Customer-Churn-With-Machine-Learning

![](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/customer_churn_3.jpg)
---

## Using Decision Tree Model, Random Forest and XG Boosting to predict Customer Churn for Y Bank


![](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Rf%20tree.png)


## INTRODUCTION
A Machine learning project to determine probability of customer churn at Y bank using already existing dataset for analysis and a new customer dataset for prediction. Then preparing Visualization to present findings to satkeholders on factor thatcontirbutes to customer churn and customer who are at the rsik of churning for appropriate immediate action.

**_Disclaimer_**: _All datasets and reports do not represent any company, but just a dummy dataset to perfrom machine learning algorithms and showcase several functionalities of Python Libraries and Power BI._ 

Dataset can be downloaded below
- [Customer churn raw data](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/churn%20raw%20data.txt)
- [New Customer Dataset](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/new%20unseen%20data.txt)

## PROBLEM STATEMENT 
1.	Use existing dataset to determine factors that caused a customer to churn
2.	Predict customer who are at the risk of churning with new dataset



## SKILLS / CONCEPT DEMONSTRATED
Python and Power BI skills were used for this project
The following Python Libraries were used
-	Pandas, Numpy, Matplotlib, seaborn
-	Exploratory Data Analysis
-	Standardization, Creating dummies
-	Machine learning models : Decision Tree, Random Forest, XGBoost.

The following Power BI concepts were put in place
-	Implicit Measures
-	Data Modelling
-	Filters


## Python Documentation
The full python document can be found on the jupyter notebook [here](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Churn_With_Decison_Tree.ipynb)

But I'll be giving a brief summary of processes involved in this analysis.
- Imported the Necessary Libraries needed for the analysis
- Loaded the csv file
#### EXPLORATORY DATA ANALYSIS 
      - Checked for size of data
      - Number of unique values (Distiinct Values)
      - Checked for any missing values and ofcourse datatype
      - Checked for correlation between variables using heatmap (didn't find any promising result)
      - Then I checked using pairplot and could geberate some insights from it (Age&Creditscore),(Age&EstimatedSalary) ,(Balance&EstimatedSalary)
      - Chcked to see how categorical variables varied with the customer churn feature
 
#### MODEL PREPROCESSING 
- Created dummy variables for categorical values
- Performed a MinMax scaling to standardize certain features to avoid overfitting of data - Now dataset was ready for modelling
- Split dataset into train and test data

#### MODEL DESIGN
  Since dataset had a output/target varaibale that was binary and several input variables, machine learning models that was quite best fit for this data would include:
  - Decision Tree
  - Random Forest
1. DECISION TREE MODEL
   - Created variable fro decision tree
   - Chose required features for the model with a depth of 4
   - Tried to import graphviz and pydotplus in order to visualize decison tree, but there seemed to be an issue with the PATH of installion on my system, but do try it, it could work on yours
   - Next, I calcluated feature importnace for each feature, trying to see the how each feature had an impact on the target variable(Customer Churn)
   - Age, No of Products and IsActiveMember seems to be the top 3 features that had mor imoact on the target variable
   - Now, I checked for accuray of the model which was quite impressive with a result of 85.1% on test data
   - Then I plotted the confusion matrix to se how many percent of churn was predicted correctly, and only 42% was predictied corrected
   -![Screenshot (575)](https://user-images.githubusercontent.com/87811793/227467576-f036d4d8-b1d2-4500-846f-94edc1e2d076.png)
   
   _Definitely this model needs improving_ 
   THUS !!
   
   #### RANDOM FOREST
   - Called out the random forest model, initialized a variable
   - Set up features and set the number of trees to 200 and criterion to entropy
   - Checked for accuracy of model with was 100% for train and an improved 86.6% for test model, better than the one gotten from decsion tree
   - Checked confusion matrix and model was abel to predict correctly 50% of churn  _much more better!!_
   -![Screenshot (577)](https://user-images.githubusercontent.com/87811793/227468879-aeb38fe2-a6fe-45c3-9434-f1f119f4a6b7.png)
       
      Tunning the model for a much more imporved result was the way forward : could we see an improvement in the confusion matrix?
      ##### TUNNING RANDOM FOREST MODEL
      - Set up features by selecting number of forest to 200 
      - Number of features between 1,sqrt and log2
      - Depth between None, 2, 3, 4, 5.
      - Created a for loop to print out accuaracy and plot confusion matrix -whcih it did, but apparently there was no improved result to the initial model.
      - Thus XG Boosting

  #### XG BOOSTING
  - Tried to install  XGboost, but issues with GPU denied me, but it didn't stop analysis
  - Determine best parameter neded for the model
  - Created a variable finall_model to run the best paramenter
  - Tried the model and plotted confusion matrix, but I only got 45% of churn correctly
    ![Screenshot (579)](https://user-images.githubusercontent.com/87811793/227476355-28da488f-3fe0-428d-80be-0d678cc73270.png)



Having tried these methods, I had to go for the model that produced the best result for me which was the initial Rnadom forest model without tunning.

### MODEL DEPLOYMENT
- Loaded new customer dataset
- Used model to predict churn and probability of churn.
- Exported dataset to be used for visualization


### VISUALIZATION
![](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/first_page.png)
![](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Trailing_page.png)
---
Used Power BI for visualization showing
- Number of Customers
- Number of Possible Churns
- Relationship between AGE and creditScore, NumberOfProducts,  Balance, ActiveMembers (_Used Feature Importance jsutify showcasing this Viz_)
- Showcased Prediction churn by location
- Table to with conditinal formatting to show customer who are at the rsik of churnning.

You can download pdf cersion of the report [here](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Churn%20Prediction%20Dashboad.pdf)
Check out the Power BI report [here](https://github.com/charlezvictor/Predict-Customer-Churn-With-Machine-Learning/blob/main/Churn%20Prediction%20Dashboad.pbix)

## RECOMMENDATION AND CONCLUSION
- From the report it is clear that customers between the ages of 40 and 60 are most likely to churn.
- Customer who ahve 3 or 4 Number of Products with the bank are very much likely to churn,a nd customer with one product but between the ages of 40 and 60 are also likely to churn.
- Customers who have a balance between 100k and 200k, between the age bracket of 40 to 60 are likely to churn.
- Most chrun customers are from Germany and most loayl customers are from France
- Customers who are not active are definitely going to churn.
- Customers below 30 and above 60 are loyal customers
- So, in order to improve this, a startegy has to be put in place to entice target cusotmers (ages 40-60) to stay with the bank - like low interest rate on loans.

## Thank You
![](https://github.com/charlezvictor/Sales_Analysis_Viz/blob/main/Thank%20you.jpg)




### I'm available to answer any questions and receive any recommendations you have concerning this project.
#### Let's connect on [Linkedin](https://www.linkedin.com/in/victor-onyeaghala-08a909167/) and on [Twitter](https://www.twitter.com/_char_lez)

Credits - Data 360 YP (Youtube Channel)
100% Data Science educative channel
