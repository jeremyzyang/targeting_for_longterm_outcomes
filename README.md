# targeting_for_longterm_outcomes

The code contains four Jupyter Notebooks that each performs a main subtask. 

The analysis is organized in three steps: 1) imputing surrogate index, 2) using cross-fitting to estimate an outcome model for surrogate index, 3) constructing doubly-robust scores with the outcome model and optimizing and evaluating policy with doubly-robust scores. Main results reported in the paper are shown. See the description of each file below.

1. Imputing surrogate index

The first step uses surrogate index to predict the long-term revenues. 

Input data: historical data on 18-month and 3-year revenue, covariates and surrogates; covariates and surrogates for users in the two experiments. 
Output data: surrogate index for 18-month and 3-year revenue for users in the two experiments.

2. Using cross-fitting to estimate an outcome model for surrogate index

The second step uses cross-fitting to estimate an outcome model for surrogate index. 

Input data: surrogate index and covariates for users in the two experiments. 
Output data: predicted outcome under each potential treatment condition for users in the two experiments.

3. Constructing doubly-robust scores with the outcome model and optimizing and evaluating policy with doubly-robust scores

The third step uses surrogate index and predicted outcomes to construct doubly-robust scores and then use the doubly-robust scores to optimize and evaluate policy. It produces results in Table 1 and Figure 3.

Input data: surrogate index, covariates, and predicted outcomes for users in the two experiments. 
Output data: optimized policy and optimal actions for users in the two experiments, difference in policy values.

4. Estimating treatment effects 

This is not part of the policy learning pipeline. It produces results in Figure D.3-D.8 and Table D.4.

Input data: observed churn and revenue, and covariates for users in the two experiments.
Output data: estimated treatment effects.
