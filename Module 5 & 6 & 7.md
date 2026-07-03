
## Module 4: Hidden Markov Models for Sequential Pattern Classification

### 1. Definition and Core Concept

A Hidden Markov Model (HMM) is a statistical model used to describe systems that are assumed to be Markovian, meaning the current state of the system depends *only* on the previous state and not on any earlier states.

* **The "Hidden" Aspect:** The true underlying states of the system are not directly observable; instead, they are inferred from observable outputs or measurements.


* **Primary Use:** HMMs are widely used to predict future observations or classify sequences based on the hidden process generating the data.



### 2. Components of an HMM

An HMM characterizes the relationship between hidden states and observations using a specific set of parameters:

* **States ($S$):** A set of $N$ hidden states, $S = \{s_1, s_2, ..., s_N\}$, which generate the observed data.


* **Observations ($O$):** A set of $M$ visible variables, $O = \{o_1, o_2, ..., o_M\}$.


* **Initial State Distribution ($\pi$):** Specifies the probability of starting in each respective hidden state.


* **Transition Probability Matrix ($A$):** Defines the probability of moving from one hidden state to another.


* **Emission Probability Matrix ($B$):** Defines the probability of emitting a specific observation from a given hidden state.



### 3. Discrete vs. Continuous Models

* **Discrete HMM (DHMM):** Both the hidden states and the observations are discrete variables (e.g., distinct words in speech recognition).


* **Continuous Density HMM (CDHMM):** Both the states and observations are continuous in nature.



### 4. PYQ & Exam Focus Areas

* **State Representation:** In an HMM, the state of the process is described by a single discrete random variable.


* **Online Smoothing:** The concept of "constant space" suggests the existence of an efficient recursive algorithm for online smoothing in HMMs.


* **Framework Extensions:** Additional state variables can be added to a temporal model while staying within the HMM framework.


* **Finite-State Machine:** An HMM can be considered a probabilistic finite-state machine, as it transitions between states based on probabilities rather than strict deterministic logic.



---

## Module 5: Dimension Reduction Methods

### 1. The Curse of Dimensionality & Feature Management

As the dimensionality of an input dataset increases, predictive modeling and machine learning algorithms become exceedingly complex—a phenomenon known as the curse of dimensionality. Dimension reduction converts higher-dimension datasets into lesser dimensions while ensuring the preserved data provides similar information.

* **Feature Selection:** Isolating a subset of relevant features and discarding irrelevant ones (e.g., Filter, Wrapper, and Embedded methods).


* **Feature Extraction:** Transforming high-dimensional space into a new, lower-dimensional space (e.g., PCA, LDA).



### 2. Principal Component Analysis (PCA)

PCA is an unsupervised learning algorithm that converts correlated features into a set of linearly uncorrelated features (Principal Components) using orthogonal transformation.

* **Purpose:** PCA is a critical step in data dimension reduction, maximizing variance and minimizing information loss.


* **Conditions for Success:** PCA works better if variables are scaled to the same unit and the data exhibits a linear structure.


* **Algorithm Steps:**
1. Standardize the data to a mean of 0 and standard deviation of 1.


2. Calculate the covariance matrix to observe variable relationships.


3. Calculate the eigenvectors (directions of most variance) and eigenvalues (magnitude of variance).


4. Select the principal components (eigenvectors with the highest eigenvalues).


5. Transform the original data into the new lower-dimensional space.





### 3. Linear Discriminant Analysis (LDA)

LDA is a supervised technique used for modeling differences between classes. Unlike PCA, which represents data efficiently, LDA discriminates between classes efficiently.

* **Objective:** LDA maximizes the distance between the means of two classes while minimizing the variance within each individual class.


* **Formula:** The linear discriminant function is represented as $W^T X - W_0$.



### 4. PYQ Numerical Walkthrough: PCA Projection

**Problem from "6592_47619_I059.pdf":** *Given four points in 2D as $\{(1,1), (3,0), (3,2), (5,1)\}$, find the principal component using PCA. What is the projection of the vector $(2, 7)$ onto a lower dimension using PCA?*

**Step 1: Find the Means**

* $\bar{X} = \frac{1 + 3 + 3 + 5}{4} = 3$
* $\bar{Y} = \frac{1 + 0 + 2 + 1}{4} = 1$

**Step 2: Mean-Center the Data**
Subtract the means from each point $(X - \bar{X}, Y - \bar{Y})$:

* $P_1: (1-3, 1-1) = (-2, 0)$
* $P_2: (3-3, 0-1) = (0, -1)$
* $P_3: (3-3, 2-1) = (0, 1)$
* $P_4: (5-3, 1-1) = (2, 0)$

**Step 3: Calculate the Covariance Matrix**

* $Cov(X,X) = \frac{(-2)^2 + 0^2 + 0^2 + 2^2}{3} = \frac{8}{3}$
* $Cov(Y,Y) = \frac{0^2 + (-1)^2 + 1^2 + 0^2}{3} = \frac{2}{3}$
* $Cov(X,Y) = \frac{(-2)(0) + (0)(-1) + (0)(1) + (2)(0)}{3} = 0$
* The covariance matrix is diagonal: $\begin{bmatrix} 8/3 & 0 \\ 0 & 2/3 \end{bmatrix}$

**Step 4: Eigenvalues and Principal Component**
Since the matrix is diagonal, the eigenvalues are simply the diagonal entries: $\lambda_1 = 8/3$ and $\lambda_2 = 2/3$. The principal component is the eigenvector corresponding to the largest eigenvalue ($8/3$), which is $[1, 0]^T$.

**Step 5: Project the Vector (2,7)**
Mean-center the new vector: $(2-3, 7-1) = (-1, 6)$.
Project it onto the principal component using the dot product:
$(-1 \times 1) + (6 \times 0) = -1$.
The projection onto the lower dimension is **-1**.

---

## Module 6: Non-parametric Estimation Techniques

### 1. Parametric vs. Non-Parametric Methods

* **Parametric Methods:** Assume the underlying population follows a specific distribution (like a Normal distribution) and attempt to estimate its fixed parameters (mean, standard deviation).


* **Non-Parametric Methods:** Make minimal assumptions about the data distribution. They estimate the probability density function (PDF) directly from the data, providing greater flexibility for complex, unknown distributions.



### 2. Histogram Density Estimator

The histogram is the simplest way to estimate density, grouping data into specific bins.

* **Advantages:** It is simple to evaluate and use, and it can be computed sequentially as new data arrives (allowing you to discard the raw data once the histogram is computed).


* **Disadvantages:** It scales poorly in high dimensions (curse of dimensionality), and the estimated density has unnatural discontinuities driven strictly by arbitrary bin edges rather than the underlying data.


* **Key Lesson:** To estimate probability density accurately, a smoothing parameter (bin width) must be carefully chosen—neither too large nor too small—to consider data points within a local neighborhood.



### 3. Parzen-Window Method

The Parzen window is a generalization of K-nearest neighbors.

* **Concept:** Instead of finding a fixed number of neighbors, it considers a voting scheme for all sample points and assigns weights based on a specific kernel function (window function).


* **Characteristics:** It requires no dedicated training phase, making testing slower, and its success heavily relies on the choice of the window dimension $h_n$. As the volume of the hypercube $V_n$ approaches zero (and $nV_n$ approaches infinity), the variance of the estimate approaches zero.



### 4. K-Nearest Neighbor (KNN) Classification

KNN is a non-parametric, supervised, "lazy learner" algorithm. It does not build a model during training; instead, it stores the dataset and performs classification entirely at runtime.

* **How it Works:** To classify a new data point, the algorithm calculates the Euclidean distance to all stored points, selects the $K$ closest neighbors, and assigns the new point to the category that appears most frequently among those $K$ neighbors.


* **Distance Metrics:** KNN relies on metrics like Euclidean Distance (standard for geometrical problems), Minkowski Metric (which includes Manhattan/City Block distance), and Mahalanobis Distance.


* **Error Rate:** When the number of training samples tends to infinity, the error rate in a nearest neighbor classifier is at most twice the Bayes Error.