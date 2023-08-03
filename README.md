# Product Sales Prediction

Hello and welcome to my analysis and prediction of product sales!

The data used for this analysis originated from Kaggle and can be found here at sales_prediction.csv in this repository. 

What am I going to do with this data?

Here are the steps I will use in order to analyze this sales data and make meaningful predictions.
* Initial Analysis & Findings
* Machine Learning Models
* Deep Analysis & Findings
* Data Driven Recommendations
* Conclusion

# Initial Analysis & Findings

What was I able to find with a cursory glance at the data, so to speak?

Below are just a few of the correlations that I could find in the data relating to product sales. 

![Correlation](images/product_sales_corr.png)

Based on this heatmap of correlations, there are two features which have a positive relationship with sales. 
* Item Maximum Retail Price
* Item Visibility

# Predictive Models 

So far, several models have been attempted with certain models showing quite a lot of potential. In my first notebook titled "prediction_of_product_sales_j_hunter.ipynb" the two best models were the gradient boosting regressor and the neural network. The gradient boosting regressor has comparatively low root mean squared error and a reasonably high R^2 score of 60%. This model with some refinement is looking rather promising. 

In my notebook titled "Project 1 - Revisited.ipynb", I went about searching for the best features worth focussing in on. Out of both models attempted in this particular notebook, I chose the random forest model due to its high training R^2 score compared to the other model that I tried, which was a linear regressor. The random forest model allowed me to discover the coefficients worth focussing in on, as can be seen in the figure below.

![Importance](images/rf_importance.png)

Here we see the five most important features. 
* Item Price
* Grocery store
* Visibility
* Weight
* Type 3 Supermarket

# SHAP Explanations

In order to better construct an idea of exactly how the top features are affecting the target, I used the SHAP library in order to create a couple of helpful visualizations. Below can be seen a graph of the top features according to this SHAP framework.

![SHAP](images/shap_bar.png)

We can see that there are similarities with the graph above this one. Both ways of identifying key features agree that item MSRP and the outlet type being a grocery store are vitally important when it comes to predicting product sales. Other importances do vary but are still relevant according to both methods of observing the feature data.

Below we can get a sense of exactly how each feature alter's the model's predictions. Item MSRP has a profound impact on product sales, which is a fairly obvious observation. Though, the more specific interpretation is that a lower price will generally lead to a higher number of sales. We can also see that if the outlet is a grocery store, there will be a significant decrease in product sales. If the outlet is a type 3 supermarket; however, there will be a marked increase in product sales. The relationship between outlet type and product sales can also be seen in the next figure below the SHAP feature data.

![SHAP](images/shap_dot.png)

![Correlation](images/sales_by_outlet_type.png)
