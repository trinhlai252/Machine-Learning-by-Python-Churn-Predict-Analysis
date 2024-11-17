# Python-Churn-Predict-Analysis

## I. Introduction
This project contains an eCommerce dataset that I will explore using SQL on [Google BigQuery](https://cloud.google.com/bigquery). The dataset is based on the Google Analytics public dataset and contains data from an eCommerce website.
## II. Business question
An ecommerce firm is initiating a project aimed at predicting chunrned users in order to offer potential promotions. The accompanying dataset provided by the company (churn_predict.csv) will be employed to address the following questions
* Build the Machine Learning model for predicting churned users. (fine tuning) 
* Based on the behaviors of churned users, the company would like to offer some special promotions for them. Please segment these churned users into groups. What are the differences between groups? 
## III. Dataset 
<table>
        <tr>
            <th>Variable</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>CustomerID</td>
            <td>Unique customer ID</td>
        </tr>
        <tr>
            <td>Churn</td>
            <td>Churn Flag</td>
        </tr>
        <tr>
            <td>Tenure</td>
            <td>Tenure of customer in organization</td>
        </tr>
        <tr>
            <td>PreferredLoginDevice</td>
            <td>Preferred login device of customer</td>
        </tr>
        <tr>
            <td>CityTier</td>
            <td>City tier</td>
        </tr>
        <tr>
            <td>WarehouseToHome</td>
            <td>Distance between warehouse to home of customer</td>
        </tr>
        <tr>
            <td>PreferredPaymentMode</td>
            <td>Preferred payment method of customer</td>
        </tr>
        <tr>
            <td>Gender</td>
            <td>Gender of customer</td>
        </tr>
        <tr>
            <td>HourSpendOnApp</td>
            <td>Number of hours spent on mobile application or website</td>
        </tr>
        <tr>
            <td>NumberOfDeviceRegistered</td>
            <td>Total number of devices registered by a particular customer</td>
        </tr>
        <tr>
            <td>PreferedOrderCat</td>
            <td>Preferred order category of customer in the last month</td>
        </tr>
        <tr>
            <td>SatisfactionScore</td>
            <td>Satisfactory score of customer on service</td>
        </tr>
        <tr>
            <td>MaritalStatus</td>
            <td>Marital status of customer</td>
        </tr>
        <tr>
            <td>NumberOfAddress</td>
            <td>Total number of addresses added by a particular customer</td>
        </tr>
        <tr>
            <td>Complain</td>
            <td>Any complaint has been raised in the last month</td>
        </tr>
        <tr>
            <td>OrderAmountHikeFromLastYear</td>
            <td>Percentage increase in order amount from last year</td>
        </tr>
        <tr>
            <td>CouponUsed</td>
            <td>Total number of coupons that have been used in the last month</td>
        </tr>
        <tr>
            <td>OrderCount</td>
            <td>Total number of orders that have been placed in the last month</td>
        </tr>
        <tr>
            <td>DaySinceLastOrder</td>
            <td>Number of days since the last order by the customer</td>
        </tr>
        <tr>
            <td>CashbackAmount</td>
            <td>Average cashback received in the last month</td>
        </tr>
</table>

## IV. Process
### Data Handling and Cleaning
* Define type of data
* Check duplicate data, remove if have
* Check missing/null data. Draw a box plot of each column with null data to decide whether to replace it with the mean, median, or mode.

### EDA
#### WarehouseToHome, HourSpendOnApp, CashbackAmount
![image](https://github.com/user-attachments/assets/dc95d0a8-0b6d-4101-98e9-3ded882de32a)
![image](https://github.com/user-attachments/assets/d1339694-71aa-4f15-93d2-38e3a13b7685)


#### Tenure
|index|tenure|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|0|0\.0|508|272|53\.54330708661418|
|1|1\.0|690|349|50\.57971014492754|
|9|9\.0|511|93|18\.199608610567513|
|20|20\.0|109|16|14\.678899082568808|
|21|21\.0|84|10|11\.904761904761903|

![image](https://github.com/user-attachments/assets/d1778906-fdb7-466a-9c66-6fe5a4d5b1c3)

#### Citytier
|index|citytier|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|2|3|1722|368|21\.37|
|1|2|242|48|19\.83|
|0|1|3666|532|14\.51|

![image](https://github.com/user-attachments/assets/44e38eba-b369-41a9-b466-dfeb8d181d2b)


#### Numberofdevice
|index|numberofdeviceregistered|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|5|6|162|56|34\.57|
|4|5|881|198|22\.47|
|3|4|2377|392|16\.49|
|2|3|1699|254|14\.95|
|1|2|276|26|9\.42|
|0|1|235|22|9\.36|

#### satisfactionscore
|index|satisfactionscore|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|4|5|1108|264|23\.83|
|2|3|1698|292|17\.2|
|3|4|1074|184|17\.13|
|1|2|586|74|12\.63|
|0|1|1164|134|11\.51|

#### numberofaddress
|index|numberofaddress|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|11|19|1|1|100\.0|
|12|20|1|1|100\.0|
|6|7|256|64|25\.0|
|7|8|280|66|23\.57|
|10|11|98|23|23\.47|
|8|9|239|46|19\.25|
|9|10|194|35|18\.04|
|2|3|1278|228|17\.84|
|1|2|1369|241|17\.6|
|5|6|382|66|17\.28|
|0|1|371|45|12\.13|
|4|5|571|67|11\.73|
|3|4|588|65|11\.05|
|13|21|1|0|0\.0|
|14|22|1|0|0\.0|

![image](https://github.com/user-attachments/assets/cbab9e09-0d53-413d-b651-6140dd5c807a)

#### Complain
|index|complain|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|1|1|1604|508|31\.67|
|0|0|4026|440|10\.93|

#### orderamounthike, couponused, ordercount, daysincelastorder
![image](https://github.com/user-attachments/assets/b77e9cc3-6b7e-4416-b5fe-072c340f522c)

#### gender
|index|gender|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|1|Male|3384|600|17\.73|
|0|Female|2246|348|15\.49|

#### prefeturedlogindevide
|index|preferredlogindevice|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|2|Phone|1231|276|22\.42|
|0|Computer|1634|324|19\.83|
|1|Mobile Phone|2765|348|12\.59|

#### PreferredPaymentMode
|index|preferredpaymentmode|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|1|COD|365|105|28\.77|
|5|E wallet|614|140|22\.8|
|0|CC|273|59|21\.61|
|6|UPI|414|72|17\.39|
|2|Cash on Delivery|149|23|15\.44|
|4|Debit Card|2314|356|15\.38|
|3|Credit Card|1501|193|12\.86|

#### PreferedOrderCat
|index|preferedordercat|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|4|Mobile Phone|1271|350|27\.54|
|3|Mobile|809|220|27\.19|
|0|Fashion|826|128|15\.5|
|2|Laptop & Accessory|2050|210|10\.24|
|5|Others|264|20|7\.58|
|1|Grocery|410|20|4\.88|

### Model training
We proceed with the following steps:
* Feature Transforming
* Split train/validate/test set
* Normalization for each set
* Apply mode
* Model evaluation and choose a better model
  
  In this problems, we use balanced accuracy as evaluate metric
  
| Model               | balanced_accuracy_train | balanced_accuracy_val |
| ------------------- | ----------------------- | --------------------- |
| Logistic Regression | 0.7                     | 0.68                  |
| Random Forest       | 1                       | 0.91                  |

=> We choose the Random Forest model
* Hyperparameter tuning
We use GridSearchCV to optimize the parameters of the RandomForestClassifier model based on the set of values ​​in param_grid. After finding the best set of parameters, the model is evaluated on the test set with the accuracy printed out.

| Model               | balanced_accuracy_train | balanced_accuracy_val |
| ------------------- | ----------------------- | --------------------- |
| Random Forest       | 1                       | 0.92             |
## V. Conclusion
