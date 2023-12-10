# targeting_for_longterm_outcomes

The code contains six Jupyter notebooks in R each performing a main subtask. The first four notebooks reproduce the main results in the paper with the original data and the fifth and sixth notebooks generate synthetic data that preserves the joint distribution of the original data and conduct analysis on the synthetic data.

The analysis that reproduces the main results in the paper is organized into three steps: 1) imputing a surrogate index, 2) using cross-fitting to estimate an outcome model for the surrogate index, 3) constructing doubly-robust scores with the outcome model and optimizing and evaluating policy with doubly-robust scores. See the description of each file below.

1. Imputing surrogate index\
The first step uses the surrogate index to predict long-term revenues.

Input data: historical data on 18-month and 3-year revenue, covariates and surrogates; covariates and surrogates for users in the two experiments. \
Output data: surrogate index for 18-month and 3-year revenue for users in the two experiments.

2. Using cross-fitting to estimate an outcome model for a surrogate index\
The second step uses cross-fitting to estimate an outcome model for the surrogate index.

Input data: surrogate index and covariates for users in the two experiments. \
Output data: predicted outcome under each potential treatment condition for users in the two experiments.

3. Constructing doubly-robust scores with the outcome model and optimizing and evaluating policy with doubly-robust scores\
The third step uses a surrogate index and predicted outcomes to construct doubly-robust scores and then use the doubly-robust scores to optimize and evaluate policy. It produces results in Table 1 and Figure 3.

Input data: surrogate index, covariates, and predicted outcomes for users in the two experiments. \
Output data: optimized policy and optimal actions for users in the two experiments, the difference in policy values.

4. Estimating treatment effects\
This is not part of the policy learning pipeline. It produces results in Figure D.3-D.8 and Table D.4.

Input data: observed churn, revenue, and user covariates in the two experiments. \
Output data: estimated treatment effects.

5. Generating synthetic data \
This is not part of the policy learning pipeline. It generates synthetic data that preserves the joint distribution of the original data in the first experiment.

Input data: original data. \
Output data: synthetic data.

6. Optimizing and evaluating policy on synthetic data \
This is not part of the policy learning pipeline. It conducts policy optimization and evaluation of the synthetic data.

Input data: synthetic data. \
Output data: optimized policy and difference in policy values.

Description of the data

The variables can be divided into four categories.

1. Pre-treatment covariates
   
The pre-treatment variables contain demographics (e.g., zip code), account activities (e.g., billing address change, credit card expiration date, complaints), and content consumption before the treatment (e.g., when and what article section they read). Variables are named in the following way:
- Activity name + num/first/last. Activity names are self-explanatory. For instance, “billing_address_change_num” is the number of times that a user changed her billing address, “billing_address_change_first” is the first time a user changed her billing address, “billing_address_change_last” is the last time a user changed her billing address.
- Article section name + last month/last 3 months/last 6 months. Article section names are self-explanatory. For instance, “politics_last_3month” is the number of articles a user read in the politics section in the last 3 months.

2. Treatment
   
- “Treated” is a binary variable for treatment in the first experiment.
- “Condition” is a categorical variable that encodes the name of the 6 treatments
and 1 control condition in the second experiment.
- “Risk score” is the predicted churn probability of a user.
- “P_treated” is the probability of a user receiving the treatment.

3. Surrogates
   
Surrogate variables contain short-term revenues and when and what article section a user reads after the treatment. Variables are named in the following way:
- Revenue + 1m/2m/3m/4m/5m/6m. For instance, "rev_3m" is the 3-month revenue after the treatment.
- Article section name + 1m/2m/3m/4m/5m/6m. Article section names are self-explanatory. For instance, “politics_1m” is the number of articles a user read in the politics section 1 month after the treatment.

4. Outcomes

- "Rev" is the observed revenue.
- Rev_x is the surrogate index of long-term revenues computed with surrogates
from the first x months. For instance, "rev_3" is the surrogate index of long-term revenue imputed with surrogates from the first 3 months.
- Y0_x and Y1_x are outcomes predicted with the outcome model using surrogates
from the first x months. For instance, "Y0_3" and "Y1_3" are the predicted outcomes without and with the treatment using surrogates from the first 3 months.


