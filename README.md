# User Verification Based on Mouse Dynamics: a Comparison of Public Data Sets
### mouse_dynamics_balabit_chaoshen_dfl
## Context 
Code repository of paper:
13th International Symposium on Applied Computational Intelligence and Informatics (SACI), IEEE  pp. 143-147, 2019.

## Used data sets

* [Balabit](https://github.com/balabit/Mouse-Dynamics-Challenge) - Mouse Dynamics Challenge (10 users)
* [Chaoshen](https://figshare.com/articles/Mouse_Behavior_Data_for_Continuous_Authentication/5619328) - Chao Shen's data set (28 users)
* [DFL](https://ms.sapientia.ro/~manyi/DFL.html) - Our DFL data set (21 users)



## Evaluation

### Feature extraction

Raw data were segmented into mouse actions then 39 features were extracted from each mouse action. For details see
* Our paper [Intrusion Detection Using Mouse Dynamics](https://arxiv.org/abs/1810.04668)
* [Resources](https://ms.sapientia.ro/~manyi/mousedynamics/)


### Performance measures

Performances are reported using ROC Area Under Curve (AUC).

### Evaluation protocol

A binary classifier (Random forest, 100 trees) was trained for each users using positive and negative data. In the case of positive data, the chronologically first 2/3 of the data was used for training and the remaining 1/3 of the data was used for evaluation. Negative data were selected from the other users (#positive samples = #negative samples).

* First Scenario: user identity predictions using a single mouse action
* Second Scenario: user identity predictions using a sequence of consecutive actions (sliding window, overlap between consecutive windows was 90%).

Software: Python 3, scikit-learn 0.19.1

## Usage

Example: Evaluate the Balabit data set using the first 500 actions/user and 10 actions for user identity predictions.

1. Please set the followings in util/settings.py

* CURRENT_DATASET = DATASET.BALABIT
* DATASET_USAGE = DATASET_AMOUNT.FIRST1000
* NUM_TRAINING_SAMPLES = 500
* NUM_ACTIONS = 10

2. Run evaluation

* python main.py
