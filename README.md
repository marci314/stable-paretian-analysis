# Stable Paretian Distribution Analysis

A comprehensive study of symmetric stable Paretian distributions $S_{\alpha}(\beta, c, \mu)$ using numerical methods, simulation, and financial modeling in MATLAB.

## Overview
This project explores the computational behavior of stable laws. It covers numerical convolution techniques for variables with differing tail indices, the robustness of nonparametric estimators (stableregkw), and the application of stable mixture models to 32 years of Dow Jones Industrial Average (DJIA) stock returns.

## Technical Components

### 1. Convolution of Symmetric Stables
Analysis of the sum $S = X_1 + X_2$ for independent variables with $\alpha_1 = 1.3$ and $\alpha_2 = 1.7$. 
* **Deterministic Methods**: Integral convolution, Characteristic Function (CF) inversion (Trapezoidal rule), and Fast Fourier Transform (FFT).
* **Stochastic Methods**: Direct simulation via the Chambers-Mallows-Stuck (CMS) algorithm (`stabgen`) and the Probability Integral Transform (PIT) using numerical inverse-CDFs.
* **Analysis**: Computed the $L_\infty$ norm to quantify the approximation error between PIT and CMS methods.

### 2. Tail Index Estimation (stableregkw)
Evaluation of the `stableregkw` estimator’s performance on both stable and non-stable sums.
* **Sample Size Sensitivity**: Comparison of precision using $n=1,000$ and $n=10,000$.
* **Bootstrap Precision**: Generation of 90% nonparametric bootstrap confidence intervals.
* **Convergence**: Verified the $\sqrt{n}$ convergence rate, observing that a 10x increase in sample size reduced confidence interval lengths by a factor of approximately 3.10 (matching the theoretical $\sqrt{10} \approx 3.16$).

### 3. Maximum Likelihood Estimation (MLE)
Implementation of MLE for single and mixture stable models applied to financial data.
* **Two-Component Mixtures**: Developed custom negative log-likelihood functions to fit mixtures of two symmetric stable distributions.
* **Financial Application**: Fitted the model to 25 DJIA assets. Findings indicate that two-component stable mixtures effectively capture the heavy-tailed behavior and high central concentration of 32 years of daily log-returns.



## Key Conclusions
* **Numerical Methods**: Deterministic methods (FFT/CF Inversion) provide noise-free density estimates, whereas stochastic methods exhibit significant variance in the tail regions ($4 \le s \le 8$).
* **Computational Efficiency**: The CMS algorithm is the most efficient for simulation (0.07s), while analytical integral convolution is the most intensive (1.18s).
* **Asset Modeling**: Symmetric stable mixtures provide a superior fit for leptokurtic financial data compared to standard Gaussian models.

## Software Requirements
* **MATLAB R2024b**
* Statistics and Machine Learning Toolbox (for `makedist`, `pdf`, and `mle` functions)
