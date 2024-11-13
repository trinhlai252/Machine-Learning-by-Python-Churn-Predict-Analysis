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
### WarehouseToHome, HourSpendOnApp, CashbackAmount

## V. Conclusion
