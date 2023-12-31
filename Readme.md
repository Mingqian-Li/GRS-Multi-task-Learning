## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Setup](#setup)
* [Performance](#performance)
## General info
This project mainly focuses on building multi-task learning framework for developing Genetic Risk Score (GRS) Models of T1D. Given necessary features, ones can identify the fairness difference and use different regularization methods to alleviate the unfaireness.
	
## Technologies
Project is created with:
* scipy version: 1.7.3
* sklearn
* Python 3.7.1
* mutar 0.0.1 
	
## Setup
To run this project, install it locally using mutar:

```
$ cd ../experiments
$ pip install -U mutar
```
The original mutar package is from https://github.com/hichamjanati/mutar. We modified the package and added extra logistic regression model to make it has better performance on classification problem.

The modified mutar allows us to train multi-task logistic regression model with L1 regularization/Group regularization/Sparse Group regularization. 

# Performance
For the current version, we have developed multi-task logistic regression model and tested them on survey dataset refer to https://doi.org/10.1002/widm.1452. The loading model baseline is based on https://github.com/tailequy/fairness_dataset. If ones want to directly use orginal setting, please check if features are correctly selected.
## Survey datasets
* Fairness performance has been tested based on logistic regression models with different regularization, L1, Group and Sparse Group.
* Red means the fairness performance is better, but result may not be reliable because of small training dataset sample numbers. Yellow means the fairness performance is better, also reliable. The detail results can be found in ~./experiments/Group regression.ipynb.

* All the regularization terms are set to 0.1 for all dataset, which is not optimium for now. 

* For some datasets, normalization has improved the accuracy performance.

* Models are based on paper https://www.cs.utexas.edu/~pradeepr/paperz/mtdm_nips.pdf. Need to pay attention to several conditions. This dirty model may not be able to work under some circumstances, such as insufficient sample numbers or oversize feature numbers.
* Unfairness issue has been identified on CSR based on TEDDY MP68 dataset.

![image](https://user-images.githubusercontent.com/70342781/219811476-9052d519-c557-4eb2-b34a-628620ea7af7.png)

## Diabetes
The diabetes folder mainly focuses on how to improve the diabetes prediction accuracy for the minority race. 

The given features are GRS, family background and AB test results. We train a cox model based on the given data and use it to compute to compute CRS. With this CRS, we can tell who might be the potential patient.

The precondition is that we consider there is no fairness issue on GRS. GRS is just a given value for each individual. 

After we train the cox model based on all data points, we have identified the unfairness for difference races. Race 2 testing performance is the best, since Race 2 is the majority. The rest races were all put into the minority group, because many small races don't have enough data to compute a ROC curve. The accuracy is much worse for a 3 years diabetes prediction. Performance for prediction in 8 years is more stable.
![CRS_minority](https://github.com/Mingqian-Li/Fairness-annual-review/assets/70342781/4d662194-d346-4c40-a05c-b9ef7d4dd2fe)
![CRS_majority](https://github.com/Mingqian-Li/Fairness-annual-review/assets/70342781/b24462b0-dd3e-4796-80bc-679314de2cff)


