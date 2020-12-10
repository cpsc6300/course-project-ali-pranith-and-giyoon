

# Shipment Delivery Prediction in Logistics Using Machine Learning

### Team Members: Ali Shirzadibabakan, Pranith Abbarajou, Giyoon Kwag
### Date: December 10th, 2020

# 1. Problem Statement and Motivation

One of the most challenging problems in logistics and supply chain network is meeting the scheduled shipment delivery. A firm has limited time and budget and needs to receive and deliver its shipments on time. The common issues negatively affecting deliveries' timeliness are poor shipment delivery planning, lading errors, and attaching incorrect documentation (Lingaro Group,2020). There are many ways to improve delivery times. Firms may achieve on-time deliveries by planning proper schedules in line with capacities, adequate tracking and collaborating with suppliers, accurate forecasting and monitoring efficiency, and integrating and controlling systems. 

Machine Learning methods can considerably help suppliers with utilizing historical data on shipment delivery and predict whether a shipment with specific characteristics (origin, destination, shipment type, etc.) will deliver on time or not. This prediction model substantially helps suppliers and third-party logistics companies to enhance their supply chain network and offer more reasonable delivery dates to their customers. For instance, if the prediction shows that the delivery of a specific type of shipment or delivery to a particular destination will have a delay, the provider might figure out the main issues to enhance the network in the future. They can also notice the customer that the shipment might not deliver on time.

In this project, we propose several modeling scenarios based on the available data and the stage at which a firm wants to predict if a shipment will be delivered on time or not using various supervised machine learning methods. Therefore, in this project, our target is a binary feature indicating that if a shipment meets its scheduled delivery or not. For this purpose, we utilized various time-independent predictors such as supplier location, shipment origin, shipment destination, shipment type, shipment material, the quantity of the shipment, etc. and time-dependent features such as different milestones indicating that if a shipment has met its scheduled date for that milestone or not. Logistics firms usually have a system to track their shipments from an origin to a destination. They also set several milestones and plan schedules for each milestone to track if a shipment will follow its scheduled plan. In this case study, we collected data from an extensive Engineering, Procurement, and Construction (EPC) logistics firm with a large-scale supply chain network and gathers different time-independent and time-dependent features shipments. This firm sets ten milestones for tracking a shipment at different stages, from issuing a purchase order to delivery to the destination. For each milestone, the firm sets a scheduled date that expects the shipment to meet and collected an actualized date that the shipment met that milestone. The difference between the scheduled and actualized dates for each milestone shows that if the shipment has met that milestone or not. This study aims to predict if a shipment will meet the final milestone (milestone 10), which is delivery to the end customer.  To this end, we designed different modeling scenarios and developed appropriate machine learning models for each scenario. 


# 2. Introduction and Data Description

The satisfaction of delivery requirements and customers’ expectations is essential for every business. Four of the top six challenges reported by the 2020 MHI Annual Industry Report are related to higher customer expectations and faster delivery. Increasing attention is given to on-time delivery of goods in the logistics and distribution industry. With uncertainties in customer demands, on-time deliveries cannot be ensured frequently (Zhang et al., 2016). On-time delivery is defined as a process and supply chain efficiency measure, which measures the number of finished goods or services delivered to customers on time and in full. It helps determine how efficiently we meet our customer's or agreed deadlines (Lean Manufacturing & Operations Management).

Weak delivery performance negatively affects customer satisfaction and indicates low production efficiency and materials handling procedures. Poor delivery can cause several issues affecting other aspects of a company’s supply chain network, such as production delays due to material shortages, avoidable expedited shipping costs, and customer dissatisfaction (Otto Motors, 2017). Therefore, suppliers need to predict delivery time accurately and, according to this prediction, offer a precise delivery time to their customers. Also, they need to know which shipments might deliver delayed based on historical data. This helps them to notice the customer and provide more actual delivery time to the customer. Furthermore, on-time delivery is not just about customer satisfaction and deadlines. Not meeting on-time delivery can affect the entire business's functioning, including its financial stability (Lingaro Group,2020). 

In this project, we want to utilize supervised machine learning techniques to predict whether a shipment will meet its scheduled delivery time or not. For this purpose, we collected data from an extensive Engineering, Procurement, and Construction (EPC) logistics firm that has provided data for individual items being shipped through its supply chain network. The dataset contains more than 93,000 records and 137 features about the characteristics of shipments, origin, destination, and 10 milestones that the supplier has defined to track a shipment from an origin to a destination. These milestones show that if a shipment has met the scheduled plan of the firm. In other words, there are two dates (i.e., scheduled and actualized dates) for each milestone, indicating that if that milestone has been met or not. The 10th milestone is the shipment delivery to the final customer that we want to predict. Table 1 describes the most important features in this dataset.




<h1 align="center"> **Table 1: Description of Features**</h1>

| Feature  | Description |
| ------------- | ------------- |
| SUPPLIER_LOCATION  | The city that the supplier’s facilities are located at |
| SUPPLIER_COUNTRY | The country that the supplier’s facilities are located at |
| LINE_NUMBER | The line number in the supply chain network |
| SHIP_POINT  | The origin city of the shipment  |
| SHIP_POINT_COUNTRY  | The origin country of the shipment  |
| DESTINATION  | The destination of the shipment |
| ITEM_PRIME_ID  | The categorical type of the item (shipment) |
| PO_PRIME_ID | The category of purchase order of the item (shipment)  |
| SHIP_GROUP_STATUS  | The status of the shipment group including “Closed” or “Open”  |
| RECEIVING_ONLY_PO | A binary feature indicating if only the purchase order has been received or not |
| QTY_ORDERED  | The quantity of the ordered shipment |
| MATERIAL_TYPE | The material type of the item (shipment) |
| SCP_DATE  | The date of Supplier Current Promise (SCP) |
| MILESTONE_1_SCHEDULE  | The scheduled date for issuing the purchase order   |
| MILESTONE_1_ACTUALIZED  | The actualized date that the purchase order was issued  |
| MILESTONE_2_SCHEDULE | The scheduled date for issuing Shipment Reference Number (SRN)  |
| MILESTONE_2_ACTUALIZED  | The actualized date that the Shipment Reference Number (SRN) was issued |
| MILESTONE_3_SCHEDULE  | The scheduled date that the shipment will be at Free Carrier (FCA) supplier shop  |
| MILESTONE_3_ACTUALIZED | The actualized date that the shipment was at Free Carrier (FCA) supplier shop  |
| MILESTONE_4_SCHEDULE  | The scheduled date that the shipment will be at packer location  |
| MILESTONE_4_ACTUALIZED  | The actualized date that the shipment was at packer location  |
| MILESTONE_5_SCHEDULE  | The scheduled date that the shipment will be in air transit |
| MILESTONE_5_ACTUALIZED | The actualized date that the shipment was in air transit  |
| MILESTONE_6_SCHEDULE  | The scheduled date that the shipment will be in ocean transit   |
| MILESTONE_6_ACTUALIZED  | The actualized date that the shipment was in ocean transit  |
| MILESTONE_7_SCHEDULE | The scheduled date that the shipment will be in ocean transit from Australia  |
| MILESTONE_7_ACTUALIZED  | The actualized date that the shipment was in ocean transit from Australia |
| MILESTONE_8_SCHEDULE  | The scheduled date that the shipment will be at the destination’s Custom |
| MILESTONE_8_ACTUALIZED | The actualized date that the shipment was at the destination’s Custom  |
| MILESTONE_9_SCHEDULE  | The scheduled date that the shipment will be at the destination’s supplier warehouse  |
| MILESTONE_9_ACTUALIZED  | The actualized date that the shipment was at the destination’s supplier warehouse  |
| MILESTONE_10_SCHEDULE  | The scheduled date that the shipment will be at the destination (The scheduled date of Material Received Report (MRR)) |
| MILESTONE_10_ACTUALIZED | The actualized date that the shipment was at the destination (The actualized date of Material Received Report (MRR))  |











# 3. Literature Review and Related Work 

The concept of on-time delivery measures performance regarding perfact delivery and customer service level with delivery reliability and order completeness(Gunasekaran et al., 2004). On-time delivery, lead time length, delivery reliability, and inventory service level are examples of common delivery service performance variables in dyadic customer–supplier interfaces. Among them, on-time delivery is often considered the most important performance variable when orders are seldom changed in the supply chain(Keebler et al.1999, Stock and Lambert 2001). Most companies, regardless firm size and industry, normally have on-time as in important supply perfromnance metric. When defining on-time delivery, there are several different issues that firms need to consider(Forslund and Jonsson 2007). 

The first concerns the measurement object, which may be the number of orders, individual items or, order lines. The second concerns the time unit for measuring being on time. It could vary between the correct hour, day, week or within a specific time window. The third concerns the measurement point, i.e. where along the supply chain the order is considered to be delivered. The fourth concerns the comparison date for an actual delivery date in order to decide if it is on time or not. However, few studies have examined in any depth how delivery service performance should be managed, and almost none have focused on measuring on-time delivery.



# 4. Data Preparation

### 4.1. Drop unnecessary columns and columns with too many Null values 

To clean up the dataset, we first dropped unnecessary columns (features) including noninformative features (e.g., the description columns), the columns containing the same value for all the records (e.g., SHIP_GROUP_TYPE which has the same value for all the records), and duplicated features (e.g., the columns containing the same value for every record such as the columns of REV and IN_DOC_REV_PK). Also, we dropped the columns with too many null values.






### 4.2. Fill null values

Some important features, specifically the Milestone columns, have some Null values that can be effectively filled out using the values of other features. Since the Milestone features are the important features in this study, we don't want to easily drop all the records with missing values beacaue we will miss a lot of records. Therefore, after the consultation with the data analyst at the Firm, we found out the features containing the same value for the Milestones and use these duplicated features to fill out the Null values of the Milestone features. However, beacuse the Milestones 5 and 7 include too many Null values, we dropped those from the dataset.

For example, we filled null values in MILESTONE_1_ACTUALIZED with the possible values from other columns.
Number of Null Values in MILESTONE_1_ACTUALIZED before cleaning up: 11
Number of Null Values in MILESTONE_1_ACTUALIZED after cleaning up: 0






### 4.3. Create new features

We created a binary feature for each milestone showing whether the milestone has been met or not. For example, "MILESTONE_1_meet" is 1 if it has been met (i.e., the "MILESTONE_1_ACTUALIZED" date is before than the "MILESTONE_1_SCHEDULE" date) and it is 0 if it has not been met. Also, we created a numerical feature for each milestone showing the number of days between the scheduled and actualized dates of meeting the milestone. For example, "MILESTONE_1_Diff" shows the difference (in days) between the "MILESTONE_1_ACTUALIZED" and "MILESTONE_1_SCHEDULED".The negative values of "MILESTONE_x_Diff" shows the number of days that the "Milestone x" has been met earlier and the positive values shows the number of delay days. Note that Milestone_10_meet is our target feature that we want to predict it using other milestones and other features in the dataset. 

We also created some additional features for the differences between the scheduled milestone 10 and the scheduled date of other milestones under the assumption that if we have more time between the scheduled dates of other milestones and milestone 10, the probability of meeting milestone 10 might be increased. Finally, we created some features showing the number of days between the scheduled milestone 10 and other important dates (i.e. LINE_SOP_DATE, LINE_RAS_DATE, and SCP_DATE) under the assumption that these might be informative for the prediction of meeting milestone 10.






### 4.4. Data Visualization

Milestone 10 is the target feature that we want to predict using other features.



![figure18](https://user-images.githubusercontent.com/61207345/101703648-01175380-3a51-11eb-9f27-8d221394917e.png)

<h1 align="center"> **<Figure 1: Milestone 10 Distribution>**</h1>


The number of zero of "Milestone_10_Meet" is much more than of 1, which means that the number of days that  Milestone 10 didn't meet schedule on time is more than on-time schedule.







![figure19](https://user-images.githubusercontent.com/61207345/101703828-60756380-3a51-11eb-9b7a-80267399d260.png)

**<Figure 2: Difference between Scheduled and Actualized Dates of Milestone 10>** 



Because we already see in figure 1, figure2 also shows that Milestone_10 delayed a lot and its delay is mainly distributed from 0 to 1000 delay days.




### 4.5. Encoding Categorical Features & Scaling Numerical Features

It should be noted that according to the performance metrics, our final model is Random Forest. Random Forest require neither encoding categorical features nor scaling numerical features. However, we still do encoding and scaling processes because we will test other classification methods such as SVM, KNN, and Logistic Reression and these methods require encoded categorical data and scaled numerical data to produce better results. Also, to encode categorical data, we used label encoder method which is a simple encoder method; however, other encoders such as One Hot encoder might produce more reliable results and should be considered in future works.








# 5. Modeling Approach

For the prediction of meeting Milestone 10, we followed 3 different modeling scenarios:

Scenario 1: We are at the stage after Milestone 9 and know whether the Milestones 1 through 9 have been met or not.

Scenario 2: We are at the early stage before meeting any milestones. Therefore, in this scenario, we assumed that we do not have any information on whether Milestones 1 trough 9 will be met or not.

Scenario 3: We supposed that we do not have any information on meeting the Milestones 1 trough 9 and on other time-dependent features such as Line_SOP_date, Line_RAS_date, etc. In other words, in this scenario, we only used time-independent features such as ORIGIN, DESTINATION, SHIPMENT TYPE, SUPPLIER, etc. to predict meeting Milestone 10.



## 5.1. Scenario 1: We are at the stage after Milestone 9

### 5.1.1. Using binary features for meeting the Milestones 1-9

In Model 1, in addition to the available features, we included the binary features showing whether the milestones 1-9 have been met or not. We tuned Random Forest to determine the best values for the hyperparameters of max_depth, max_features, and min_samples_leaf. Also, we determined the importance of features and selected the most important ones using the importance of features obtained from Random Forest. Finally, we selected the most important features, trained the tuned Random Forest model, and obtained the performance metrics using test dataset.


![figure1](https://user-images.githubusercontent.com/61207345/101667738-b16b6480-3a1d-11eb-976d-b0db726cc1dc.png)

**<Figure3: Feature Selection>**


From Random Forest, we selected features

selected_features = ['SUPPLIER_LOCATION', 'LINE_NUMBER', 'ITEM_PRIME_ID', 'SHIP_POINT', 'RECEIVING_ONLY_PO', 'MILESTONE_2_meet', 'MILESTONE_3_meet', 'MILESTONE_4_meet', 'MILESTONE_6_meet', 'MILESTONE_8_meet','MILESTONE_9_meet', 'MILESTONE_10_meet']

As seen in the above plot, Milestone_9_meet has the most important feature 
Next important feature is NIN_NUMBER, which is the line number in the supply chain network 





![figure2](https://user-images.githubusercontent.com/61207345/101670361-0eb4e500-3a21-11eb-929a-dade35cfce64.png)

**<Figure4: Confusion Matrix>**




Mean Cross-Validated Accuracy: 0.9142750054122457

Training Accuracy: 0.9195601166070201

Testing Accuracy: 0.9169589534553039

From figure 2, overall accuracy is under 92 % and I cannot say that the accuray is very high 




**Table 2: Classification Report **
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.96  |0.92  |0.94  |7423  |
| 1  | 0.82  |0.92  |0.87  |3126  |


Precision: THe ratio of correctly predicted positive observations to the total predicted positive observations.

Recall: THe ratio of correctly predicted positive observations to the all observations in actual class - yes.

F1 Score: The weighted average of Precision and Recall. F1-score takes both false positives and false negatives into account

High precision relates to the low false positive rate. We have got 0.82 precision (for 1) which is pretty good.
Also, other numbers including Recall, F1 Score are also pretty good




### 5.1.2. Using difference features for meeting Milestones 1-9

In Model 2, instead of using the binary features for meeting the milestones 1 through 9, we used the numerical features showing the difference between the scheduled and actualized dates for the milestones 1 through 9. We tuned Random Forest to determine the best values for the hyperparameters of max_depth, max_features, and min_samples_leaf. Also, we determined the importance of features and selected the most important ones using the importance of features obtained from Random Forest. Finally, we selected the most important features, trained the tuned Random Forest model, and obtained the performance metrics using test dataset.


![figure3](https://user-images.githubusercontent.com/61207345/101671314-55570f00-3a22-11eb-8930-393fb618c58d.png)

**<Figure5: Feature Selection>**



From Random Forest, we selected features

selected_features = ['SUPPLIER_LOCATION', 'LINE_NUMBER', 'ITEM_PRIME_ID', 'SHIP_POINT', 'RECEIVING_ONLY_PO',
                     'MILESTONE_2_Diff', 'MILESTONE_3_Diff', 'MILESTONE_4_Diff', 'MILESTONE_6_Diff', 
                     'MILESTONE_8_Diff', 'MILESTONE_9_Diff', 'MILESTONE_10_meet']

As seen in the above plot, Milestone_9_Diff has the most important feature 




![figure4](https://user-images.githubusercontent.com/61207345/101671417-7881be80-3a22-11eb-9c93-37dda274cc1d.png)

**<Figure6: Confusion Matrix>**




Mean Cross-Validated Accuracy: 0.987130651061792

Training Accuracy: 0.9942881520631385

Testing Accuracy: 0.9879609441653238

When using the numerical features showing the difference between the scheduled and actualized dates for the milestones 1 through 9 (instead of using the binary features for meeting the milestones 1 through 9 in model 1), we found that all accuracy increased to 98%.





**Table 3: Classification Report**
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.99  |0.99  |0.99  |7423  |
| 1  | 0.98  |0.98  |0.98  |3126  |


High precision relates to the low false positive rate. We have got 0.98 precision (for 1) which is much higher than model 1 case.
Also, other numbers including Recall, F1 Score are also much more higher than model 1.






### 5.1.3. Dropping Milestones 6 and 8 & Compare the Performance of Various Classification Methods including Random Forest, Decision Tree, SVM, KNN, and Logistic Regression

In Model 3, to increase the size of training and test datasets, we removed the features related to the Milestones 6 and 8 as they have much more Null values compared to other features. Because we want to run different classification methods and compare their performance metrics, we performed a correlation matrix beteen features and selected the highest correlated features with the target feature as the most important features. Then, we tuned the hyperparameters of several classification methods including Random Forest, Decision Tree, SVM, KNN, and Logistic Regression. Finally, we trained the tuned models, obtained the performance metrics using test dataset, and compare the results.



#### 5.1.3.2. Random Forest


![figure5](https://user-images.githubusercontent.com/61207345/101778115-6c990980-3ac1-11eb-93a3-ab8dcf3d355c.png)

**<Figure7: Feature Selection>**



selected_features = ['SUPPLIER_LOCATION', 'LINE_NUMBER', 'ITEM_PRIME_ID', 'SHIP_POINT', 'RECEIVING_ONLY_PO', 
                     'MILESTONE_2_Diff', 'MILESTONE_3_Diff', 'MILESTONE_4_Diff', 'MILESTONE_9_Diff', 'MILESTONE_10_meet']

As seen in the above plot, Milestone_9_Diff has the most important feature 




#### 5.1.3.1. Correlation Matrix


![figure6](https://user-images.githubusercontent.com/61207345/101671610-b54db580-3a22-11eb-9acc-112772bdcf62.png)

**<Figure8: Correlation Matrix>**



There is not vairable which is problematic because of high correlation with other variables



![figure7](https://user-images.githubusercontent.com/61207345/101671952-37d67500-3a23-11eb-833a-1df006266c8d.png)

**<Figure9: Confusion Matrix>**



Mean Cross-Validated Accuracy: 0.9889121228458648

Training Accuracy: 0.9944941893694037

Testing Accuracy: 0.9900937285681628



**Table 4: Classification Report** 
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.99  |0.99  |0.99  |9565  |
| 1  | 0.98  |0.98  |0.98  |3558  |


High precision relates to the low false positive rate. We have got 0.98 precision and 0.99 (for 1 and 0) which is much higher than model 1 case.

Also, other numbers including Recall, F1 Score are also much more higher than model 1 and similar with model 2



#### 5.1.3.3. Decision Tree

The best tuned hyperparameters are:
{'max_depth': 15, 'max_features': 9, 'min_samples_leaf': 1, 'min_samples_split': 3}

The Cross Validated Accuracy for the best Model is: 0.9874261764145551


![figure8](https://user-images.githubusercontent.com/61207345/101672144-7d933d80-3a23-11eb-9532-1e26c7e79a1c.png)

**<Figure10: Confusion Matrix>**

 
 
Mean Cross-Validated Accuracy: 0.9873880230048796

Training Accuracy: 0.9939226519337017

Testing Accuracy: 0.9887982930732302



**Table 5: Classification Report** 
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.99  |0.99  |0.99  |9565  |
| 1  | 0.98  |0.98  |0.98  |3558  |

 
High precision relates to the low false positive rate. We have got 0.98 precision and 0.99 (for 1 and 0) which is much higher than model 1 case and similar with model 2

Also, other numbers including Recall, F1 Score are also much more higher than model 1 and similar with model 2

 
 
 
#### 5.1.3.4. SVM

The best tuned hyperparameters are:
{'C': 50, 'kernel': 'rbf'}

The Cross Validated Accuracy for the best Model is:
0.9225185749666603


![figure9](https://user-images.githubusercontent.com/61207345/101672312-baf7cb00-3a23-11eb-8b7b-bf0e543430f7.png)

**<Figure11: Confusion Matrix>**



Mean Cross-Validated Accuracy: 0.9217184836932603

Training Accuracy: 0.9232044198895027

Testing Accuracy: 0.9225786786557951



**Table 6: Classification Report** 
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.99  |0.99  |0.99  |9565  |
| 1  | 0.98  |0.98  |0.98  |3558  |


High precision relates to the low false positive rate. We have got 0.98 precision and 0.99 (for 1 and 0) which is much higher than model 1 case and similar with model 2

Also, other numbers including Recall, F1 Score are also much more higher than model 1 and similar with model 2





#### 5.1.3.5. KNN

The best tuned hyperparameters are: {'n_neighbors': 1}

The Cross Validated Accuracy for the best Model is: 0.9784911411697467
          


![figure10](https://user-images.githubusercontent.com/61207345/101672458-e37fc500-3a23-11eb-919b-1fd937592e2e.png)

**<Figure12: Confusion Matrix>**



Mean Cross-Validated Accuracy: 0.97883402354555

Training Accuracy: 0.9964945703943608

Testing Accuracy: 0.9809494780156977




**Table 6: Classification Report** 
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.99  |0.99  |0.99  |9565  |
| 1  | 0.97  |0.96  |0.96  |3558  |


High precision relates to the low false positive rate. We have got 0.90 precision and 0.96 (for 1 and 0) which is much higher than model 1 case. When comparing above models, KNN's precision, recall, and f1-score for 1 is slightly less.





#### 5.1.3.6. Logitstic Regression

The best tuned hyperparameters are: {'C': 10, 'penalty': 'l1'}

The Cross Validated Accuracy for the best Model is: 0.9078491141169747


![figure11](https://user-images.githubusercontent.com/61207345/101672574-0a3dfb80-3a24-11eb-8448-108471c534e8.png)

**<Figure13: Confusion Matrix>**


Mean Cross-Validated Accuracy: 0.9081731153287536

Training Accuracy: 0.9083825490569633

Testing Accuracy: 0.9075668673321649



**Table 7: Classification Report** 
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.95  |0.92  |0.94  |9565  |
| 1  | 0.81  |0.87  |0.84  |3558  |


High precision relates to the low false positive rate. We have got 0.95 precision and 0.81 (for 1 and 0) which is the least number when comparing above models. 

Also, other numbers including Recall, F1 Score are also much less than above models.

Thus, logitstic model shows poor performance and it is not recommened to use logitstic model in scenario 1




#### 5.1.3.7. Comparison of Models

![figure12](https://user-images.githubusercontent.com/61207345/101672654-26419d00-3a24-11eb-9f79-4eb1fba46803.png)

**<Figure 14: Comparison of Models>**




**Table 8: Comparison of Models** 
| Method  | Training Accuracy |Testing Accuracy |Mean Cross Validation Accuracy |
| ------------- | ------------- |------------- |------------- |
| Random Forest | 0.9945  |0.9901  |0.9889 |
| Decision Tree  | 0.9939  |0.9888  |0.9874  |
| SVM | 0.9232  |0.9226  |0.9217 |
| KNN  | 0.9965  |0.9809  |0.9788  |
| Logitstic Regression  | 0.9084  |0.9076  |0.9082 |


From the comparison of models, we found that Random Forest has the highest accuracy (over 98%) and Logistic Rgression has the lowest accuracy (under92%). 

Thus, in scenario 1, it is recommened to use Random Forest model. 





## 5.2. Scenario 2: We are at the early stage before meeting any Milestone

In Scenario 2, we supposed that we are at the early stage before meeting any milestones. Therefore, there is no information on meeting the Milestones 1 through 9. However, we can include some features showing the difference between the scheduled date of milestone 10 and the scheduled dates of other milestones because the scheduled date of all the Milestones are set at the early stage though we don't know whether these scheduled dates will be met or not. Additionally, we used some new features showing the difference between the scheduled date of milestone 10 and some given dates such as Line_SOP date, Line_RAS date, and SCP date. Because the comparison of the several classification methods in the previous section showed that the Random Forest Model results in better performance, we only run a Random Forest model for this scenario. The importance obtained from the Random Forest shows that while the differences between the scheduled date of milestone 10 and the scheduled dates of other milestones are not important, the differences from Line_SOP date, Line_RAS date, and SCP date are very important.


Radom Forest --- Selecting Features


![figure13](https://user-images.githubusercontent.com/61207345/101673068-a7992f80-3a24-11eb-9f37-abb7dd8c2ace.png)

**<Figure 15:  Feature Selection>**



selected_features = ['REV', 'SUPPLIER_LOCATION', 'LINE_NUMBER', 'PO_PRIME_ID', 'ITEM_PRIME_ID', 'MATERIAL_TYPE', 'SHIP_POINT','RECEIVING_ONLY_PO', 'SCHEDULE_SOP_10_Diff', 'SCHEDULE_RAS_10_Diff', 'SCHEDULE_SCP_10_Diff', 'MILESTONE_10_meet']

As seen in the above plot, 3 features (Schedule_SOP_10_Diff,Schedule_RAS_10_Diff, Schedule_SCP_10_Diff) have the most important feature



The best tuned hyperparameters are: {'max_depth': 20, 'max_features': 7, 'min_samples_leaf': 1}

The Cross Validated Accuracy for the best Random Forest Model is: 0.9775658182879946



![figure14](https://user-images.githubusercontent.com/61207345/101673194-dca58200-3a24-11eb-9443-19305a803e0e.png)

**<Figure 16: Confusion Matrix>**



Mean Cross-Validated Accuracy: 0.9801449720686802

Training Accuracy: 0.9953120184274985

Testing Accuracy: 0.979885803270179



**Table 9: Classification Report**
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.99  |0.99  |0.99  |11427  |
| 1  | 0.96  |0.96  |0.96  |3956  |



High precision relates to the low false positive rate. We have got 0.99 precision and 0.96 (for 1 and 0) which is similar with scenario 1 models except for logitstic regression

Also, other numbers including Recall, F1 Score are also similar with scenario 1 models except for logitstic regression





## 5.3. Sceario 3: What if we don't have any time-dependent data?

In Scenario 3, we supposed that we do not have any information on meeting the milestones 1 through 9 as well as on other time-dependent features such as Line_SOP_date, Line_RAS_date, and SCP date. In other words, in this scenario, we supposed that there is no given date in the dataset. Therefore, we only used the time-independent features such as supplier location, line number, and shipment point to predict meeting Milestone 10. We want to know how much time-independent features are able to predict whether the Milestone 10 will be met or not. Again, we only developed a Random Forest model.




Radom Forest --- Selecting Features


![figure15](https://user-images.githubusercontent.com/61207345/101673279-f6df6000-3a24-11eb-90d6-a064dae0f828.png)

**<Figure 17: Feature Selection>**


selected_features = ['REV', 'SUPPLIER_LOCATION', 'LINE_NUMBER', 'DESTINATION', 'PO_PRIME_ID', 'ITEM_PRIME_ID', 
                     'MATERIAL_TYPE', 'SHIP_POINT', 'RECEIVING_ONLY_PO', 'QTY_ORDERED', 'MILESTONE_10_meet']
                     
As seen in the above plot, LIN_NUMBER has the most important feature 


The best tuned hyperparameters are: {'max_depth': 15, 'max_features': 7, 'min_samples_leaf': 2}

The Cross Validated Accuracy for the best Random Forest Model is: 0.8642490930752447



![figure16](https://user-images.githubusercontent.com/61207345/101673442-2bebb280-3a25-11eb-9c45-e7ab403a9971.png)

**<Figure 18: Confusion Matrix>**



Mean Cross-Validated Accuracy: 0.8662704997996059

Training Accuracy: 0.8895492818226844

Testing Accuracy: 0.8652281002355965



**Table 10: Classification Report** 
|   | Precision |Recall |F1-Score |Support |
| ------------- | ------------- |------------- |------------- |------------- |
|0  | 0.90  |0.92  |0.91  |13957  |
| 1  | 0.75  |0.71  |0.73  |4719  |

High precision relates to the low false positive rate. We have got 0.90 precision and 0.75 (for 1 and 0) which is less than  scenario 1 & 2 models 

Also, other numbers including Recall, F1 Score are also is less than  scenario 1 & 2 models 



## 5.4. Sensitivity analysis on the effects of training % vs. testing % on the Random Forest Model


![figure17](https://user-images.githubusercontent.com/61207345/101673739-8e44b300-3a25-11eb-8863-36e7566d3249.png)

**<Figure 19: Sensitivity Analysis>**



When Cross-valid and Testing data size increase, thier accuracies decrease
When Training data size increases, its accuracy also increase. 



The maximum Cross-Validated is 0.8647578610958556 obtained from the test sample size = 0.2

The maximum training is 0.9061696658097687 obtained from the test sample size = 0.9500000000000001

The maximum testing accuracy is 0.8653887342043264 obtained from the test sample size = 0.2






# 6. Project Trajectory, Results and Discussion 

In this project, we developed a machine learning model to predict whether a shipment delivery will be on time or not. On-time delivery is one of the biggest concerns of a supplier affecting customer satisfaction considerably. Therefore, a supplier wants to have an accurate model predicting if a shipment might be delivered with a delay. This model helps the supplier adjust its delivery schedule and logistics processes to reduce delivery delays for the shipments that are likely to delay delivery. For this purpose, we collected data from a firm’s large-scale supply chain network containing different features about the shipment. This firm sets ten milestones for tracking a shipment at different stages from the purchase order issue to delivery to the destination. For each milestone, the firm defines two dates: a scheduled date that the firm expects the shipment will meet and an actualized date that the shipment was met. The difference between the scheduled and actualized dates indicates that if the shipment has met that milestone or not. This study aims to predict if a shipment will meet the final milestone (milestone 10) or not.  To this end, we designed different scenarios and developed an appropriate machine learning model for each scenario. 

In the first scenario, we suppose that the firm is at the milestone 9 and wants to know if the delivery will be on time. In other words, in this scenario, we assume that the firm knows which milestones of 1 through 9 have been met by a shipment. To predict if milestone 10 will be on-time or not, we developed different machine learning methods. First, we developed a random forest model using 9 binary features indicating whether milestones 1 through 9 have been met or not and other important features. The results showed that the model could predict if a shipment will be delivered on time with 91.4% cross-validation accuracy. Also, different performance metrics such as precision, recall, and f1 are higher than 90%, indicating good predictability of the model. 
In the second modeling approach, instead of using 9 binary features for meeting milestones 1 through 9, we used 9 numerical features indicating the difference between the scheduled date and actualized date for each milestone. In other words, these features show that how many days earlier or later a shipment has been met milestones 1 through 9. Again, we developed a random forest model, and the results showed that the performance metrics significantly increases compared to those in the first modeling approach. The cross-validation accuracy obtained from this model is about 98.7%. All the other metrics, including precision, recall, and f1 are also higher than 98%, indicating this model's power to predict meeting milestone 10.

In the first and second modeling approach, we found out that milestones 6 and 8 have too many null values, and hence we missed a lot of observations. Therefore, to increase the number of observations, we decided to remove milestones 6 and 8 from the training and test datasets and also develop different supervised classification models to compare their performance. Therefore, all the features used in this model are the same as those used in model 2, but we removed milestones 6 and 8. We developed a random forest, decision tree, KNN, SVM, and logistics regression and compared their performance metrics. The results showed that the random forest model with 98.9% cross-validation accuracy produces the highest accuracy. The random forest model was followed by the models of the decision tree, KNN, SVM, and logistics regression with 98.7%, 97.9%, 92.2%, and 90.8% cross-validation accuracy, respectively. In addition to the cross-validation accuracy, we compared other metrics, including precision, recall, and f1. The results showed that the random forest model overall produces higher performance compared to other models. Therefore, in scenarios 2 and 3, we only developed a random forest model.

In the second scenario, we supposed that we are at the early stage before meeting any milestones. In other words, in this scenario, we supposed that the firm has no information about meeting milestones 1 through 9 and wants to predict if a shipment will deliver on time without tracking it at different milestones (i.e., milestones 1 through 9). While the firm has no information on meeting milestones 1 through 9, it still has a scheduled date for every milestone because the scheduled dates of all the Milestones are set at the early stage, though the firm does not know whether these scheduled dates will be met or not. Therefore, we defined some features showing the difference between the scheduled date of milestone 10 and the scheduled dates of other milestones. Furthermore, we created some new features showing the difference between the scheduled date of milestone 10 and some given dates such as Line_SOP date, Line_RAS date, and SCP date. The results showed that the random forest model is still able to properly predict meeting milestone 10 with a cross-validation accuracy of 98%. All the other performance metrics, including precision, recall, and f1 are higher than 96%, indicating the model's high predictability. In addition, the results showed that while the features measuring the difference between the scheduled date of the milestone 10 and the scheduled dates of other milestones are not influential in the prediction of the milestone 10, the difference between the dates of Line_SOP, Line_RAS, and SCP and scheduled date of milestone 10 is significant.

In the last scenario, we supposed that the firm does not track a shipment at all but still wants to know if the shipment will be delivered to the destination on time or not. In other words, the firm has neither information on meeting the milestones 1 through 9 nor on other time-dependent features such as Line_SOP_date, Line_RAS_date, and SCP date. Hence in this scenario, we supposed that the firm has no time-dependent features and wants to use only time-independent features such as supplier location, line number, shipment point, material type, quantity ordered, etc., to predict if Milestone 10 will be met on time. Again, we developed a random forest model, and the results showed that the model could predict meeting milestone 10 with 88.9% of cross-validation accuracy, which is a reasonable accuracy.


# 7. Conclusions and Future Work
This project developed supervised machine learning models to predict if a shipment delivery will be on time in logistics. On-time delivery is one of the most challenging logistics problems. All the suppliers and third-party logistics companies try to predict delivery time accurately and schedule their shipment delivery accordingly. We followed several modeling scenarios depending on if the firms track a shipment at different delivery stages and how much information it has on shipment delivery. In the first scenario, we showed that if the firm tracks its shipments at different stages (milestones), it will predict if the delivery to the end-user will be on time or not with high accuracy. This model requires a firm to have a tracking system to collect data from a shipment at different stages and has a rich shipment database and information technology infrastructures. However, many logistics firms might not have access to this information; therefore, in the second scenario, we developed a supervised machine learning model to predict if a shipment will be delivered on time without tracking shipment information at different stages. In this model, we only used the firm's scheduled dates for shipment delivery and other features such as destination, origin, shipment type, material type, the quantity of the shipment, etc., to predict if the delivery will be on time. The results showed that the model is still able to predict meeting on-time delivery with high accuracies. Finally, in the last modeling scenario, we assumed that the firm does not have any schedule for the shipment delivery at different stages and only knows if the shipment will arrive on time to the final destination. For this purpose, we developed a machine learning model based on time-independent features. The results showed that we could predict if a shipment delivery will be on time with about 89% accuracy, which is reasonable accuracy in this case.

The results show that the use of supervised machine learning models can significantly help a logistics firm to predict if the delivery will be met its scheduled date or not. As a result, the firm can predict the shipment that is more likely to have a delivery delay and adjust its schedule. Also, for future shipments, the firm can set the scheduled dates of similar shipments more accurately. This significantly reduces the negative consequences of delayed delivery and increases customer satisfaction as on-time delivery is one of the most important criteria influencing user satisfaction in logistics and supply chain networks.

For future work, several modeling and technical approaches can be considered. First, in this project, we only predict if a shipment will meet its scheduled delivery time or not. In other words, the target feature was binary in this study; however, in the future, we can consider a numerical target feature showing the amount of delay in days. In other words, instead of using a binary feature, we might use a numerical feature measuring the difference between the scheduled and actualized delivery dates in days. Second, in this study, we applied simple methods such as calculating the correlation between the target feature and predictors and the importance of features obtained from the random forest to select the most significant features. We can use more reliable feature selection methods such as forward feature selection, backward feature selection, or information gain to select the features in future work. Finally, we applied a simple encoder for encoding the categorical features that might affect the performance of some machine learning techniques such as SVM and logistics regression. Therefore, in future work, we can use more reliable encoding techniques such as one-hot encoding.  


# 8. References:
This could include the revised key papers, texts, or websites that you may use to develop your project.

[1] Otto Motors (2017), Being on Time, Every Time: On-Time Delivery & Customer Satisfaction, https://ottomotors.com/blog/on-time-delivery-manufacturing

[2] Zhang, J., Lam, W. H., & Chen, B. Y. (2016). On-time delivery probabilistic models for the vehicle routing problem with stochastic demands and time windows. European Journal of Operational Research, 249(1), 144-154.

[3] Lean Manufacturing & Operations Management, http://www.leanmanufacture.net/kpi/ontimedelivery.aspx

[4] Lingaro Group (2020), On Time Delivery - The Full Story Behind the Metric and Its Potential, https://lingarogroup.com/blog/on-time-delivery-the-full-story-behind-the-metric-and-its-potential/

[5] Keebler, J.S., et al., 1999. Keeping score – measuring the business value of logistics in the supply chain. Oakbrook, IL:Council of Logistics Management

[6] Gunasekaran, A., Patel, C., & McGaughey, R. E. (2004). A framework for supply chain performance measurement. International Journal of Production Economies, 87, 333-347

[7] Stock, J.R. and Lambert, D.M., 2001. Strategic logistics management. New York: McGraw-Hill

[8] Forslund, H. and Jonsson, P., 2007. Dyadic integration of the performance management process: a delivery service casestudy. International Journal of Physical Distribution & Logistics Management, 37 (7), 546–567




# Support Materials
Provide a list of materials that support your project, for example, the notebooks and data sources.

# Declaration of academic integrity and responsibility

In your report, you should include a declaration of academic integrity as follows:

```
With my signature, I certify on my honor that:

The submitted work is my and my teammates' original work and not copied from the work of someone else.
Each use of existing work of others in the submitted is cited with proper reference.
Signature: ____________ Date: ______________
```

# Credit
The above project template is based on a template developed by Harvard IACS CS109 staff (see https://github.com/Harvard-IACS/2019-CS109A/tree/master/content/projects).
