## Project Details
AnomaData (Automated Anomaly Detection for Predictive Maintenance)

## Problem Statement:
Many industries need predictive maintenance solutions to reduce risks and gain actionable insights by processing equipment data.<br/>
Although system failure is a general issue that can occur in any machine, predicting the failure and taking steps to prevent such failure is most important for any machine or software application.<br/>
Predictive maintenance evaluates the condition of equipment by performing online monitoring. The goal is to perform maintenance before the equipment degrades or breaks down.<br/>
This Capstone project aims to predict the machine breakdown by identifying the anomalies in the data.<br/>
The data we have contains about 18000+ rows collected over a few days. The column ‘y’ contains the binary labels, with 1 denoting there is an anomaly. The rest of the columns are predictors.<br/>

## Quick Overview:
ANOMA is a standard practice popular among industries to predict maintenance solutions to reduce risks and gain actionable insights by processing equipment data. <br/>
There are mainly three types of maintenance measures:
<ol> 
  <li>
Corrective Maintenance- <br/>
It’s a traditional method that allows maximum equipment exploitation but simultaneously implies unreliability as the failure's time and impact are unknown. This measure is expensive and time-consuming. 
Here the maintenance is planned upon the failure of the machine.<br/>
  </li>
  <li>
    Preventive Maintenance- <br/>
    It’s a practice to systematically maintain equipment, systems or machines to increase reliability. The maintenance is cyclic. This method is effective if coincidently, the planned maintenance occurs just before the failure.  <br/><br/>
    Both 1 and 2 methods are vulnerable as they are unable to predict the factors/ probability of failure. <br/>
  </li>
  <li>
    Predictive- <br/>
    To overcome the above-mentioned shortcomings industries have implemented predictive maintenance. Using ML models, the industries can predict failures and plan maintenance accordingly. <br/>
    Upon deep diving into predictive maintenance, the most common machine learning used are decision tree models. <br/>
  </li>
</ol>

## Data sources:
Sample data shared in the problem statement - Anoma_data.csv <br/>
Upgrad learning videos to lay the formulas <br/>
SMOTE analysis - GeekForGeek - <a href="https://www.geeksforgeeks.org/ml-handling-imbalanced-data-with-smote-and-near-miss-algorithm-in-python/ "> click here </a>

## Explanation:
The libraries used for the analysis are pandas, numpy, matplotlib, seaborn,sklearn, imblearn
<ol>
  <li>Started with Data Cleaning methods ensuring no null values and proper data types. For example the input variable has data value in the form ”20.14”.Hence, the data type of this variable should be float. </li>
  <li>The dataset contains a time column. It is insignificant in the decision tree analysis. Hence, removed this column from our training</li>
  <li>Followed by EDA, where the main motive was freeing the data of any outliers. Using Matplotlib library, populated histograms of each input variable. Observed distribution and ran filters on the entire data based on the interquartile range, ensuring there is no major outliers. </li>
  <li>There are 60 input variables shared in the data. Running the model training with all variables will make the model complex. Hence, ran a feature selection to reduce the number of variables. I chose features above 20 points. </li>
  <li>The share of anomalies row compared to overall ros is very small. To balance the imbalance or counter biases, ran SMOTE on the entire dataset. Now, our data is finally ready for model training. </li>
  <li>Divided the dataset into input and output dataframes. Further, split the data into test and train. The motive is to get high recall and accuracy values from the model upon validating against test dataframes with the least complexity. </li>
  <li>Tuning the max depth, I ran the Decision Tree Model and Random Forest Model on the train data</li>
  <li>Based on recall, accuracy values and complexity, I concluded with the final result</li>
</ol>

## Conclusion:
I ended by trying 6 permutations of model training with the maximum depth as 3, 5 and 7, and with the two models, i.e, Decision Tree and Random Forest. <br/>

The random forest result with max depth 5 has a recall value of 81.6% and an accuracy of 81.5%<br/>

The random forest result with max depth 5 has a recall value of 84.6% and an accuracy of 84.5% <br/>

Also,  the complexity is low compared to max 7 and 10. The models with max depth 7 and 10 have loads of steps involved but no significant increase in accuracy. <br/>

<b>How does this aim to predict the machine breakdown by identifying the anomalies in the data?</b><br/>
There are 2 ways:
<ol>
  <li>Thresholding and Alerts: 
    <ul>
      <li>Set thresholds to trigger alerts when sensor/predictor readings exceed expected values or anomaly scores fall outside a specific range.</li>
      <li>The ranges are well-defined in the Decision Tree Model. With each step, the hierarchy of the alarm should be coded. </li>
      <li>Ex-First Alarm ( least level of alarm)<br/>
          Second Alarm should be designed based on the next steps</li>
      <li>Upon receiving an anomaly alert, maintenance personnel investigate the potential cause of the issue. This involves analyzing sensor data, historical trends, and maintenance records to pinpoint the problem. Finally, schedule maintenance or repairs based on the weight of the issue.</li>
    </ul>
  </li>
  <li>
    <ul>
      Each of the variables is defined against time at regular frequency in the sample data.
      <li>We can run time series forecasting algorithms on each of the columns to predict the next set of values.</li>
      <li>Based on the forecasted values, we can check the probability of an anomaly for each row. </li>
      <li>Capture the time against the first row with a high probability of anomaly. Schedule maintenance before that time. </li>
    </ul>
</li>
</ol>
