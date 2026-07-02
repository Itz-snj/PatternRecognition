## Module 1: Basics of Pattern Recognition

### Fundamental Concepts

Pattern recognition is the process of recognizing patterns by using a machine learning algorithm. It involves the classification of data based on already gained knowledge or statistical information extracted from patterns.

- **Pattern:** Anything around us in the digital world, mathematically represented by applying algorithms.
    
- **Feature:** A function of one or more measurements that quantifies significant characteristics of an object.
    
- **Feature Vector:** An n-dimensional vector of numerical features that represent an object.
    
- **Feature Extraction:** The process of transforming raw data into numerical features that can be processed while preserving original information.
    
- **Feature Selection:** The process of isolating the most consistent, non-redundant, and relevant features to use in model construction.
    

### The Pattern Recognition Design Cycle

The design of a classification system follows a specific interrelated cycle.

- **Sensing and Data Acquisition:** Stimuli produced by objects are perceived by sensory devices to create a measurement space.
    
- **Segmentation:** Data objects are segmented into smaller segments.
    
- **Feature Generation/Extraction:** Subsets of attribute values are selected to create a feature space, reducing the measurement space dimension.
    
- **Classifier Design:** AI models group or cluster the objects based on probability theory or learning techniques.
    
- **System Evaluation:** An unknown pattern is presented to the system to evaluate its performance and efficiency.
    

### Major Approaches to Pattern Recognition

There are four primary approaches used to build a pattern recognition system:

|**Approach**|**Description**|
|---|---|
|**Template Matching**|Finds similarity between two entities by comparing a pattern against a stored template (e.g., a $d \times d$ mask) in a knowledge base.|
|**Statistical Approach**|Represents patterns in a d-dimensional space and uses probability distributions to draw decision surfaces that separate classes into compact regions.|
|**Syntactic Approach**|Decomposes complex patterns into simpler sub-patterns using hierarchical grammar rules (e.g., syntax trees).|
|**Neural Networks**|Uses massively parallel computing systems with interconnected simple processors that update weights to learn and generalize.|

### Learning Types

- **Supervised Learning:** The system builds a model using labeled training data to predict output classes (Classification).
    
- **Unsupervised Learning:** The system learns without supervision, finding useful insights and restructuring unlabeled input data into groups (Clustering).
    
- **Reinforcement Learning:** A feedback-based method where the system learns and updates itself through rewards and punishments for its actions.
    

## Module 2: Bayesian Decision Theory

### Foundations of Bayesian Theory

Bayesian Decision Theory is a statistical approach that leverages probability to make classifications and measures the risk of assigning an input to a class. The rule describes the most reasonable action based on current observations and prior knowledge.

The core formula is Bayes' Theorem:

$$P(C_i|X) = \frac{P(C_i)P(X|C_i)}{P(X)}$$

- **Prior Probability $P(C_i)$:** The probability of a class occurring independently of any conditions (based on past occurrences).
    
- **Likelihood $P(X|C_i)$:** The probability that outcome $C_i$ occurs given current condition $X$.
    
- **Evidence $P(X)$:** The number of times the conditions $X$ occurred. The greek letter Sigma in the generalized formula denominator guarantees it can never be zero.
    
- **Posterior $P(C_i|X)$:** The updated probability that outcome $C_i$ occurs given the condition $X$.
    

### Bayesian Classifier & Risk Minimization

A Bayesian classifier (or Naive Bayes) assumes that features are conditionally independent given the class label. It applies Bayes' decision rule to minimize the expected misclassification rate (Bayes' risk) by selecting the class with the highest posterior probability.

- **Optimal Classifier:** Of all classifiers, the Optimal Bayes classifier has the lowest probability of misclassifying an observation.
    
- **Conditional Average Risk:** If a pattern classifier decides an object belongs to $\omega_j$ when it actually belongs to $\omega_i$, it incurs a loss $L_{ij}$. The conditional average risk is the sum of these probability-weighted losses.
    

### Normal (Gaussian) Density

In continuous feature spaces, conditional probabilities are typically modeled using continuous probability distributions.

- **Univariate Gaussian Distribution:** Defined by mean $\mu$ and standard deviation $\sigma$.
    
- **Univariate Formula:** $f(x,\mu,\sigma) = \frac{1}{\sigma\sqrt{2\pi}}e^{\frac{-(x-\mu)^2}{2\sigma^2}}$.
    
- **Multivariate Normal Distribution Formula:** $f_{X}(x) = \frac{1}{(2\pi)^{d/2}|\Sigma|^{1/2}}exp\{-\frac{1}{2}(x-\mu)^T\Sigma^{-1}(x-\mu)\}$.
    
- **Characteristics:** The curve is symmetric, bell-shaped, and unimodal. The mean, median, and mode are equal. The total area under the curve equals 1.
    

### Discriminant Functions and Decision Surfaces

A discriminant function is a mathematical equation based on a set of variables used to discriminate or classify samples. A decision surface is the diagnostic tool or boundary in a feature space where the classifier assigns different patterns to different classes.

| **Type of Discriminant**         | **Mathematical Assumption**                                                                                                                         |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Linear Discriminant (LDA)**    | Assumes decision boundaries are linear. If the covariance matrices for all classes are identical, the discriminant functions will always be linear. |
| **Quadratic Discriminant (QDA)** | Relaxes the linearity assumption, allowing for quadratic boundaries defined by a quadratic term matrix.                                             |
| **Nonlinear Discriminant**       | Uses Kernel Support Vector Machines (SVM) when boundaries are highly nonlinear.                                                                     |
| **Probabilistic Discriminant**   | Uses models like Gaussian Mixture Models (GMM) to assign probabilities based on evidence and likelihoods.                                           |

### Semester Numerical Guide: Solving for Threshold ($X_0$)

A standard semester numerical involves finding the decision boundary threshold ($X_0$) for a two-class problem where both classes follow a Gaussian distribution.

**Scenario:** Two classes ($\omega_1, \omega_2$) have means $\mu_1, \mu_2$ and the _same_ variance $\sigma^2$. If the costs for choosing incorrectly are $\lambda_{12}$ and $\lambda_{21}$, and correct classification costs are zero ($\lambda_{11} = \lambda_{22} = 0$), the optimal threshold minimizing average risk is calculated as:

$$x_0 = \frac{\mu_1 + \mu_2}{2} - \frac{\sigma^2}{\mu_1 - \mu_2} \ln \left( \frac{\lambda_{21} P(\omega_2)}{\lambda_{12} P(\omega_1)} \right)$$

_External Knowledge Note for Sums:_ If the problem states that prior probabilities are equal ($P(\omega_1) = P(\omega_2) = 0.5$) and the costs of misclassification are equal (or not provided, implying zero/equal risk), the natural logarithm term evaluates to $\ln(1) = 0$. In this simplified case, the optimal decision boundary is exactly the midpoint between the two means: $x_0 = \frac{\mu_1 + \mu_2}{2}$.