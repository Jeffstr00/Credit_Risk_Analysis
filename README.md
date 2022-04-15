# Credit_Risk_Analysis:
## Supervised Machine Learning and Credit Risk

## Overview

FastLending, a peer-to-peer lending services company, wants to use machine learning to predict credit risk in an attempt to provide a quicker and more reliable loan experience.  Ultimately, they believe that machine learning will lead to a more accurate identification of good candidates for loans, which will lead to lower default rates.  If true, that would create a win/win/win situation where the fewer people are ruining their lives when they default on loans, good customers can be charged a more fair rate as they won't be subsidizing as many defaulting customers, and the company can become more efficient and make more money.

FastLending's lead data scientist, Jill, has asked for our assistance in setting up a machine learning environment that can (hopefully) accurately predict credit risk.  We are provided with a massive spreadsheet containing over 100,000 rows with 86 columns, so machine learning definitely seems like the right tool for the job.  However, Jill knows that assessing credit risk can be tricky, especially since good loans easily outnumber risky ones.  Therefore, she asks us to use six different machine learning algorithms to assess the data and then evaulate their performances to see whether or not they should be used to predict credit risk.

## Results

### Oversampling

* RandomOverSampler

![RandomOverSampler](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/RandomOverSampling.png)

blah

* SMOTE

![SMOTE](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/SMOTE.png)

blah

### Undersampling

* ClusterCentroids

![RandomUnderSampling](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/RandomUnderSampling.png)

blah

### Combination

* SMOTEENN

![SMOTEENN](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/SMOTEENN.png)

blah

### Bias Reduction

* BalancedRandomForestClassifier

![BalancedRandomForest](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/BalancedRandomForest.png)

blah

* EasyEnsembleClassifier

![EasyEnsemble](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/EasyEnsemble.png)

blah

## Analysis

There is a summary of the results (2 pt)
There is a recommendation on which model to use, or there is no recommendation with a justification (3 pt)