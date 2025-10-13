---
layout: page
title: Dobbs v. Jackson Women Health
description: a study of abortion access impacts on women labor
img: assets/img/dobbs_1.png
importance: 2
# category: causal inference
---

# Impact of Abortion Access on Women's Labor Force Participation

This blog contains the analysis for an empirical study measuring the potential impact of changes in abortion access, specifically following the **Dobbs v. Jackson Women's Health Organization** Supreme Court decision in June 2022, on women's labor force participation.

The central hypothesis is that women without access to safe abortion may leave the labor force due to increased pregnancy and childcare responsibilities.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dobbs_1.png" 
        title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dobbs_3.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dobbs_2.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Research Approach

The study employs a **Difference-in-Differences (DiD)** identification strategy to compare labor force outcomes before and after the **Dobbs** decision across states with different post-Dobbs abortion policies.

### State Selection

To implement the DiD strategy effectively, states were selected based on geographic proximity and policy divergence:

| Group | States (FIPS Codes) | Abortion Policy |
| :--- | :--- | :--- |
| **Treatment** | **Idaho** (16), **Wisconsin** (55) | Strict/Restrictive laws post-Dobbs |
| **Control** | **Oregon** (41), **Minnesota** (27) | Protective laws post-Dobbs |

### Key Assumptions
* **Parallel Trends Assumption:** Labor force trends in both the treatment and control states would have been similar in the absence of the Dobbs decision.
* **No Spillover Effects:** The policy changes did not cause significant migration for abortion access that would confound the labor force data.
* **No Other Simultaneous Shocks:** No other major, unrelated labor policy changes disproportionately affected one group of states.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/dobbs_state.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/dobbs_plot.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

## Data

The analysis uses monthly data from the **Current Population Survey (CPS)**, covering the period from **January 2020 to March 2024**.

* **Source:** Data was sourced from **IPUMS CPS**.
* **Data File:** `data/cps_00003.csv`
* **Key Variables:** State, Employment Status (`EMPSTAT`), Sex, and Age.
* **Sample:** Limited to working-aged individuals (**15 to 64 years old**).
* **Outcome Variable:** `WORKING` (Dummy: 1 if `EMPSTAT` = 10 "At work", 0 otherwise).

### Time Periods for DiD
* **Pre-Dobbs Period:** January 2022 – May 2022
* **Post-Dobbs Period:** January 2023 – May 2023

---

## Analysis and Results

### Regression Model (Simplified for Women Only)

The core analysis uses an OLS regression on the sub-sample of women:

$$
\text{Working} = \beta_0 + \beta_1 \cdot \text{STRICT} + \beta_2 \cdot \text{POST} + \beta_3 \cdot (\text{STRICT} \times \text{POST}) + \epsilon
$$

The coefficient of interest is $\beta_3$, which captures the **Difference-in-Differences treatment effect**.

### Key Finding

| Coefficient | Estimate ($\beta_3$) | P-value |
| :--- | :--- | :--- |
| $\text{STRICT} \times \text{POST}$ | **0.0136** | **0.311** |

* **Interpretation:** The positive coefficient (0.0136) suggests that women in strict-abortion states were **1.36 percentage points more likely** to be working in the post-Dobbs period compared to women in protective states, relative to the pre-Dobbs difference.
* **Statistical Significance:** The p-value of **0.311** is high, meaning the observed effect is **not statistically significant** at common critical levels (e.g., 5% or 10%).

### Conclusion
Based on this specific DiD analysis using the selected states and time periods, **there is no clear statistical evidence** that the Dobbs decision had a causal effect on women’s labor force participation. The estimated effect, while positive, is not statistically significant.

## Repository Structure

* `notebook/dobbs_jackson_health.ipynb`: The main Jupyter Notebook containing the data preparation, DiD model estimation, and results interpretation.
* `data/cps_00003.csv`: The raw data file used for the analysis.