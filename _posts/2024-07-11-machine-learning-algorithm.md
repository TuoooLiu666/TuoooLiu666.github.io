---
layout: post
title: Machine Learning Algorithm
date: 2024-07-12 11:12:00-0400
description: ML algorithm
categories: MachineLearning
tags: MachineLearning
---

- statistical perspective: $$Y=f(X)+\epsilon$$ 
  - model=algorithm(data)
- computer science perspective:
  - output = program(input)
  - prediction = program(instance)

- algorithms that learn a mapping from input to output
  - ML algorithms are techniques for estimating target function f to predict the output (Y) given input variables (X)
  - different ML algorithms make different assumptions about the shape and structure of the target function and how best to optimize a representation to approximate it, which makes fitting and comparing a suite of algorithms necessary.

## Algorithms & Models

- linear models
  - linear regression
  - generalized linear models (GLMs)
  - logistic regression (LR)
  - Naive Bayes classifers (NB)
  - linear discriminant analysis (LDA)
- tree-based methods
  - decision trees
  - random forest
  - gradient boosting
- instance-based methods
  - kNN
  - SVM
- neural networks
  - feedforward neural networks (NN)
  - convolutional neural networks (CNN)
  - recurrent neural networks (RNN)
  
### Binary classification


- input vector $$x \in \mathbb{R}^d$$
- output $$ y \in \{0,1\} $$
- the goal is to construct a function \begin{equation}f: \mathcal{X} \rightarrow \{0,1\} \end{equation} 

using 0-1 loss, the risk of a classifier $$ f: \mathcal{X} \rightarrow Y $$ is given by:

\begin{equation}
R(f)=EPE(f)E_{X,Y} \mathcal{1}(Y \ne f(X)) = P(Y \ne f(X))
\end{equation}

the Bayes rule $$f^{*}$$ relies on the posterior probabilities

\begin{equation}
f^{*}=\arg \min R(f)=\begin{cases} 1 \quad if \quad P(Y=1|X=x) > P(Y=0|X=x) \\
0 \quad if \quad P(Y=1|X=x) <> P(Y=0|X=x)
\end{cases}
\end{equation}

the Bayes risk is defined as the risk of $$f^{*}$$, which has the smallest possible risk among all possible classifiers

\begin{equation}
R(f^{*})=P(Y \ne f^{*}(X))=P(Y=1)P(Y=0|X=x)+P(Y=0)P(Y=1|X=x)
\end{equation}

#### example: rare disease

define class 1 = "disease", 0 = "disease-free". $$\pi_1=1\%, \pi_0=99\%$$. 

recall the Bayes rule $$f(x)=\mathcal{1}(P(Y=1|X=x) > P(Y=0|X=x))$$

- posterioe class probability P(Y=j|X=x) gives updated probabilities after observing x
- if $$P(Y=1|X=x) > 0.5$$, thenwe randomly assign data to one class.

Example: Assume a certain rare disease occurs among 1% of the
population. There is a test for this disease: 99.5% of the disease
will test positive, and only 0.5% of the disease-free group will test
positive. (We assume the false positive and false negative rate are
both 0.005.) Now a person comes with a positive test result.
What is the prediction rule?

the conditional probability of X given Y is 

$$
P(X=+|Y=1)=0.995, P(X=-|Y=0)=0.005 \\
P(X=+|Y=0)=0.005, P(X=-|Y=0)=0.995
$$

using Bayes' Theorem,

$$
P(Y=1|X=+) = \frac{P(X=+|Y=1)P(Y=1)}{P(X=+)} = \frac{P(X=+|Y=1)P(Y=1)}{P(X=+|Y=1)P(Y=1)+P(X=+|Y=0)P(Y=0)} = \frac{0.995*0.01}{0.995*0.01+0.005*0.99} = 0.668 \\
P(Y=0|X=+) = \frac{P(X=+|Y=0)P(Y=0)}{P(X=+)} = \frac{0.005*0.99}{0.995*0.01+0.005*0.99} = 0.332
$$

Since P(Y = 0|X = +) = 0.332 < 0.668, the Bayes rule assigns a person with the “+” test result to class “disease”.

Similarly, P(Y = 0|X = −) = 0.9999, P(Y = 1|X = −) = 0.0001, so the Bayes rule assigns a person with the “-” test result to class “disease-free”.


#### Unequal cost
the Bayes rule under unequal cost is given by

\begin{equation}
f^{*}(x)=
\begin{cases} 
1 \quad if \quad C(1,0)P(Y=1|X=x) > C(0,1)P(Y=0|X=x) \\
0 \quad if \quad C(1,0)P(Y=1|X=x) < C(0,1)P(Y=0|X=x)
\end{cases}
\end{equation}
### Linear classification methods
two popular linear classifiers

- Linear Discriminant Analysis (LDA)
- Logistic Regression models (LR)
  - both models rely on the linear-odd assumption, indirectly or directly.
  - LDA and LR estimate the coefficients in a different ways.


linear-logit model (LDA and LR): assume that the logit is linear in x:

\begin{equation}
\log \frac{P(Y=1|X=x)}{P(Y=0|X=x)}=w^Tx+b
\end{equation}

posterior probability:

\begin{equation}
P(Y=1|X=x)=\frac{e^{w^Tx+b}}{1+e^{w^Tx+b}}=\frac{1}{1+e^{-w^Tx-b}} \\
P(Y=0|X=x)=\frac{1}{1+e^{w^Tx+b}}
\end{equation}

under equal-cost, the decision boundary is given by $$\{x|w^Tx+b=0\}=\{x|P(Y=1|X=x)=0\}$$.

#### LDA

LDA assumptions 

- each class density is multivariate Guassian: $$X|Y_j \sim N(\mu_j, \sigma_j)$$
- Equal covariance matrices for each class: $$\sigma_j = \sigma$$

under mixture Guassian assumption, the log-odds is expressed as:

\begin{equation}
  \log \frac{P(Y=1|X=x)}{P(Y=0|X=x)}=\log \frac{\pi_1 \phi(x|\mu_1, \Sigma)/m(x)}{\pi_0 \phi(x|\mu_0, \Sigma)/m(x)} \\
  = \log \frac{\pi_1}{\pi_0} + \log \phi(x|\mu_1, \Sigma)- \log \phi(x|\mu_0, \Sigma) \\
  = \log \frac{\pi_1}{\pi_0} - \frac{1}{2}(x-\mu_1)^T\Sigma^{-1}(x-\mu_1) + \frac{1}{2}(x-\mu_0)^T\Sigma^{-1}(x-\mu_0) \\
  = \log \frac{\pi_1}{\pi_0} - \frac{1}{2}(\mu_1+\mu_0)^T\Sigma^{-1}(\mu_1-\mu_0) + x^T\Sigma^{-1}(\mu_1-\mu_0) \\
  \log \frac{\pi_1}{\pi_0} - \frac{1}{2}(\mu_1+\mu_0)^T\beta_1+x^T\beta_1
\end{equation}

under 0-1 loss, the Bayes rule is: assign 1 to x if and only if:

$$
\log \frac{P(Y=1|X=x)}{Y=0|X=x}>0
$$

which is equivalent to: assign 1 to x if and only if:

$$
\bigg [ \log \frac{\pi_1}{\pi_0} - \frac{1}{2}(\mu_1+\mu_0)^T\Sigma^{-1}(\mu_1-\mu_0) \bigg ] + x^T\Sigma^{-1}(\mu_1-\mu_0) > 0.
$$

#### LR

- denote $$\mu=E(Y|X)=P(Y=1|X)$$.
- assuming $$g(\mu)=\log \frac{\mu}{1-\mu}=\beta_0+\beta_1^TX$$.

#### high-dimensional classifiers

- LDA-type 
  - Naive Bayes, Nearest Shrunken Centroid (NSC)
  - sparse LDA, regularized LDA
- penalized logistic regression
- large-margin methods
  - support vector machines (SVM)
- classification tree
  - decision tree
  - random forest
- boosting

### Nonlinear classifier

- KNN
- kernal SVM
- trees, random forests
- ...

#### K-Nearest Neighbor (KNN) classifiers
the degree of freedom is n/k
- k controls the model complexity
  - smaller k: lower bias and higher variance
  - larger k: higher bias and lower varance (reduce effect of noise)
- the best choice of k depends upon the data

- pros
  - geenrally low bias
  - no stringent assumptions about data
  - robust against outliers
  - works well for large n small d
- cons
  - potentially high variance
  - work bad for large d small n
  - accuracy severely degraded by noisy or irrelevant features, or the feature scales are not consistent with their importance
    - Much research effort on selecting or scaling features to improve classification, such as optimize feature scaling.


#### kernal SVM

#### tree-based method


### Ensemble methods

- bagging
- boosting
- stacking

### neural network

#### forward feeding neural network

#### convolutional neural network (CNN)


#### recurrent neural network (RNN)

RNN is a special case of feed-forward NN with a single hidden layer, where the hidden layer is a recurrent layer.RNN is a special case of CNN with a single filter.

- What is the purpose of gated recurrent unit (GRU) in a recurrent neural network (RNN)?

The purpose of a gated recurrent unit (GRU) in a recurrent neural network (RNN) is to address the vanishing gradient problem and capture long-range dependencies in sequential data. 

The vanishing gradient problem occurs when the gradients used to update the weights in an RNN diminish exponentially as they propagate back through time, making it difficult for the network to learn long-term dependencies. The GRU helps mitigate this problem by introducing gating mechanisms that control the flow of information within the network.

The GRU has two main gates: the update gate (Gamma_u) and the reset gate (Gamma_r). The update gate determines how much of the previous memory should be retained and how much of the new input should be incorporated. The reset gate decides how much of the previous memory should be forgotten.

By adaptively updating and resetting the memory cell, the GRU can selectively retain important information and discard irrelevant information, allowing it to capture long-range dependencies more effectively. This makes the GRU a powerful tool for tasks such as natural language processing, speech recognition, and time series analysis.

- How does a gated recurrent unit (GRU) work?

Sure! Let's break down the topic of gated recurrent units (GRUs) in a recurrent neural network (RNN) in simple terms.

Imagine you're reading a sentence and trying to understand its meaning. As you read each word, you need to remember important information from earlier in the sentence to make sense of it. The same goes for a computer trying to process sequential data, like sentences or time series.

The problem is that traditional RNNs struggle to remember long-range connections and can't capture important information from earlier in the sequence. This is where GRUs come in.

GRUs are like memory cells in the RNN. They help the network remember important information from earlier in the sequence and use it to make predictions or understand the data better. They do this by using two gates: the update gate and the reset gate.

The update gate decides how much of the previous memory to keep and how much new information to incorporate. It helps the network decide what's important to remember and what can be forgotten.

The reset gate determines how much of the previous memory to forget. It helps the network reset or update the memory cell based on the current input.

By using these gates, GRUs can selectively retain important information and discard irrelevant information, allowing the network to capture long-range connections and dependencies in the data. This makes GRUs very useful for tasks like understanding language, recognizing speech, and analyzing time series data.

- What is the role of attention mechanism in sequence models?

- Explain the concept of word embeddings in natural language processing.

Word embeddings are a way of representing words as dense vectors in a continuous vector space. They are used in natural language processing (NLP) to capture the semantic and syntactic relationships between words.

Word embeddings are trained on large text corpora and learn to represent words based on their context. For example, the word "king" might be represented as a vector that is close to the vector for "queen" and far from the vector for "car."

- What is the transformer network and how does it improve upon traditional sequence models?

The transformer network is a type of deep learning model that is used for processing sequential data, such as text or time series. It is based on the concept of self-attention, which allows the model to focus on different parts of the input sequence when making predictions.