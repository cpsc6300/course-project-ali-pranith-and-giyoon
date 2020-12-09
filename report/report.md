

# TITLE: A shipment delivery prediction in a large supply chain network using machine learning

## Team Members: Ali Shirzadibabakan, Pranith Abbarajou, Giyoon Kwag
## Date: December 5th, 2020

# Probelm Statement and Motivation
This should be a brief and self-contained decription of the problem that your project aims to solve and what motivated you to solve this problem.

One of the most challenging problems in a supply chain network is meeting the scheduled shipment delivery. A firm has a limited time and budget and needs to receive its shipment on time. For example, the common issues that affect the timeliness of deliveries include poor shipment delivery planning, lading errors, and attaching incorrect documentation(Lingaro Group,2020).

When a customer requests a shipment, the provider schedule a time to provide that shipment from an origin to the destination. There are a variety of factors affect the shipment delivery. Therefore, provider and customer would like to know whether the shipment would meet the scheduled delivery or not. There are many way to improve delivery times. For example, firms achieve on time delivery by planning proper schedules that are in-line wiht capacitiies, proper tracking and collaborating with suppliers, accurate forecasting abd monitoring effeciency, and integrating and integrating and controlling systems.

Machine Learning methods can considerably help with this issue as they can utilize the historical data on shipment delivery and predict if a shipment with specific characteristics (origin, destination, shipment type, etc.) will deliver on time. This prediction model substantially helps provider to improve its supply chain network and provide more real deliver dates to the customers. Also, if the prediction of the delivery is much more than expected, they might figure out the main issues to enhance the network in the future. They can also notice the customer that the shipment might not deliver on time.

Here is our resarch question: What factors are useful/important for predicting whether a shipment is going to be on-time? 

# Introduction and Description of Data
Description of relevant knowledge. Why is this problem important? Why is it challenging? Introduce the motivations for the project question and how that question was defined through preliminary EDA.

Meeting delivery requirements and customers’ expectations is very important for every business. In fact, 4 of the top 6 challenges reported by 2020 MHI Annual Industry Report are related to higher customer expectations and faster delivery. Increasing attention is given to on-time delivery of goods in the logistics and distribution industry. With uncertainties in customer demands, on-time deliveries cannot be ensured frequently (Zhang et al., 2016). On time delivery is defined as a measure of process and supply chain efficiency which measures the amount of finish goods or services delivered to customers on time and in full. It helps determine how efficiently we are meeting our customer's or agreed deadlines[3].

Weak on-time delivery performance not only negatively affects customer satisfaction, but also indicates poor production efficiency and materials handling procedures. Poor on-time delivery can cause several issues that affect other aspects of a company’s supply chain network such as production delays due to material shortages, avoidable expedited shipping costs, and customer dissatisfaction (Otto Motors, 2017). Therefore, suppliers need to accurately predict delivery time and according to this prediction, provides a precise delivery time to the customer. Also, they need to know what shipments might been delivered delayed based on the historical data. This helps them to notice the customer and provide more actual delivery time to the customer. Furthermore, on time delivery is not just about the customer satisfaction and deadlines.

Not meeting on time delivery can affect the functioning of the entire business, including firm's financial stability (Lingaro Group,2020), It In this project, we want to utilize supervised machine learning techniques to predict whether a shipment will meet its scheduled delivery time or not.

For this purpose, we collected data from a large Engineering, Procurement, and Construction (EPC) firm that has provided data for individual items being shipped through its supply chain network. The dataset contains more than 93,000 records and 137 features about the characteristics of shipments, origin, destination, and 10 milestones that the supplier has defined to track a shipment from the production to customer. These milestones show if a shipment has met different scheduled time milestones or not. In other words, there are two dates (i.e. scheduled and actual) indicating that if that milestone has met or not. The tenth milestone is the shipment delivery to the final customer that we want to predict.

# Literature Review/Related Work 
This could include noting any key papers, texts, or websites that you have used to develop your modeling approach, as well as what others have done on this problem in the past. You must properly credit sources.

The concept of on-time delivery measures performance regarding perfact delivery and customer service level with delivery reliability and order completeness(Gunasekaran et al., 2004). On-time delivery, lead time length, delivery reliability, and inventory service level are examples of common delivery service performance variables in dyadic customer–supplier interfaces. Among them, on-time delivery is often considered the most important performance variable when orders are seldom changed in the supply chain(Keebler et al.1999, Stock and Lambert 2001). Most companies, regardless firm size and industry, normally have on-time as in important supply perfromnance metric. When defining on-time delivery, there are several different issues that firms need to consider(Forslund and Jonsson 2007). 

The first concerns the measurement object, which may be the number of orders, individual items or, order lines. The second concerns the time unit for measuring being on time. It could vary between the correct hour, day, week or within a specific time window. The third concerns the measurement point, i.e. where along the supply chain the order is considered to be delivered. The fourth concerns the comparison date for an actual delivery date in order to decide if it is on time or not. However, few studies have examined in any depth how delivery service performance should be managed, and almost none have focused on measuring on-time delivery.

# Modeling Approach

For the prediction of meeting Milestone 10, we followed 3 different modeling scenarios:
Scenario 1: We are at the stage after Milestone 9 and know whether the Milestones 1 through 9 have been met or not.

Scenario 2: We are at the early stage before meeting any milestones. Therefore, in this scenario, we assumed that we do not have any information on whether Milestones 1 trough 9 will be met or not.

Scenario 3: We supposed that we do not have any information on meeting the Milestones 1 trough 9 and on other time-dependent features such as Line_SOP_date, Line_RAS_date, etc. In other words, in this scenario, we only used time-independent features such as ORIGIN, DESTINATION, SHIPMENT TYPE, SUPPLIER, etc. to predict meeting Milestone 10.



## Scenario 1: We are at the stage after Milestone 9

### Model 1: Using binary features for meeting the Milestones 1-9

In Model 1, in addition to the available features, we included the binary features showing whether the milestones 1-9 have been met or not. We tuned Random Forest to determine the best values for the hyperparameters of max_depth, max_features, and min_samples_leaf. Also, we determined the importance of features and selected the most important ones using the importance of features obtained from Random Forest. Finally, we selected the most important features, trained the tuned Random Forest model, and obtained the performance metrics using test dataset.

![figure1](https://user-images.githubusercontent.com/61207345/101667738-b16b6480-3a1d-11eb-976d-b0db726cc1dc.png)


selected_features = ['SUPPLIER_LOCATION', 'LINE_NUMBER', 'ITEM_PRIME_ID', 'SHIP_POINT', 'RECEIVING_ONLY_PO', 'MILESTONE_2_meet', 'MILESTONE_3_meet', 'MILESTONE_4_meet', 'MILESTONE_6_meet', 'MILESTONE_8_meet','MILESTONE_9_meet', 'MILESTONE_10_meet']
                     
Mean Cross-Validated Accuracy: 0.9142750054122457

Training Accuracy: 0.9195601166070201

Testing Accuracy: 0.9169589534553039


![figure2](https://user-images.githubusercontent.com/61207345/101670361-0eb4e500-3a21-11eb-929a-dade35cfce64.png)





### Model 2: Using difference features for meeting Milestones 1-9

In Model 2, instead of using the binary features for meeting the milestones 1 through 9, we used the numerical features showing the difference between the scheduled and actualized dates for the milestones 1 through 9. We tuned Random Forest to determine the best values for the hyperparameters of max_depth, max_features, and min_samples_leaf. Also, we determined the importance of features and selected the most important ones using the importance of features obtained from Random Forest. Finally, we selected the most important features, trained the tuned Random Forest model, and obtained the performance metrics using test dataset.

![figure3](https://user-images.githubusercontent.com/61207345/101671314-55570f00-3a22-11eb-8930-393fb618c58d.png)


selected_features = ['SUPPLIER_LOCATION', 'LINE_NUMBER', 'ITEM_PRIME_ID', 'SHIP_POINT', 'RECEIVING_ONLY_PO',
                     'MILESTONE_2_Diff', 'MILESTONE_3_Diff', 'MILESTONE_4_Diff', 'MILESTONE_6_Diff', 
                     'MILESTONE_8_Diff', 'MILESTONE_9_Diff', 'MILESTONE_10_meet']
                     
Mean Cross-Validated Accuracy: 0.987130651061792

Training Accuracy: 0.9942881520631385

Testing Accuracy: 0.9879609441653238

![figure4](https://user-images.githubusercontent.com/61207345/101671417-7881be80-3a22-11eb-9c93-37dda274cc1d.png)






### Model 3: Dropping Milestones 6 and 8 & Compare the Performance of Various Classification Methods including Random Forest, Decision Tree, SVM, KNN, and Logistic Regression

In Model 3, to increase the size of training and test datasets, we removed the features related to the Milestones 6 and 8 as they have much more Null values compared to other features. Because we want to run different classification methods and compare their performance metrics, we performed a correlation matrix beteen features and selected the highest correlated features with the target feature as the most important features. Then, we tuned the hyperparameters of several classification methods including Random Forest, Decision Tree, SVM, KNN, and Logistic Regression. Finally, we trained the tuned models, obtained the performance metrics using test dataset, and compare the results.

Model 3-1 Random Forest
          
![figure5](https://user-images.githubusercontent.com/61207345/101671525-96e7ba00-3a22-11eb-9c3a-70f713aefec8.png)

Correlation Matrix

![figure6](https://user-images.githubusercontent.com/61207345/101671610-b54db580-3a22-11eb-9acc-112772bdcf62.png)

          
selected_features = ['SUPPLIER_LOCATION', 'LINE_NUMBER', 'ITEM_PRIME_ID', 'SHIP_POINT', 'RECEIVING_ONLY_PO', 
                     'MILESTONE_2_Diff', 'MILESTONE_3_Diff', 'MILESTONE_4_Diff', 'MILESTONE_9_Diff', 'MILESTONE_10_meet']



Mean Cross-Validated Accuracy: 0.9889121228458648

Training Accuracy: 0.9944941893694037

Testing Accuracy: 0.9900937285681628


![figure7](https://user-images.githubusercontent.com/61207345/101671952-37d67500-3a23-11eb-833a-1df006266c8d.png)






Model 3-2 Decision Tree

The best tuned hyperparameters are:
{'max_depth': 15, 'max_features': 9, 'min_samples_leaf': 1, 'min_samples_split': 3}

The Cross Validated Accuracy for the best Model is: 0.9874261764145551

Mean Cross-Validated Accuracy: 0.9873880230048796

Training Accuracy: 0.9939226519337017

Testing Accuracy: 0.9887982930732302


![figure8](https://user-images.githubusercontent.com/61207345/101672144-7d933d80-3a23-11eb-9532-1e26c7e79a1c.png)

 
 
 
 
 
Model3-3 SVM

The best tuned hyperparameters are:
{'C': 50, 'kernel': 'rbf'}

The Cross Validated Accuracy for the best Model is:
0.9225185749666603

Mean Cross-Validated Accuracy: 0.9217184836932603

Training Accuracy: 0.9232044198895027

Testing Accuracy: 0.9225786786557951


![figure9](https://user-images.githubusercontent.com/61207345/101672312-baf7cb00-3a23-11eb-8b7b-bf0e543430f7.png)






Model3-4 KNN

The best tuned hyperparameters are: {'n_neighbors': 1}

The Cross Validated Accuracy for the best Model is: 0.9784911411697467
          
Mean Cross-Validated Accuracy: 0.97883402354555

Training Accuracy: 0.9964945703943608

Testing Accuracy: 0.9809494780156977

![figure10](https://user-images.githubusercontent.com/61207345/101672458-e37fc500-3a23-11eb-919b-1fd937592e2e.png)






Model3-5 Logitstic Regression

The best tuned hyperparameters are: {'C': 10, 'penalty': 'l1'}

The Cross Validated Accuracy for the best Model is: 0.9078491141169747

Mean Cross-Validated Accuracy: 0.9081731153287536

Training Accuracy: 0.9083825490569633

Testing Accuracy: 0.9075668673321649

![figure11](https://user-images.githubusercontent.com/61207345/101672574-0a3dfb80-3a24-11eb-8448-108471c534e8.png)





Comparions of Models


![figure12](https://user-images.githubusercontent.com/61207345/101672654-26419d00-3a24-11eb-9f79-4eb1fba46803.png)


From the comparisions models, we found that Random Forest has the highest accuracy and Logistic Rgression has the lowest accuracy. 




## Scenario 2: We are at the early stage before meeting any Milestone

In Scenario 2, we supposed that we are at the early stage before meeting any milestones. Therefore, there is no information on meeting the Milestones 1 through 9. However, we can include some features showing the difference between the scheduled date of milestone 10 and the scheduled dates of other milestones because the scheduled date of all the Milestones are set at the early stage though we don't know whether these scheduled dates will be met or not. Additionally, we used some new features showing the difference between the scheduled date of milestone 10 and some given dates such as Line_SOP date, Line_RAS date, and SCP date. Because the comparison of the several classification methods in the previous section showed that the Random Forest Model results in better performance, we only run a Random Forest model for this scenario. The importance obtained from the Random Forest shows that while the differences between the scheduled date of milestone 10 and the scheduled dates of other milestones are not important, the differences from Line_SOP date, Line_RAS date, and SCP date are very important.


Radom Forest --- Selecting Features

![figure13](https://user-images.githubusercontent.com/61207345/101673068-a7992f80-3a24-11eb-9f37-abb7dd8c2ace.png)


selected_features = ['REV', 'SUPPLIER_LOCATION', 'LINE_NUMBER', 'PO_PRIME_ID', 'ITEM_PRIME_ID', 'MATERIAL_TYPE', 'SHIP_POINT','RECEIVING_ONLY_PO', 'SCHEDULE_SOP_10_Diff', 'SCHEDULE_RAS_10_Diff', 'SCHEDULE_SCP_10_Diff', 'MILESTONE_10_meet']

The best tuned hyperparameters are: {'max_depth': 20, 'max_features': 7, 'min_samples_leaf': 1}

The Cross Validated Accuracy for the best Random Forest Model is: 0.9775658182879946

Mean Cross-Validated Accuracy: 0.9801449720686802

Training Accuracy: 0.9953120184274985

Testing Accuracy: 0.979885803270179

![figure14](https://user-images.githubusercontent.com/61207345/101673194-dca58200-3a24-11eb-9443-19305a803e0e.png)






## Sceario 3: What if we don't have any time-dependent data?

In Scenario 3, we supposed that we do not have any information on meeting the milestones 1 through 9 as well as on other time-dependent features such as Line_SOP_date, Line_RAS_date, and SCP date. In other words, in this scenario, we supposed that there is no given date in the dataset. Therefore, we only used the time-independent features such as supplier location, line number, and shipment point to predict meeting Milestone 10. We want to know how much time-independent features are able to predict whether the Milestone 10 will be met or not. Again, we only developed a Random Forest model.


Radom Forest --- Selecting Features

![figure15](https://user-images.githubusercontent.com/61207345/101673279-f6df6000-3a24-11eb-90d6-a064dae0f828.png)

selected_features = ['REV', 'SUPPLIER_LOCATION', 'LINE_NUMBER', 'DESTINATION', 'PO_PRIME_ID', 'ITEM_PRIME_ID', 
                     'MATERIAL_TYPE', 'SHIP_POINT', 'RECEIVING_ONLY_PO', 'QTY_ORDERED', 'MILESTONE_10_meet']
                     


The best tuned hyperparameters are: {'max_depth': 15, 'max_features': 7, 'min_samples_leaf': 2}

The Cross Validated Accuracy for the best Random Forest Model is: 0.8642490930752447

Mean Cross-Validated Accuracy: 0.8662704997996059

Training Accuracy: 0.8895492818226844

Testing Accuracy: 0.8652281002355965

![figure16](https://user-images.githubusercontent.com/61207345/101673442-2bebb280-3a25-11eb-9c45-e7ab403a9971.png)




## Sensitivity analysis on the effects of training % vs. testing % on the Random Forest Model

![figure17](https://user-images.githubusercontent.com/61207345/101673739-8e44b300-3a25-11eb-8863-36e7566d3249.png)


The maximum Cross-Validated is 0.8647578610958556 obtained from the test sample size = 0.2

The maximum training is 0.9061696658097687 obtained from the test sample size = 0.9500000000000001

The maximum testing accuracy is 0.8653887342043264 obtained from the test sample size = 0.2


## Prediction of meeting Milestone 10 for 10 random samples



<img width="925" alt="Screen Shot 2020-12-09 at 1 57 17 PM" src="https://user-images.githubusercontent.com/61207345/101674452-85081600-3a26-11eb-9abc-b7439626a40a.png">





# Project Trajectory, Results, and Interpretation 

Briefly summarize any changes in your project goals or implementation plans you have made.
These changes are a natural part of any project, even those that seem the most straightforward at the beginning.
The story you tell about how you arrived at your results can powerfully illustrate your process. 

Next, show your results. How well does your model and/or implementation perform? Did you meet your goals?

Finally, give some interpretation. What do your results mean? What impact will your work have?

# Conclusions and Future Work
Summarize your results, the strengths and short-comings of your results, and speculate on how you might address these short-comings if given more time.

# References:
This could include the revised key papers, texts, or websites that you may use to develop your project.

[1] Otto Motors (2017), Being on Time, Every Time: On-Time Delivery & Customer Satisfaction, https://ottomotors.com/blog/on-time-delivery-manufacturing

[2] Zhang, J., Lam, W. H., & Chen, B. Y. (2016). On-time delivery probabilistic models for the vehicle routing problem with stochastic demands and time windows. European Journal of Operational Research, 249(1), 144-154.

[3] http://www.leanmanufacture.net/kpi/ontimedelivery.aspx

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
