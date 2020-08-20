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
With the both sets of data cleaned with some features engineered, it was time to explore the data.
- I first used .describe() to see the basic descriptive stats for central tendency and the overall dispersion of each fature.
- Then explored the continuous/discrete numeric variables using histograms, box-plots, and a correlation matrix/heatmap
- Next we dove into the categorical variables using bar plots
- Once I had a better sense of the distribution of each feature, I used pivot tables to compare them with the outcome variable 'Survived'

