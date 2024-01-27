---
title: Hyper-parameter optimization
id: 2024012623044
tags:
  - hpo
---

There is significant prior work in hyper-parameter optimization [@agrawal2019dodge, @cowen2022hebo, @li2017hyperband, @bergstra2011algorithms, @bergstra2012random, @falkner2018bohb, @eriksson2019scalable, @ansel:pact:2014]. Indeed, as learning systems become more intricate, it is crucial that we eke out the most performance. However, this is a non-trivial problem, as evidenced by the long line of research in this direction.

The simplest form of hyper-parameter search is random search, which tries $n$ randomly chosen hyper-parameter configurations. Opentuner [@ansel:pact:2014] is a multi-armed bandit meta-technique with a sliding window that incorporates an exploration/exploitation trade-off based on the number of times a specific technique is used. It combines DE, a greedy bandit mutation technique, and hill-climbing methods. However, Bayesian Optimization is an extremely popular alternative.

However, Bayesian Optimization (BO) has emerged as the most popular technique for HPO. [@bergstraAlgorithmsHyperParameterOptimization] propose the Tree of Parzen Estimators (TPE) algorithm. Rather than model $p(y|x)$, TPE models $p(x|y)$ as

$$
p(x|y) = \begin{cases}
    l(x) &  y < y^* \\
    g(x) &  y \geq y^*
    \end{cases}
$$

where $y^*$ is chosen so that $p(y < y^*) = \gamma$ for some quantile $\gamma$. The functions $l(x)$ and $g(x)$ are kernel density estimates. TPE optimizes the EI, which they show is equivalent to maximizing $l(x) / g(x)$.

[@snoek2012practical] use Gaussian Process (GP) models as the surrogate function in Bayesian optimization. They use Expected Improvement (EI) as the acquisition function. Similarly, [@hernandez2014predictive] use predictive entropy search (PES) as the acquisition function. [@swersky2014freeze] exploit iterative training procedures in their Bayesian optimization framework, which they call freeze-thaw Bayesian optimization. [@snoek2015scalable] use neural networks for modeling distributions over functions that yields an approach that scales linearly over data size (rather than cubically as in GP-based Bayesian optimization).

BOHB [@falkner2018bohb] combines the BO-based TPE with HyperBand [@li2017hyperband], replacing the initial random configurations with a model-based search. Notably, BOHB uses a single multi-dimensional KDE instead of hierarchical single-dimensional KDEs used by TPE.

The authors of HEBO [@cowen2022hebo] note that (i) even simple HPO problems can be non-stationary and heteroscedastic (ii) different acquisition functions can conflict. To tackle the former, they use the Box-Cox [@boxAnalysisTransformations1964] and Yeo-Johnson [@yeoNewFamilyPower2000] output transformations and the Kumaraswamy [@kumaraswamyGeneralizedProbabilityDensity1980] input transformation. It also uses NSGA-II to optimize a multi-objective acquisition function.

TuRBO [@douTurBOCostefficientConfigurationbased2023] assumes the hyper-parameter to performance mapping is Lipschitz, and generates pseudo-points to improve convergence of vanilla BO. It also uses an ensemble of learners to predict performance, and if the prediction is poor, uses it to instead update the GP model.

Refer to [@feurer2019hyperparameter] and [@bischlHyperparameterOptimizationFoundations2023] for recent reviews on hyper-parameter optimization techniques.