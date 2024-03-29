# Starbucks-Promotion-Strategy
- [Project Goal](#Project-Goal)
- [Project Workflow](#Pathway)
- [Results](#Results)
- [Discussion](#Discussion)
- [Licensing, Authors, Acknowledgements](#License)

## Project Goal <a name="Project-Goal"></a>
The goal of this project is to create a model that gives promotions to users based on their features' patterns. Specifically, the goal is to maximize the two metrics: Incremental Response Rate (IRR) and Net Incremental Revenue (NIR)

**Background:** The dataset provided in this portfolio exercise was originally used as a take-home assignment provided by Starbucks for their job candidates. The data for this exercise consists of about 120,000 data points split in a 2:1 ratio between training and test files. In the experiment simulated by the data, an advertising promotion was tested to see if it would bring more customers to purchase a specific product priced at $10. Since it costs the company 0.15 to send out each promotion, it would be best to limit that promotion only to those who are most receptive to the promotion. Each data point includes one column indicating whether or not an individual was sent a promotion for the product, and one column indicating whether or not that individual eventually purchased that product. Each individual also has seven additional features associated with them, which are provided abstractly as V1-V7.


**The tasks** 
1. Use the training data to understand what patterns in V1-V7 indicate that a promotion should be provided to a user
2. Maximize the metrics: <br>
   a. Incremental Response Rate (IRR): depicts how many more customers purchased the product with the promotion, as compared to if they didn't receive the promotion.<br>
   ![irr](img/irr.png)<br>
   
   b. Net Incremental Revenue (NIR): depicts how much is made (or lost) by sending out the promotion.<br>
   ![nir](img/nir.png)<br>

## Project Workflow <a name="Pathway"></a>
### Part 1: Hypothesis Testing 
- The experiment was conducted and labeled results were collected. I analyze the results to see if giving out promotions helps with IRR and NIR
- Analyze is done by calculating the two KPIs (IRR, NIR) generated after the experiment.
- Identifying the effect of promotion is done by testing the hypotheses with the bootstrap technique

**Invariant metric**: to test whether there is a statistically significant difference between the 2 groups' size.

![invariant](img/invariant_metric_hypo.png)<br>

**Evaluation metrics**: a hypothesis testing to evaluate whether promotions have a positive impact on increasing the IRR and NIR

![kpi](img/evaluation_metric_hypo.png)<br>

### Part 2: Build a Model 
- Select customers whose features (V1 - V7) will maximize the IRR and NIR, and give them the Promotion code (Treatment)
- This is a Feature Selection problem

## Conclusions and Results <a name="Results"></a>
### Hypothesis testing
- There is no significant difference in sample size between the control and treated groups
- Giving out promotions will drive up the purchase rate. However, there is no net positive revenue generated.
### Classification model
- The practical and best ML Promotion strategy utilizes **XGBoost**. This model produces IRR 0.0256, NIR = 87.15
- The best Promotion strategy is the custom model whose metrics are: IRR = 0.0212, NIR = 266.85

## Discussion <a name="Discussion"></a>
### 1. Dataset distribution

![distribution](img/promotion_dist.png)<br>
Figure 1. The distribution of control (no promotion) and treated (received promotion) groups with regard to customer's purchase. 

This dataset is highly imbalanced. The number of customers not making purchases are much more than those who do, regardless of whether they receive promotional offers or not. For this reason, standard ML algorithms applying to the given data set will have a tendency to assign No-Promotion to all customers than trying to classify. 

Thus, SMOTE method was applied to resample and balance the data set.

### 2. Model choices
The Jupyter notebook `Startbucks Promotion Strategy_NP` entails two approaches.
- The first approach is a custom strategy that targets specific features. If satisfied, the user will receive the promotion. This approach only works if there is a manageable amount of features
- The second approach is applying an ML model. I compared the performance of 3 models: Logistic regression, Balanced random forest classifier, and XGBoost. XGBoost performed best resulting in the highest IRR value and a positive NIR value.

### 3. Suggestions
The following suggestions can improve the model: <br>
a. A more balanced data set<br>
b. Or other classifiers for an imbalanced data set

## Licensing, Authors, Acknowledgements <a name="License"></a>
* Starbucks for providing the datasets and project goal
* [Udacity](https://www.udacity.com/) for instructions
* Author: [Nguyen Pham](https://github.com/Az-otrope)

