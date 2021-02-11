### Titanic Survivor Prediction Overview
- Created: A model that predicts which passengers survived the sinking Titanic
- Purpose: To practice data science in Python and showcase the capabilities of various predictive modeling techniques
- - Note: As the outcome occurred in the distant past, there is little purpose beyond the academic.
- Performance: Overall Accuracy of survival (1 - survived | 0 - not-survived) was roughly over 77%
- Best Model: Soft Voting Classifier Enesemble of all trained (non-baseline) models
- Data: Train and Test data set provided by Kaggle
- Features: All features within the data set were extrapolated form the Titanics official passenger register

### Resources Used
- Language: Python Version - 3.7
- IDEs: Jupyter Notebook
- Packages: Pandas, Numpy, Matplotlib, Seaborn, Sklearn, XGBoost, Time, Missingno 
- For Web Framework: pip install -r requirements.txt
- Titanic Challenge Notebook: https://www.kaggle.com/startupsci/titanic-data-science-solutions
- Titanic Challenge Notebook:   https://www.kaggle.com/miguelquiceno/titanic-eda/execution
- Ken Jee's Analysis Youtube:    https://www.youtube.com/watch?v=I3FBJdiExcg&t=371s

### Data Collection
- Downloaded train.csv, test.csv, and gender_submission.csv (Note: gender_submission.csv was sample submisison set for use in submitting to the competition on Kaggle.com)
- The following serves as Data Dictionary for train.csv and test.csv (minus the 'survival' column)

| Variable      | Definition              | Key                      |
| :---          |       :----:            |                     ---: |
| survival      | survived                | 0 = No <br> 1 = Yes          |
| pclass        | Ticket class            | 1 = 1st <br> 2= 2nd <br> 3 = 3rd |
| PassengerId   | Passenger ID Code       |                          |
| Name          | Passenger name and title|                          |
| sex           | Sex                     |                          |
| Age           | Age in years            |                          |
| sibsp         | # of siblings/spouses <br> aboard the Titanic       |                          |
| parch         | # of parents/children <br> aboard the Titanic       |                          |
| ticket        | Ticket number           |                          |
| fare          | Passenger fare          |                          |
| cabin         | Cabin number            |                          |
| embarked      | Port of Embarkation     | C = Cherbourg <br> Q = Queenstown <br> S = Southampton                         |

Variable Notes
1. pclass: A proxy for socio-economic status (SES)
-1st = Upper
-2nd = Middle
-3rd = Lower

2. sibsp: The dataset defines family relations the following way...
- sibling = brother, sister, stepbrother, stepsister
- spouse = husband, wife (mistresses and fiancés were ignored)

3. parch: The dataset defines family relations in the following way...
- Parent = mother, father
- Child = daughter, son, stepdaughter, stepson (Note: Some children travelled only with a nanny, therefore parch=0 for them.)

4. Age: Age is fractional if less than 1. 

### Data Preprocessing
 #Data Cleaning
 The following lists the actions taken during this step;
 1. Data Correction
 - Remove NULLS: drop embarked nulls since there are only 2
 - Drop Columns: Cabin was dropped due to low data volume
 2. Data Completion
 - Impute NULLS: Age used the mode in this case 4 minus the median = 24.
 - Add Missing Columns: Disparities in factor level between train and test set lead to a need to harmonize the columns
 3. Data Convertion
 - Normalize Fare: used log transformation for exponential distribution
 - Create Dummy Variables: Convert factors to numeric type 
 - Scale Variables: To mitigate issue of over effect from large numeric values the data was scaled to a standard distribution
 -- Note: the unscaled data was also kept to produce models and determine the improvement, if any, from scaling the data

 #Feature Engineering
 1. Parsed Passenger Title: Created a title feature from the passenger 'name' registry to track correlation of surival with passenger title
 2. Parsed Cabin letter: Created cabin_letter feature to see if a passengers cabin section correlates with survival

### Data Exploration
With both sets of data cleaned with some features engineered, it was time to explore the data.
- I first used .describe() to see the basic descriptive stats for central tendency and the overall dispersion of each feature.
- Then explored the continuous/discrete numeric variables using histograms, box-plots, and a correlation matrix/heatmap
- Next we dove into the categorical variables using bar plots
- Once I had a better sense of the distribution of each feature, I used pivot tables to compare them with the outcome variable 'Survived'


![EDA Barplot!](https://github.com/cumeakunne/titanic_survivor_pred_repo/blob/master/bar_pic.png)
![EDA Heatmap!](https://github.com/cumeakunne/titanic_survivor_pred_repo/blob/master/heatmap_pic.png)
![EDA_Box Table!](https://github.com/cumeakunne/titanic_survivor_pred_repo/blob/master/box_pic.png)

### Data Model Building
From the data exploration and pre-processing, we use a final scaled and unscaled training set to build our models. We built 11 models; 2 baseline models, 7 robust methods, followed by a final hard and soft voting ensemble. With a binary target variable, the survival prediction accuracy score served as our evaluation metric.

Baseline Models:
1. Gaussian Naive Bayes
- Scaled Training Score: 72.11% 
- Unscaled Training Set: 73.79%
2. Classification Tree
- Scaled Training Score: 79.41% 
- Unscaled Training Set: 79.42%

Robust Models:
3. Logistic Regression
- Scaled Training Score: 82.57% 
- Unscaled Training Set: 82.46%
4. Random Forest
- Scaled Training Score: 81.78% 
- Unscaled Training Set: 81.89%
5. K-Nearest Neighbors
- Scaled Training Score: 82.45% 
- Unscaled Training Set: 81.11%
6. Support Vector Classification
- Scaled Training Score: 83.13% 
- Unscaled Training Set: 82.23%
7. AdaBoost Classifier
- Scaled Training Score: 82.0% 
- Unscaled Training Set: 82.0%
8. Gradient Boost Classifier
- Scaled Training Score: 82.79% 
- Unscaled Training Set: 82.79%
9. XGBoost Classifier
- Scaled Training Score: 82.9% 
- Unscaled Training Set: 82.9%

Voting Classifiers:
10. Soft Vote
- Scaled Training Score: 83.46% 
- Unscaled Training Set: 83.91%
11. Hard Vote
- Scaled Training Score: 84.25% 
- Unscaled Training Set: 83.46%

### Data Model Performance
- The Soft Vote Ensemble produced the most accurate prediction at roughly 77%
- In otherwords, for a randomized sample of 10 passengers we can expect our model to correctly predict the survival outcome of 7 or 8 passengers.
- The accuracy score was determined by Kaggle's scoring system and returned after submitting the results of the soft voting ensemble.



