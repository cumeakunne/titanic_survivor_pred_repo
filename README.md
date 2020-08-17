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

