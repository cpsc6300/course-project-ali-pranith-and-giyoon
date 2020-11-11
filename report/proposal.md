# TITLE: Will be the shipment on-time? A shipment delivery prediction in a large supply chain network using machine learning
## Team Members: Ali Shirzadibabakan, Pranith Abbarajou, Giyoon Kwag
## Date: November 10, 2020

# Project Description
## Probelm Statement and Motivation
One of the most challenging problems in a supply chain network is meeting the scheduled shipment delivery. A firm has a limited time and budget and needs to receive its shipment on time. For example, the common issues that affect the timeliness of deliveries include poor shipment delivery planning, lading errors, and attaching incorrect documentation(Lingaro Group,2020). When a customer requests a shipment, the provider schedule a time to provide that shipment from an origin to the destination. There are a variety of factors affect the shipment delivery. Therefore, provider and customer would like to know whether the shipment would meet the scheduled delivery or not. There are many way to improve delivery times. For example, firms achieve on time delivery by planning proper schedules that are in-line wiht capacitiies, proper tracking and collaborating with suppliers, accurate forecasting abd monitoring effeciency, and integrating and integrating and controlling systems. Machine Learning methods can considerably help with this issue as they can utilize the historical data on shipment delivery and predict if a shipment with specific characteristics (origin, destination, shipment type, etc.) will deliver on time. This prediction model substantially helps provider to improve its supply chain network and provide more real deliver dates to the customers. Also, if the prediction of the delivery is much more than expected, they might figure out the main issues to enhance the network in the future. They can also notice the customer that the shipment might not deliver on time.

## Introduction and Description of Data
Meeting delivery requirements and customers’ expectations is very important for every business.In fact, 4 of the top 6 challenges reported by 2020 MHI Annual Industry Report are related to higher customer expectations and faster delivery. Increasing attention is given to on-time delivery of goods in the logistics and distribution industry. With uncertainties in customer demands, on-time deliveries cannot be ensured frequently (Zhang et al., 2016). On time delivery is defined as a measure of process and supply chain efficiency which measures the amount of finish goods or services delivered to customers on time and in full. It helps determine how efficiently we are meeting our customer's or agreed deadlines[3].  Weak on-time delivery performance not only negatively affects customer satisfaction, but also indicates poor production efficiency and materials handling procedures. Poor on-time delivery can cause several issues that affect other aspects of a company’s supply chain network such as production delays due to material shortages, avoidable expedited shipping costs, and customer dissatisfaction (Otto Motors, 2017). Therefore, suppliers need to accurately predict delivery time and according to this prediction, provides a precise delivery time to the customer. Also, they need to know what shipments might been delivered delayed based on the historical data. This helps them to notice the customer and provide more actual delivery time to the customer. Furthermore, on time delivery is not just about the customer satisfaction and deadlines. Not meeting on time delivery can affect the functioning of the entire business, including firm's financial stability (Lingaro Group,2020),  It In this project, we want to utilize supervised machine learning techniques to predict whether a shipment will meet its scheduled delivery time or not. For this purpose, we collected data from a large Engineering, Procurement, and Construction (EPC) firm that has provided data for individual items being shipped through its supply chain network. The dataset contains more than 93,000 records and 137 features about the characteristics of shipments, origin, destination, and 10 milestones that the supplier has defined to track a shipment from the production to customer. These milestones show if a shipment has met different scheduled time milestones or not. In other words, there are two dates (i.e. scheduled and actual) indicating that if that milestone has met or not. The tenth milestone is the shipment delivery to the final customer that we want to predict.

# Plan
1- Data cleaning up and data preparation: 2 weeks

2- Feature Selection for different prediction scenarios: 1 weeks

o	Scenario 1: We are at the stage after Milestone 9 and know whether the Milestones 1 through 9 have been met or not.

o	Scenario 2: We are at the early stage before meeting any milestones. Therefore, in this scenario, we assumed that we do not have any information about meeting the Milestones 1-9.

o	Scenario 3: We supposed that we do not have any information on meeting the milestones 1-9 and on other time-related features. In other words, in this scenario, we only used time-independent features to predict meeting Milestone 10.

3- Implementation and evaluation of different ML models: 1 weeks

4- Documentation and preparation report and website: 2 weeks

of computing and storage requirements:

As our dataset is not too big, we can do this project using a typical desktop. 

# References:

[1] Otto Motors (2017), Being on Time, Every Time: On-Time Delivery & Customer Satisfaction,  https://ottomotors.com/blog/on-time-delivery-manufacturing

[2] Zhang, J., Lam, W. H., & Chen, B. Y. (2016). On-time delivery probabilistic models for the vehicle routing problem with stochastic demands and time windows. European Journal of Operational Research, 249(1), 144-154.

[3] http://www.leanmanufacture.net/kpi/ontimedelivery.aspx

[4] Lingaro Group (2020), On Time Delivery - The Full Story Behind the Metric and Its Potential, https://lingarogroup.com/blog/on-time-delivery-the-full-story-behind-the-metric-and-its-potential/
