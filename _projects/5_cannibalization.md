---
layout: page
title: Predict Organic Traffic Cannibalization Rate on E-commerce Platform
description: 
img: assets/img/colgate.png
importance: 5
# category: machine learning
related_publications: false
---

## Project Overview 📈

[cite_start]In collaboration with a worldwide Consumer Product Groups (CPG) company, this study addresses the critical challenge of **advertising spend optimization** on major e-commerce platforms like **JD.com** in China[cite: 6, 11, 39]. [cite_start]Businesses on these platforms struggle to measure the true **Return on Investment (ROI)** of their paid search advertising because the data provided is often highly aggregated, making it unclear whether a sale resulted from a paid ad (**paid search**) or if the customer would have purchased the product anyway (**organic search**)[cite: 7, 8, 9]. [cite_start]This phenomenon, where paid advertising captures sales that would have occurred organically, is known as **cannibalization**[cite: 6, 10, 19].

Our primary goal was to develop a predictive methodology to:
1.  [cite_start]**Estimate the cannibalization rate** that exists on the JD.com platform[cite: 40].
2.  [cite_start]**Identify key variables** to help the firm allocate their ad budget more efficiently to **minimize organic purchase cannibalization**[cite: 15, 41].

---

## Methodology and Data Analysis 📊

[cite_start]We analyzed a sample window of the CPG company's marketing investments on JD.com, utilizing six different datasets which included four paid ad reports, a business brand category report, and an operating report[cite: 11, 82, 84]. [cite_start]The data included metrics for different ad channels: **Banner ads (jd)**, **Search ads (ep)**, **Automated search ads (con)**, and **Feed ads (shop)**[cite: 85, 89].

### Defining and Modeling Cannibalization

The **Cannibalization Rate** was defined as the percentage loss in marginal organic view growth captured by marginal paid view growth as investment increases. [cite_start]This assumes cannibalization exists when the marginal organic growth rate is reduced and captured by the rise in the marginal paid growth rate[cite: 125, 128].

[cite_start]$$\text{Cannibalization Rate} = \frac{\Delta \text{ Marginal Organic View Growth Rate}}{\Delta \text{ Marginal Paid View Growth Rate}}$$ [cite: 129, 130]

Our modeling approach involved a staged methodology:
1.  [cite_start]**Data Pre-Processing** including outlier treatment (filtering out major promotion holidays like 6/18, 11/11, 12/12) and removing highly correlated or near-zero variation variables[cite: 151, 152, 153].
2.  [cite_start]**Building Descriptive Models** (Linear Regression) to identify the impact of variables on the Cannibalization Rate[cite: 162, 164].
3.  [cite_start]**Building Predictive Models** (Gradient Boosting Machine, Neural Network, Random Forest, Regression) to cross-validate variable importance[cite: 165, 166].

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Methodology_Flow_Chart.png" title="Methodology Flow Chart" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The detailed flow chart for the model building and variable selection process. </div>

### Key Findings on Channel Performance

[cite_start]Exploratory analysis showed that **Search ads** had the highest average click rate compared to Banner ads, Automated search ads, and Feed ads[cite: 109, 110].

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Average_click_rate_by_ads_channel.png" title="Average Click Rate by Ad Channel" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    [cite_start]Average click rate by ad channel, showing Search ads had the highest rate[cite: 104, 109]. </div>

[cite_start]Furthermore, the cannibalization rate itself showed no clear time series pattern (trend or seasonality) but did fluctuate significantly around major promotion dates[cite: 102, 103, 173, 174].

---

## Results and Recommendations ✨

### Significant Variables for Cannibalization

[cite_start]Our descriptive and predictive models demonstrated a crucial insight: investment in each ad channel's **total cost is generally *not* directly related to the cannibalization rate**[cite: 207, 214].

[cite_start]Instead, **customer behaviors and ad performance metrics**, particularly **click-related parameters**, were more significant predictors[cite: 208, 214]. [cite_start]Channels like **Search ads (ep)** and **Automated search ads (con)** were found to be more valuable to the goal of predicting the rate than Banner ads or Feed ads[cite: 211, 215].

Key significant variables included:
* [cite_start]`ep Click Rate` (Search ads Click Through Rate) [cite: 213]
* [cite_start]`con Turnover Rate` (Automated search ads) [cite: 213]
* [cite_start]`jd Number of Direct Adding to Cart` (Banner ads) [cite: 213]

<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Variables_Importance_Bar_Graph.png" title="Variables Importance Bar Graph" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    [cite_start]Variable Importance Bar Graph from the boosted tree model, highlighting the superiority of clicks-related parameters over total cost[cite: 214, 216]. </div>

### Conclusion for Spend Optimization

[cite_start]To maximize the effect of advertising investment and minimize cannibalization, the company should shift its focus away from raw investment amounts and toward **advertising quality or performance metrics**, such as **ROI** or **click rate**[cite: 235, 237]. [cite_start]Targeting efforts on **Search ads** and **Automated search ads** is recommended due to the strong predictive relationship between customer clicks in these channels and the cannibalization rate[cite: 236].

[cite_start]The final recommendation is to conduct an **A/B test** to validate these findings with real market responses before implementing any major strategic changes[cite: 239, 240].