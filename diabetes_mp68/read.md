This folder mainly focuses on how to improve the diabetes prediction accuracy for the minority race. 

The given features are GRS, family background and AB test results. We train a cox model based on the given data and use it to compute to compute CRS. With this CRS, we can tell who might be the potential patient.

The precondition is that we consider there is no fairness issue on GRS. GRS is just a given value for each individual. 

After we train the cox model based on all data points, we have identified the unfairness for difference races. Race 2 testing result has similar performance comparing is the best, since Race 2 is the majority. The rest races were all put into the minority group, because many small races don't have enough data to compute a ROC curve. The accuracy is much worse for a 3 years diabetes prediction. Performance for prediction in 8 years is more stable.


