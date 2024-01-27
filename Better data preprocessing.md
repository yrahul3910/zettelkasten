---
title: Better data preprocessing
date: 2023-04-21
id: 20230421030821
author: Rahul Yedida
---
#applied-ai #preprocessing #tse #software-analytics #static-code-warnings

# Better data preprocessing

[@yedidaHowFindActionable2023] showed that learning problems can be decomposed into multiple engineering decisions: instance engineering, boundary engineering, label engineering, and parameter engineering.

* **Instance engineering** refers to manipulating instances in the training set to learn more optimal decision boundaries and overcome issues such as class imbalance. This paper used SMOTE [@chawla2002smote].
* **Label engineering** refers to techniques that overcome issues in the labels of the training data. This particular paper was motivated by a prior paper that noted that a lot of the data was mislabeled. This paper did this by "losing" $m - \sqrt{m}$ labels and then building a kd-tree for the remaining $\sqrt{m}$ labels. For each of the "lost" labels, the kd-tree is queried for the nearest $\sqrt[4]{m}$ samples, and the mode of those is taken.
* **Boundary engineering** refers to techniques that aim to manipulate the learner's decision boundary. For example, fuzzy sampling [@yedidaValueOversamplingDeep2021] adds samples around each minority class sample, which pushes the decision boundary away.
* **Parameter engineering** refers to hyper-parameter optimization. This paper used DODGE [@agrawal2019dodge].

A combination of all the techniques used above yielded state-of-the-art performance for finding actionable static code warnings. It was shown that these techniques together improve the $\beta-$smoothness (see [[beta-smoothness]]) of the loss function.