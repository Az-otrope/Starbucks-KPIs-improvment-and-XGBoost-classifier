# Starbucks-Promotion-Strategy
- [Project Goal](#Project-Goal)
- [Project Pathway](#Pathway)
- [Installation](#Installation)
- [File Descriptions](#File-Descriptions)
- [Instructions](#How-To-Run-This-Project)
- [Results](#Results)
- [Discussion](#Discussion)
- [Licensing, Authors, Acknowledgements](#License)

## Project Goal <a name="Project-Goal"></a>
The goal of this project is to create a model that gives the promotion to users based on their features' patterns. Specifically, the goal is to maximize the two metrics: Incremental Response Rate (IRR) and Net Incremental Revenue (NIR)

**Background:** The dataset provided in this portfolio exercise was originally used as a take-home assignment provided by Starbucks for their job candidates. The data for this exercise consists of about 120,000 data points split in a 2:1 ratio among training and test files. In the experiment simulated by the data, an advertising promotion was tested to see if it would bring more customers to purchase a specific product priced at $10. Since it costs the company 0.15 to send out each promotion, it would be best to limit that promotion only to those that are most receptive to the promotion. Each data point includes one column indicating whether or not an individual was sent a promotion for the product, and one column indicating whether or not that individual eventually purchased that product. Each individual also has seven additional features associated with them, which are provided abstractly as V1-V7.


**The tasks** 
1. Use the training data to understand what patterns in V1-V7 to indicate that a promotion should be provided to a user
2. Maximize the metrics: <br>
   a. Incremental Response Rate (IRR): depicts how many more customers purchased the product with the promotion, as compared to if they didn't receive the promotion.<br>
   b. Net Incremental Revenue (NIR): depicts how much is made (or lost) by sending out the promotion.<br>

Formulas to calculate IRR and NIR are detailed in the Jupyter notebook.

## Project Pathway <a name="Pathway"></a>
### Part 1: Hypothesis Testing 
- The experiment is finished. Analyze it to see if giving out promotion helps with IRR and NIR
- Analyze = calculate the experiment's IRR, NIR
- Identify the effect of promotion = Test the hypothesese by boostrap 

### Part 2: Build a Model 
- Select customers whose features (V1 - V7) will maximize the IRR and NIR, give them the Promotion code (Treatment)
- This is a Feature Selection problem

## Installation <a name="Installation"></a>
The following packages and versions are used in this jupyter notebook. Any newer versions should work. 
| Package  | Version |
| ------------- | ------------- |
| Python  | 3.8.5  |
| Pandas  | 1.1.3  |
| Numpy   | 1.19.2 |
| Matplotlib | 3.3.2|
| imblearn   | 0.0  |
| xgboost | 1.5.2  |

## File Description <a name="File-Descriptions"></a>
There are 5 files in this repository. <br>
1. Two original training and test datasets are provided in `.csv` files <br>
2. A jupyter notebook `.ipynb` includes the process of reading in, preprocessing, and modeling the dataset. <br>
3. A test `.py` file provided by Udacity
4. A README.md file as a brief look at this repository.

## Instructions <a name="How-To-Run-This-Project"></a>
* Execute the codes in this notebook and follow along the insights to understand the decisions made throughout the process.

## Results <a name="Results"></a>
- The best Promotion strategy is the custome model whose metrics are: IRR = 0.0212 , NIR = 266.85
- The practical and best ML Promotion strategy utilizes XGBoost. This model produces IRR 0.0256, NIR = 87.15

## Discussion <a name="Discussion"></a>
### 1. Dataset distribution
This dataset is highly imbalanced. The amount of customers not making purchases are much more than thoes do. For this reason, standard ML algorithms running directly on the given data set will have a tendency to assign No-Promotion to all customers than trying to classify. 

SMOTE method was applied to resample and balance the data set.

### 2. Model choices
The jupyter notebook `Startbucks Promotion Strategy_NP` entails two approaches.
- First approach is a custom strategy which targets specific features. If statisfies, the user will receive the promotion. This approach only works if there is a managable amount of features
- Second approach is applying a ML model. I compared the performance of 3 models: Logistic regression, Balanaced random forest classifier, and XGBoost.

### 3. Suggestions
The following suggestions can improve the model: <br>
a. A more balanced data set<br>
b. Or other classifiers for imbalanced data set

## Licensing, Authors, Acknowledgements <a name="License"></a>
* Starbucks for providing the datasets and project goal
* [Udacity](https://www.udacity.com/) for instructions
* Author: [Nguyen Pham](https://github.com/Az-otrope)

