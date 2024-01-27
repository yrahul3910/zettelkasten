---
title: Flat minima and generalization
id: 2024012634563
tags:
  - theoretical-ml
---
The idea of flat minima was first studied by [@hochreiterSIMPLIFYINGNEURALNETS]. In particular, they define "flat minima" as large connected regions where the weights are $\epsilon-$optimal. [@hochreiterFlatMinima1997] intuit that because sharper minima require higher precision, flatter minima require less bits to describe. They use this intuition to show that flat minima correspond to minimizing the number of bits required to describe the weights of a neural network. This notion of minimum description length (MDL) [@rissanenUniversalPriorIntegers1983, @grunwaldMinimumDescriptionLength2007] was also exploited early on by [@hintonKeepingNeuralNetworks]. Flat minima were revisited by [@chaudhariEntropysgdBiasingGradient2019], who noted that minima with low generalization error have a large proportion of their eigenvalues close to zero. They then construct a modified Gibbs distribution corresponding to an energy landscape $f$, and minimize the negative local entropy of this modified distribution, and approximate the gradient via stochastic gradient Langevin dynamics (SGLD) [@wellingBayesianLearningStochastic]. However, their assumptions were, admittedly unrealistic. [@keskarLargeBatchTrainingDeep2017] show that when using large batch sizes, optimizers converge to sharp minima, which are characterized by many large positive eigenvalues of the Hessian. Further, they define the notion of sharpness as a generalization measure as the robustness to adversarial perturbations in the parameter space:

$$
\zeta(\boldsymbol w; \epsilon) = \frac{\max\limits_{\lvert \boldsymbol v \rvert \leq \epsilon(\lvert \boldsymbol w \rvert + 1)} f(\boldsymbol w + \boldsymbol v) - f(\boldsymbol w)}{1 + f(\boldsymbol w)}
$$

and compute this using 10 iterations of L-BFGS-B [@byrdtLIMITEDMEMORYALGORITHM] with $\epsilon = \{ 10^{-3}, 5 \cdot 10^{-4} \}$. In particular, the above is closely related to the largest eigenvalue of $\nabla^2 f(\boldsymbol w)$. This notion of sharpness was also endorsed by [@jiangFantasticGeneralizationMeasures2019], who performed a large-scale study of many complexity measures on two datasets, with 2,187 convolutional networks. In particular, they endorse the following metrics for generalization: (i) variance of gradients (ii) squared ratio of magnitude of parameters to magnitude of perturbation, à la [@keskarLargeBatchTrainingDeep2017] (iii) path norm [@neyshaburExploringGeneralizationDeep] (iv) VC-dimension (inversely correlated).

A line of work in physics [@baldassiSubdominantDenseClusters2015, @baldassiUnreasonableEffectivenessLearning2016] showed that in the discrete weight scenario (a much more difficult problem), isolated minima were rare, but there existed accessible, dense regions of subdominant minima, and that these were robust to perturbations and generalized better. These authors devised algorithms explicitly designed to search for nonisolated minima. In the continuous weight space, nonisolated minima correspond to flat minima. [@dziugaiteComputingNonvacuousGeneralization2017] obtain nonvacuous generalization bounds for deep overparameterized neural networks using the PAC-Bayes framework [@mcallesterPACBayesianModelAveraging1999]. [@neyshaburSearchRealInductive2015] showed that increasing the number of hidden units (which in turn, increases the number of trainable parameters) can lead to a decrease in generalization error with the same training error. [@neyshaburExploringGeneralizationDeep] showed that sharpness as computed by the above is not sufficient to capture the generalization behavior (but noting that "combined with the norm, sharpness does seem to provide a capacity measure"), and advocate for expected sharpness in the PAC-Bayesian framework, similar to [@dziugaiteComputingNonvacuousGeneralization2017]. They show that plots of expected sharpness versus KL divergence in PAC-Bayes bounds for varying dataset sizes capture generalization well. [@liVisualizingLossLandscape2017] showed that the sharpness of the loss surface correlates well with the generalization error. In their seminal paper, [@jastrzebskiThreeFactorsInfluencing2018] showed that SGD is a Euler-Maruyama discretization of a stochastic differential equation whose dynamics are influenced by the ratio of learning rate to batch size (which they call "stochastic noise"), and that SGD finds wider minima with higher stochastic noise levels than sharper minima. [@wuImplicitRegularizationDynamical2023] study the flat minima hypothesis through the lens of dynamical stability, and show that SGD will escape from overly sharp (measured by the Frobenius norm of the Hessian), low-loss areas exponentially fast. We note that they use the associate empirical Fisher matrix (AEFM) as an approximation for the Hessian, which holds for low empirical risk (and converges to the Hessian, see [@kunstnerLimitationsEmpiricalFisher]).

In search of flatter loss surfaces, [@Seong2016] propose the use of non-monotonic learning rate schedules. They advocate for large learning rates, which enable the optimization algorithm to escape sharp minima, and descend into flatter minima. The seminal works of [@dauphinIdentifyingAttackingSaddle] and [@choromanskaLossSurfacesMultilayer] showed both theoretically and empirically that local minima are more likely to be located close to the global minimum. In particular, [@dauphinIdentifyingAttackingSaddle] showed using the perspectives of random matrix theory (via the eigenvalue distribution of Gaussian random matrices [@wignerDistributionRootsCertain1958]), statistical physics (via the analysis of critical points in Gaussian fields by [@brayStatisticsCriticalPoints2007]), and neural network theory [@saxeExactSolutionsNonlinear2014].

Most recently, [@wenSharpnessMinimizationAlgorithms] showed that sharpness is neither necessary, nor sufficient for generalization, by studying some simple architectures, showing that generalization depends on the data distribution as well as the architecture; for example, merely adding a bias to a 2-layer MLP makes generalization impossible for the XOR dataset.
	
Of course, it is not possible to discuss generalization in deep learning without discussing the results of [@zhangUnderstandingDeepLearning2021], who showed that deep learners can fit with zero training error on random labels using an architecture that generalizes well when fit to the correct labels. [@bartlettNearlytightVCdimensionPseudodimension2019] and [@harveyNearlytightVCdimensionBounds2017] found that the VC-dimension for deep ReLU networks is $\mathcal{O}(WL \log W)$ and $\Theta(WU)$ respectively, where $W$ is the number of parameters, $L$ the number of layers, and $U$ the number of units. [@hardtTrainFasterGeneralize2016] show that stochastic gradient methods are uniformly stable\footnote{An algorithm $A$ is $\epsilon-$uniformly stable if $\forall S, S^\prime \in Z$ for some space $Z$, such that the datasets $S$ and $S^\prime$ differ by at most one example, $\sup\limits_z \mathbb{E}_A [f(A(S); z) - f(A(S^\prime); z)] \leq \epsilon$}, which implies generalization *in expectation*.