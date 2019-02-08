# mouse_dynamics_balabit_chaoshen_dfl

User Verification Based on Mouse Dynamics: a Comparison of Public Data Sets
## Context 
Code repository of paper submitted for SACI 2019, Informatics section.
## Used data sets

* [Balabit] (https://github.com/balabit/Mouse-Dynamics-Challenge) - Mouse Dynamics Challenge (10 users)
* [Chaoshen] (https://figshare.com/articles/Mouse_Behavior_Data_for_Continuous_Authentication/5619328) - Chao Shen's data set (28 users)
* [DFL] (https://ms.sapientia.ro/~manyi/DFL.html) - Our DFL data set (21 users)



## Evaluation
Performances are reported using ROC Area Under Curve (AUC).
### Evaluation protocol

A binary classifier (Random forest. 100 trees) was trained for each users using positive and negative data. In the case of positive data, the chronologically first 2/3 of the data was used for training and the remaining 1/3 of the data was used for evaluation. Negative data were selected from the other users (#positive samples = #negative samples).

* First Scenario: user identity predictions using a single mouse action
* Second Scenario: user identity predictions using a sequence of consecutive actions (sliding window, overlap between consecutive windows was 90%).

Software: Python 3, scikit-learn 0.19.1

## Usage

Evaluate the Balabit data set using the second scenario and 10 actions for user identity predictions:

Pleese set the followings in util/settings.py

* CURRENT_DATASET = DATASET.BALABIT
* DATASET_USAGE = DATASET_AMOUNT.FIRST1000
* NUM_TRAINING_SAMPLES = 1000
* NUM_ACTIONS = 10

Run evaluation

* python main.py
