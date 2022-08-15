# Bias-Variance Tradeoff 

The bias–variance tradeoff is a central problem in supervised learning. Ideally, one wants to choose a model that both accurately captures the regularities in its training data, but also generalizes well to unseen data. Unfortunately, it is typically impossible to do both simultaneously. High-variance learning methods may be able to represent their training set well but are at risk of overfitting to noisy or unrepresentative training data. In contrast, algorithms with high bias typically produce simpler models that may fail to capture important regularities (i.e. underfit) in the data.

So let’s start with the basics and see how they make difference to our machine learning Models.

## :question: What is bias?

Bias is the difference between the average prediction of our model and the correct value which we are trying to predict. Model with high bias pays very little attention to the training data and oversimplifies the model. It always leads to high error on training and test data. High bias can cause an algorithm to miss the relevant relations between features and target outputs (**underfitting**)

## :question: What is variance?

Variance is the variability of model prediction for a given data point or a value which tells us spread of our data. Model with high variance pays a lot of attention to training data and does not generalize on the data which it hasn’t seen before. As a result, such models perform very well on training data but has high error rates on test data(**overfitting**).

## :label: Bias–variance decomposition of mean squared error

Suppose that we have a training set consisting of a set of points $x_{1}, \dots, x_{n}$ and real values $y_{i}$ associated with each point $x_{i}$. We assume that there is a function with noise ${y=f(x)+\varepsilon}$, where the noise, $\varepsilon$, has zero mean and variance $\sigma ^{2}$.

We want to find a function ${\displaystyle {\hat {f}}(x; D)}$, that approximates the true function $f(x)$ as well as possible, by means of some learning algorithm based on a training dataset (sample) ${\displaystyle D=\{(x_{1}, y_{1})\dots, (x_{n}, y_{n})\}}$. We make "as well as possible" precise by measuring the mean squared error between ${\displaystyle {\hat {f}}(x; D)}$: we want ${\displaystyle (y-{\hat {f}}(x; D))^{2}}$ to be minimal, both for $x_{1}, \dots, x_{n}$ and for points outside of our sample. Of course, we cannot hope to do so perfectly, since the $y_{i}$ contain noise $\varepsilon$; this means we must be prepared to accept an irreducible error in any function we come up with.

Finding an ${\hat {f}}$ that generalizes to points outside of the training set can be done with any of the countless algorithms used for supervised learning. It turns out that whichever function ${\hat {f}}$ we select, we can decompose its expected error on an unseen sample $x$ as follows:

$${\displaystyle \operatorname {E}_{D, \varepsilon}{\Big[}{\big (}y-{\hat {f}}(x; D){\big)}^{2}{\Big ]}={\Big(}\operatorname {Bias} _{D}{\big[}{\hat {f}}(x; D){\big]}{\Big)}^{2}+\operatorname {Var} _{D}{\big[}{\hat {f}}(x; D){\big]}+\sigma ^{2}}$$

where

$${\displaystyle \operatorname{Bias}_{D}{\big [}{\hat {f}}(x; D){\big ]}=\operatorname {E} _{D}{\big [}{\hat {f}}(x; D){\big ]}-f(x)}$$

and

$$\operatorname{Var}_D\big[\hat{f}(x; D)\big] = \operatorname{E}_D[\big(\operatorname{E}_D[\hat{f}(x; D)] - \hat{f}(x; D)\big)^2].$$

The expectation ranges over different choices of the training set $D=\{(x_1, y_1) \dots, (x_n, y_n)\}$, all sampled from the same joint distribution $P(x, y)$ which can for example be done via Bootstrapping (statistics]. 
The three terms represent:

* the square of the ''bias'' of the learning method, which can be thought of as the error caused by the simplifying assumptions built into the method. E.g., when approximating a non-linear function $f(x)$ using a learning method for linear models, there will be error in the estimates $\hat{f}(x)$ due to this assumption; 
* the ''variance'' of the learning method, or, intuitively, how much the learning method $\hat{f}(x)$ will move around its mean; 
* the irreducible error $\sigma^2$. 

Since all three terms are non-negative, the irreducible error forms a lower bound on the expected error on unseen samples.

The more complex the model $\hat{f}(x)$ is, the more data points it will capture, and the lower the bias will be. However, complexity will make the model "move" more to capture the data points, and hence its variance will be larger.

### :calling:  Derivation

The derivation of the bias–variance decomposition for squared error proceeds as follows. For notational convenience, we abbreviate ${\displaystyle {\hat {f}}={\hat {f}}(x; D)}$ and we drop the $D$ subscript on our expectation operators. First, recall that, by definition, for any random variable $X$, we have

$${\displaystyle \operatorname {Var} [X]=\operatorname {E} [X^{2}]-\operatorname {E} [X]^{2}.}$$

Rearranging, we get:

$${\displaystyle \operatorname {E} [X^{2}]=\operatorname {Var} [X]+\operatorname {E} [X]^{2}.}$$

Since $f$ is deterministic, i.e. independent of $D$, ${\displaystyle \operatorname {E} [f]=f.}$

Thus, given ${\displaystyle y=f+\varepsilon}$ and ${\displaystyle \operatorname {E} [\varepsilon ]=0}$ (because $\varepsilon$ is noise), implies ${\displaystyle \operatorname {E} [y]=\operatorname {E} [f+\varepsilon ]=\operatorname {E} [f]=f.}$

Also, since ${\displaystyle \operatorname {Var} [\varepsilon ]=\sigma ^{2},}$

$${\displaystyle \operatorname {Var} [y]=\operatorname {E} [(y-\operatorname {E} [y])^{2}]=\operatorname {E} [(y-f)^{2}]=\operatorname {E} [(f+\varepsilon -f)^{2}]=\operatorname {E} [\varepsilon ^{2}]=\operatorname {Var} [\varepsilon ]+\operatorname {E} [\varepsilon ]^{2}=\sigma ^{2}+0^{2}=\sigma ^{2}.}$$

Thus, since $\varepsilon$ and ${\hat {f}}$ are independent, we can write

$$\begin{align} MSE =
\operatorname{E}\big[(y - \hat{f})^2\big]
 & = \operatorname{E}\big[(f+\varepsilon  - \hat{f} )^2\big] \\[5pt]
 & = \operatorname{E}\big[(f+\varepsilon  - \hat{f} +\operatorname{E}[\hat{f}]-\operatorname{E}[\hat{f}])^2\big] \\[5pt]
 & = \operatorname{E}\big[(f-\operatorname{E}[\hat{f}])^2\big]+\operatorname{E}[\varepsilon^2]+\operatorname{E}\big[(\operatorname{E}[\hat{f}]- \hat{f})^2\big] 
+2\operatorname{E}\big[(f-\operatorname{E}[\hat{f}])\varepsilon\big]
+2\operatorname{E}\big[\varepsilon(\operatorname{E}[\hat{f}]- \hat{f})\big]
+2\operatorname{E}\big[(\operatorname{E}[\hat{f}]- \hat{f})(f-\operatorname{E}[\hat{f}])\big] \\[5pt]
 & = (f-\operatorname{E}[\hat{f}])^2+\operatorname{E}[\varepsilon^2]+\operatorname{E}\big[(\operatorname{E}[\hat{f}]- \hat{f})^2\big] 
+2(f-\operatorname{E}[\hat{f}])\operatorname{E}[\varepsilon]
+2\operatorname{E}[\varepsilon]\operatorname{E}\big[\operatorname{E}[\hat{f}]- \hat{f}\big]
+2\operatorname{E}\big[\operatorname{E}[\hat{f}]- \hat{f}\big](f-\operatorname{E}[\hat{f}]) \\[5pt]
 & = (f-\operatorname{E}[\hat{f}])^2+\operatorname{E}[\varepsilon^2]+\operatorname{E}\big[(\operatorname{E}[\hat{f}]- \hat{f})^2\big]\\[5pt]
 & = (f-\operatorname{E}[\hat{f}])^2+\operatorname{Var}[\varepsilon]+\operatorname{Var}\big[\hat{f}\big]\\[5pt]
 & = \operatorname{Bias}[\hat{f}]^2+\operatorname{Var}[\varepsilon]+\operatorname{Var}\big[\hat{f}\big]\\[5pt]
 & = \operatorname{Bias}[\hat{f}]^2+\sigma^2+\operatorname{Var}\big[\hat{f}\big].
\end{align}$$

Finally, MSE loss function (or negative log-likelihood) is obtained by taking the expectation value over ${\displaystyle x\sim P}$ :

$${\displaystyle {\text{MSE}}=\operatorname {E} _{x}{\bigg \{}\operatorname {Bias} _{D}[{\hat {f}}(x; D)]^{2}+\operatorname {Var} _{D}{\big [}{\hat {f}}(x; D){\big ]}{\bigg \}}+\sigma ^{2}.}$$

!!! Info Reference

    - :link: [Understanding the Bias-Variance Tradeoff](https://towardsdatascience.com/understanding-the-bias-variance-tradeoff-165e6942b229)
    - :link: [Bias–variance tradeoff](https://en.wikipedia.org/wiki/Bias–variance_tradeoff)
