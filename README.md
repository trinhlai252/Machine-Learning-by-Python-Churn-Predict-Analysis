# Python-Churn-Predict-Analysis

## I. Introduction
In this project, I works on  machine learning models to predict user churn for an e-commerce company. The model is being developed using Python on Google Colab with relevant data for analysis.
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
* __WarehouseToHome__: The distribution is skewed right, with values ​​concentrated mainly below 40, and some outliers (around 100). In the boxplot, the two groups _Churn = 0_ and _Churn = 1_ have relatively similar medians. The difference between the two groups was not very clear => __WarehouseToHome__ may __lightly__ affect the churn ratio.
* __HourSpendOnApp__:Most of the value is concentrated in the 2 to 4-hour period. In the boxplot, the _Churn = 0_ (no churn) group has a higher median, and wider distribution, meaning they spend more time on the app than the _Churn = 1_ group. It seems like non-churn users tend to use the app more => __HourSpendOnApp__ is a related feature
* __CashbackAmount__: The distribution is right-skewed, with most values ​​concentrated in the 100-200 range. In the boxplot, there are quite a few outliers in the _Churn = 0_ group. The Churn = 0 group has a higher median, narrower distribution, and receives less cashback than the _Churn = 1_ group. Receiving more cashback can make customers less likely to leave. => __CashbackAmount__ is related to churn


#### Tenure
|index|tenure|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|0|0\.0|508|272|53\.54|
|1|1\.0|690|349|50\.58|
|9|9\.0|511|93|18\.2|
|20|20\.0|109|16|14\.68|
|21|21\.0|84|10|11\.91|

![image](https://github.com/user-attachments/assets/2021d1fb-5ed8-4e19-85c4-fed326e2779d)

* Users with tenuree = 0 and 1 have a much higher churn ratio (> 50%) than the remaining tenures.
*_Non-churn (0)_ has a higher median tenure with a wider range, indicating customers who stay longer are less likely to churn.
=>  here is a clear relationship between __Tenure__ and churn 


#### Citytier
|index|citytier|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|2|3|1722|368|21\.37|
|1|2|242|48|19\.83|
|0|1|3666|532|14\.51|

* Customers from higher city tiers (Tier 3) tend to churn more frequently, while customers in lower city tiers (Tier 1) have a lower churn ratio => There is a clear relationship between __Citytier__ and churn



#### Numberofdevice
|index|numberofdeviceregistered|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|5|6|162|56|34\.57|
|4|5|881|198|22\.47|
|3|4|2377|392|16\.49|
|2|3|1699|254|14\.95|
|1|2|276|26|9\.42|
|0|1|235|22|9\.36|

* Customers with more devices registered (for excample 6 devices) have the highest churn ratio at 34.57%.
* The churn ratio decreases as the number of devices decreases, reaching the lowest churn ratio (~9.36%) for customers with 1 or 2 devices.
=> __numberofdevice__ is related to churn

#### satisfactionscore
|index|satisfactionscore|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|4|5|1108|264|23\.83|
|2|3|1698|292|17\.2|
|3|4|1074|184|17\.13|
|1|2|586|74|12\.63|
|0|1|1164|134|11\.51|

* Customers with the highest satisfaction score (5) have the highest churn ratio at 23.83%.
* The churn ratio generally decreases as the satisfaction score decreases, with customers scoring 1 having the lowest churn ratio at 11.51%.
  
=> __satisfactionscore__ and churn is counterintuitive relationship 

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

![image](https://github.com/user-attachments/assets/54cb6dbd-e8de-4b63-8b0a-9f9e9a6c8f71)
* customers with more addresses are more likely to churn. Churn ratio increases as __numberofaddress__ rises, with higher churn seen in customers having 7+ addresses. Lower churn ratios are observed for those with 1-5 addresses
=> __numberofaddress__ is related to churn

#### complain
|index|complain|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|1|1|1604|508|31\.67|
|0|0|4026|440|10\.93|
* Customer with complaint has significantly higher churn ratio
  
=> __complain__ is related to churn
#### orderamounthike, couponused, ordercount, daysincelastorder
![image](https://github.com/user-attachments/assets/b77e9cc3-6b7e-4416-b5fe-072c340f522c)
* __orderamounthike, couponused, ordercount__ : There is a similar distribution between the two groups _churn = 0_ and _churn = 1_. However, __couponused__ has a clear difference in outliers between the two groups.
* __daysincelastorder__: _churn=0_ wider distribution, larger median and fewer outliers than _churn =1_

=> __orderamounthike,  ordercount__ is not related. __daysincelastorder__ is related. __couponused__  maybe relate, need to check more

#### gender
|index|gender|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|1|Male|3384|600|17\.73|
|0|Female|2246|348|15\.49|

* _Male_ and _Female_ have similar churn ratio

=> __gender__ is not related to churn

#### prefeturedlogindevide
|index|preferredlogindevice|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|2|Phone|1231|276|22\.42|
|0|Computer|1634|324|19\.83|
|1|Mobile Phone|2765|348|12\.59|
* Customers using Phone as their preferred login device have the highest churn ratio (22.42%), followed by Computer (19.83%). Mobile Phone users have the lowest churn ratio (12.59%)

=> __prefeturedlogindevide__ is related to churn
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

* There are varying churn ratios for different payment modes. The churn ratio decreases as the payment mode shifts from manual methods (like COD) to more automated or digital options (like Credit Card, Debit Card, and E-wallet).
  
=> __PreferredPaymentMode__ is related

#### preferedOrderCat
|index|preferedordercat|total\_cus|churn\_cus|churn\_ratio|
|---|---|---|---|---|
|4|Mobile Phone|1271|350|27\.54|
|3|Mobile|809|220|27\.19|
|0|Fashion|826|128|15\.5|
|2|Laptop & Accessory|2050|210|10\.24|
|5|Others|264|20|7\.58|
|1|Grocery|410|20|4\.88|
* Customers in mobile-related categories have higher churn rates. Trends suggest that non-tech categories may have lower churn rates.
=> __preferedOrderCat__ is related

### Model training
We proceed with the following steps:
* Feature Transforming
* 
  Feature Transformation removes unrelated columns, identifies categorical columns, and applies One-Hot Encoding to encode them.
* Split train/validate/test set
  We split the dataset into training, validation, and test sets. First, 70% of the data is allocated for training, while the remaining 30% is split equally into validation and test sets using train_test_split with a fixed random state for reproducibility.
  
| Subset                      | Number |
| --------------------------- | ------ |
| Number data of train set    | 3941   |
| Number data of validate set | 844    |
| Number data of test set     | 845    |
* Normalization for each set

MinMaxScaler to scale the feature values between 0 and 1
* Apply mode

  In this project, we use 2 most popular predict machine learning:  __Logistic Regression__ and __Random Forest__
* Model evaluation and choose a better model
  
  We use balanced accuracy to evaluate metric
  
| Model               | balanced_accuracy_train | balanced_accuracy_val |
| ------------------- | ----------------------- | --------------------- |
| Logistic Regression | 0.7                     | 0.68                  |
| Random Forest       | 1                       | 0.91                  |

=> We choose the Random Forest model
* Hyperparameter tuning
We use GridSearchCV to optimize the parameters of the RandomForestClassifier model based on the set of values ​​in param_grid. After finding the best set of parameters, the model is evaluated on the test set with the accuracy metrics.

| Model               | balanced_accuracy_train | balanced_accuracy_val |
| ------------------- | ----------------------- | --------------------- |
| Random Forest       | 1                       | 0.92             |
## V. Conclusion
