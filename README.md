# Analyze-A-B-Test-Results


## Problem Definition:
For this project, we will be working to understand the results of an A/B test run by an e-commerce website.  Our goal is to work through this notebook to help the company understand if they should implement the new page, keep the old page, or perhaps run the experiment longer to make their decision.


### Data Preparation:
1. check for nulls
2. check for duplicates.
3. drop the unreasonable records.


### Hypothesis Test:
we assume that the old page is better unless the new page proves to be definitely better at a Type I error rate of 5%

1. The null hypothesis is :  **$p_{new}$** <= **$p_{old}$**
* means: the conversion rate to the old page is greater or equal to the conversion rate to new page

2. The Alternative hypothesis is : **$p_{new}$** > **$p_{old}$**
* means: the conversion rate to the new page is greater than the conversion rate to the old page

** Results**:
  * we found that the p-value is large `0.9` then we shouldn't move away from the null hypothesis. that is we **failed to reject** the null hypothesis.

### Regression Approach:
we showed that the result we acheived in the A/B test part can also be acheived by performing regression.
Since each row is either a conversion or no conversion, so we perform **logistic regression**

**Steps**:
  1. we create a new column ab_page and encoded it to have 1 when an individual receives the treatment.
  2. we add a new column , the intercept which is neccessary to the model.
  `Note` According to point 1, the null hypothesis is that the probability of conversion when an individual recieves the new page is less than the probability when an individual recieves the old page **$p_{new}$** > **$p_{old}$**, which is the opposite to the one in the Hypothesis Test.
  
**Results**:
  * the p-value associated with ab_page is 0.19  
  * since the p-values is small we can reject the null hypothesis here which is the opposite to the one in **Hypothesis Test part**
