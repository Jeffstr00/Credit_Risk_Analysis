# Credit_Risk_Analysis:
## Supervised Machine Learning and Credit Risk

## Overview

FastLending, a peer-to-peer lending services company, wants to use machine learning to predict credit risk in an attempt to provide a quicker and more reliable loan experience.  Ultimately, they believe that machine learning will lead to a more accurate identification of good candidates for loans, which will lead to lower default rates.  If true, that would create a win/win/win situation where the fewer people are ruining their lives when they default on loans, good customers can be charged a more fair rate as they won't be subsidizing as many defaulting customers, and the company can become more efficient and make more money.

FastLending's lead data scientist, Jill, has asked for our assistance in setting up a machine learning environment that can (hopefully) accurately predict credit risk.  We are provided with a massive spreadsheet containing over 100,000 rows with 86 columns, so machine learning definitely seems like the right tool for the job.  However, Jill knows that assessing credit risk can be tricky, especially since good loans easily outnumber risky ones.  Therefore, she asks us to use six different machine learning algorithms to assess the data and then evaulate their performances to see whether or not they should be used to predict credit risk.

## Results

Note: for all six algorithms, precision was virtually the same: a near perfect 1.00 score for low risk, but incredibly low (1-7%) grades for high risk loans.  When calculating the precision by dividing total positives by the number of all positives (true + false positives), the huge discrepancy between the number of low and high risk loans in this example lead to this result since the denominator is so huge.  However, in this instance we are more concerned with the sensitivity/recall scores, since our main goal is to correctly identify each high risk loan.

### Oversampling

* RandomOverSampler

![RandomOverSampler](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/RandomOverSampling.png)

With random oversampling, the algorithm attempts to make up for the gross imbalance between the two groups by adding instances of the minority class to the training set until the two are balanced.  In this case, the model had an unimpressive balanced accuracy score of 64%, with a sensitivity rate of 65%.

* SMOTE

![SMOTE](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/SMOTE.png)

SMOTE oversampling also tries to deal with unbalanced datasets by increasing the size of the minority group.  However, instead of randomly making these selections, SMOTE does it by interpolating its instances, or creating values based on its closest neighbors.  However, that did not make much of a difference here, as this had a near identical balanced accuracy score of 63% and 64% recall.

### Undersampling

* RandomUnderSampler

![RandomUnderSampling](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/RandomUnderSampling.png)

Random under sampling is just like random over sampling, but in reverse.  Instead, instances from the majority class are removed at random until the sizes of the two populations match.  In this case, results were not an improvement, as the balanced accuracy score fell to 59% with a 57% sensitivity score.

### Combination

* SMOTEENN

![SMOTEENN](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/SMOTEENN.png)

SMOTEENN is an combined over/under sampling algorithm with two steps.  It first oversamples the minority class with SMOTE, then it undersamples the derived data by dropping data points whose two closest neighbors belong to seperate classes.  In this case, it improved the recall rate of high risk loans which rose to 71% at the expense of low_risk, which dropped to 59%.  Overall, its balanced accuracy score of 65% was the highest so far, albeit not by a large margin.

### Bias Reduction

* BalancedRandomForestClassifier

![BalancedRandomForest](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/BalancedRandomForest.png)

BalancedRandomForestClassifier is a bias reduction algorithm that creates many small and simple decision trees.  While these trees are considered weak learners by themselves, when put together, many small decision trees can have incremental positive impacts that ultimately combine to form a strong learner.  Here, those incremental improvements did add up as we saw our highest balanced accuracy score so far at 79%.  While the sensitivity rate for high risk loans was in line with much of the others at 67%, that of the low risk loans was much higher at 91%.

* EasyEnsembleClassifier

![EasyEnsemble](https://github.com/Jeffstr00/Credit_Risk_Analysis/blob/main/Resources/EasyEnsemble.png)

Like RandomForest, EasyEnsemble is another bias reduction algorithm.  However, while RandomForest is, well, random...EasyEnsemble creates balanced samples by using the entirety of the minority class and then picking from the majority class to match it.  Here, that certainly paid dividends.  We had easily our highest balanced accuracy score of 93%.  Additionally, the recall rates for both high (91%) and low (94%) risk earned the highest marks.

## Analysis

In this case, it is abundantly clear which algorithm(s) produced the best results.  With all of the over and under sampling methods had balanced accuracy scores in (or just below) the 60's, both bias reduction methods were higher.  While BalancedRandomForest was a good 10 points higher at 79%, even that was clearly outclassed by the EasyEnsemble classifier and its 93% score.  While the huge low:high risk ratio led to every method having lopsided precision scores, even then, the bias reduction methods (especially EasyEnsemble) showed the best high risk precision.  When it came to sensitivity, which we are more concerned with, we saw the same thing.  Both random and under sampling produces scores in the 60's ballpark, SMOTEENN's combination method saw an improvement for high risk loans to 71% at the expense of that of low risk loans which fell to 59%, but the two bias reduction methods beat them all.  While BalancedRandomForest's high risk recall rate was similarly at 67%, its low risk score jumped all the way up to 91%.  However, EasyEnsemble reigned supreme on all accounts with its best across the boards scores of 91 and 94% for high and low risk respectively.

Ultimately, there is no hard and fast rule deciding whether or not a particular algorithm should be used given its scores.  Virtually no test will be perfect, which means that some instances will inevitably be misclassified.  Each time this happens, the company will end up losing money.  However, with good tests, this should be minimized, and this was clearly the case with EasyEnsemble's bias reduction classifier.  It had the highest scores across the board, so it leaves no doubt as to which one should be used.  While the company ultimately has to decide whether or not those rates are acceptable, with a accuracy score of 93%, it seems rather unlikely EasyEnsemble's classifier didn't perform up to standards.