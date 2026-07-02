## (HMM , MLE , Bayesian Theorem Sums from YT , will add links if i watch any)
## Module 3: Parameter Estimation Methods

### 1. Introduction to Parameters

A parameter is a characteristic or value that defines the behavior or properties of a population or probability distribution. It represents an unknown quantity that we seek to estimate or infer based on observed data. Common examples include the population mean, variance, and success probability.

### 2. Maximum Likelihood Estimation (MLE)

Maximum Likelihood Estimation is a statistical method used to estimate the parameters of a probability distribution or statistical model.

- **Purpose:** It seeks to find the parameter values that maximize the likelihood of observing the given training data.
    
- **When to Use (PYQ):** MLE is used when we want a single, best-possible deterministic estimate of parameters without requiring any prior knowledge about the data distribution.
    
- **The Likelihood Function:** Represents the probability of observing the given data for different values of the parameters. For a dataset $D$ with $n$ independent samples, the likelihood is: $p(D|\theta) = \prod_{k=1}^{n} P(X_k|\theta)$.
    
- **Log-Likelihood:** To simplify calculations (converting products to sums), the natural logarithm is taken. The log-likelihood function $l(\theta) = \sum_{k=1}^{n} \ln p(X_k|\theta)$ is differentiated with respect to the parameter and set to zero ($\nabla_{\theta}l = 0$) to find the maximum likelihood estimate.
    

### 3. Bayesian Parameter Estimation (BPE)

Bayesian estimation involves using Bayes' theorem to update prior beliefs or knowledge about the parameters of interest with new evidence provided by the observed data.

- **Formula:** The posterior distribution of the parameters $\theta$ given the data $D$ is $P(\theta|D) = \frac{P(D|\theta)P(\theta)}{P(D)}$.
    
- $P(\theta)$ represents the prior distribution (initial beliefs before observing data).
    
- $P(D|\theta)$ is the likelihood function.
    

### 4. MLE vs. Bayesian Parameter Estimation (PYQ)

The fundamental difference between these two approaches lies in their assumptions and computational methods.

|**Feature**|**Maximum Likelihood Estimation (MLE)**|**Bayesian Parameter Estimation (BPE)**|
|---|---|---|
|**Estimate Type**|Deterministic (single best possible solution).|Probabilistic (probability density estimate).|
|**Prior Knowledge**|No prior knowledge is used.|Prior knowledge is absolutely necessary.|
|**Complexity**|Solved using easy gradient search and differential calculus.|Requires complex multidimensional integration.|
|**Overfitting Solution**|Handled using regularization parameters.|Overfitting is solved naturally by the selection of the prior.|

### 5. Gaussian Mixture Models (GMM)

A Gaussian Mixture Model is a probability distribution used universally for generative unsupervised learning or clustering. It represents normally distributed subpopulations within an overall population without needing to know which subpopulation a data point belongs to beforehand.

- **Mathematical Model:** The density function of a GMM is $P(x) = \sum_{k} \pi_k N(x|\mu_k, \Sigma_k)$.
    
- $\pi_k$ represents the weight or mixing coefficient of the k-th Gaussian component, determining its relative contribution.
    
- $N(x|\mu_k, \Sigma_k)$ is the probability density function of a single Gaussian component with mean $\mu_k$ and covariance $\Sigma_k$.
    

### 6. Expectation-Maximization (EM) Algorithm

The EM algorithm is an unsupervised learning technique used to determine local maximum likelihood estimates (MLE) for unobservable (latent) variables in statistical models. It is inherently linked to models like GMM and k-means clustering.

- **Expectation Step (E-step):** Computes the expected values of the latent variables based on current parameter estimates, effectively "guessing" missing values.
    
- **Maximization Step (M-step):** Uses the expected values from the E-step to update the model parameters to maximize the expected log-likelihood.
    
- **Convergence:** The E and M steps repeat iteratively until convergence, meaning the values of given variables match each other closely or the change in log-likelihood falls below a threshold.
    
- **EM for K-Means (PYQ):** K-means is a specific, hard-clustering application of the EM algorithm principles. In k-means, the E-step corresponds to assigning each data point to its closest centroid. The M-step corresponds to recalculating the centroids based on the current cluster assignments.
    

## Module 4: Hidden Markov Models for Sequential Pattern Classification

### 1. Introduction to Hidden Markov Models

A Hidden Markov Model (HMM) is a statistical model used to describe systems assumed to be Markovian, meaning the current state depends _only_ on the previous state. It describes the probabilistic relationship between a sequence of observations and a sequence of hidden states.

- **"Hidden" Nature:** The true states of the system are not directly observable, but are inferred from observable outputs.
    
- **Core Use:** Highly effective for predicting future observations or classifying sequential data.
    

### 2. Components of an HMM

An HMM consists of several key sets of variables and matrices:

- **States ($S$):** A set of $N$ hidden states that generate observed data.
    
- **Observations ($O$):** A set of $M$ visible variables that can be directly measured.
    
- **Initial State Distribution ($\pi$):** Specifies the probability of starting in each hidden state.
    
- **Transition Probability Matrix ($A$):** Defines the probability of moving from one hidden state to another.
    
- **Emission Probability Matrix ($B$):** Defines the probability of emitting a specific observation from a given hidden state.
    

### 3. Types of HMMs

|**Model Type**|**Description**|
|---|---|
|**Discrete HMM (DHMM)**|Both the hidden states and observations are discrete variables (e.g., specific phonemes in speech, distinct weather conditions).|
|**Continuous Density HMM (CDHMM)**|Both the states and observations are continuous in nature. Often trained using the Expectation-Maximization (EM) algorithm.|

### 4. Algorithms and Applications

- **Forward-Backward Algorithm:** Used to estimate the hidden state sequence from the observed data.
    
- **Viterbi Algorithm:** Calculates the most probable, specific sequence of hidden states based on the transition and emission probabilities.
    
- **Applications:** Widely used in Speech Recognition, Natural Language Processing, Bioinformatics, and Finance.
    
- **Limitations:** HMMs have limited modeling capabilities because they force the underlying structure of the data to be represented strictly by sequential hidden states, which may not capture complex dependencies.
    

### 5. PYQ Quick Facts for 1-Mark Questions

- **How is the state of the process described in an HMM?** It is described by a single discrete random variable.
    
- **Is an HMM a finite-state machine?** Yes, it can be viewed as a probabilistic extension of a non-deterministic finite-state machine, where transitions and emissions are governed by probability distributions rather than strict rules.
    
- **What suggests the existence of an efficient recursive algorithm for online smoothing?** Constant space.
    
- **Where are additional variables added in an HMM?** Additional state variables can be added to a temporal model while staying within the HMM framework.