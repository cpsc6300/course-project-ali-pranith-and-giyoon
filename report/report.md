

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

+ Describe the baseline model.
+ Describe your implementations beyond the baseline model and the design choices that you have made.

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
