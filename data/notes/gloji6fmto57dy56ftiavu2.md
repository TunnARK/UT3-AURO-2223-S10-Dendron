
Source:
- Video: [Lecture 11 Probability Review, Bayes Filters, Gaussians -- CS287-FA19 Advanced Robotics](https://www.youtube.com/watch?v=xamzdNUN1o0)
- Slide: [CS287FA19-AdvancedRobotics.Lecture11-ProbabilityReviewBayesFiltersGaussians.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CS287FA19-AdvancedRobotics.Lecture11-ProbabilityReviewBayesFiltersGaussians.pdf)
- Course given by Pieter Abbeel
---

![](/assets/images/P1K.Lecture11.Slide-01.png)

- LQR
- Shorcutting

# Introduction

## Why Probability in Robotics ?

![](/assets/images/P1K.Lecture11.Slide-02.png)

- Can take actions/decisions to search for more sensory information in order to improve state estimation.

## Example 1: Helicopter

![](/assets/images/P1K.Lecture11.Slide-03.png)

- magnometer gives an idea of orientation 
- We don't have a direct knowledge of the state of the heli but can inderectly know its state through thoses instruments

## Example 2: Mobile robot

![](/assets/images/P1K.Lecture11.Slide-04.png)

- Carefull with laser and reflecting surfaces as it renders the measures unusable

# Probability Review

![](/assets/images/P1K.Lecture11.Slide-05.png)

## Probabilty Axioms

![](/assets/images/P1K.Lecture11.Slide-06.png)
![](/assets/images/P1K.Lecture11.Slide-07.png)
![](/assets/images/P1K.Lecture11.Slide-08.png)

## Discrete Random Variables

![](/assets/images/P1K.Lecture11.Slide-09.png)

## Continuous Random Variables

![](/assets/images/P1K.Lecture11.Slide-10.png)

- Continuum => Integration
- In continuous proba space, we can't say that a probability takes an exact value but we should say that it lies in an interval

## Joint and Conditional Probability

![](/assets/images/P1K.Lecture11.Slide-11.png)

- Very important in robotics because we will always compare the state of the robot with the measurements taken
    - We indeed try to use the measurement to tell smth about the state
    - Or we want to know the dynamic now and relate it to the dynamic in the future 
    - Both require joint distributions over two random variables instead of just one

- If two variables are independent then you cannot tell anything about X when using Y since they are unrelated

- Joint Distribution
$$
P(X=x\;and\;Y=y) = P(x,y)
$$

- Conditional Probability
$$
P(x\;|\;y) = \dfrac{\;P(x,y)\;}{P(y)}
$$

## Law of Total Probability, Marginals

![](/assets/images/P1K.Lecture11.Slide-12.png)
<!--![](/assets/images/P1K.Lecture11.BB-01.png)-->

## Bayes' Rule

![](/assets/images/P1K.Lecture11.Slide-13.png)
![](/assets/images/P1K.Lecture11.BB-02.png)

- If there is a state, it will cause distribution of a reading
- Therefore the conditional $P(y|x)$ reflect causal effect and $P(x)$ represent the state deduced from previous estimates
- The division by $P(y)$ often written $\dfrac{1}{z}$ or $\eta$ is simply a normalisation

## Normalisation

![](/assets/images/P1K.Lecture11.Slide-14.png)

## Conditionning

![](/assets/images/P1K.Lecture11.Slide-15.png)
![](/assets/images/P1K.Lecture11.Slide-16.png)
<!--![](/assets/images/P1K.Lecture11.BB-03.png)
![](/assets/images/P1K.Lecture11.BB-04.png)-->


## Conditional Independance

![](/assets/images/P1K.Lecture11.Slide-17.png)
![](/assets/images/P1K.Lecture11.BB-05.png)
<!--
![](/assets/images/P1K.Lecture11.BB-06.png)-->

## Example of State Estimation

![](/assets/images/P1K.Lecture11.Slide-18.png)

## Casual vs Diagnostic Reasoning

![](/assets/images/P1K.Lecture11.Slide-19.png)

## Door Example (one measurement)

![](/assets/images/P1K.Lecture11.Slide-20.png)

> Does it mean that the sensor measuring $z$ can detect the door is open at 67% chance ??? (if so the conditional probability would return the precision of the instrument ???)

## Combining Evidence

![](/assets/images/P1K.Lecture11.Slide-21.png)

## Recursive Bayesian Updating 

![](/assets/images/P1K.Lecture11.Slide-22.png)

**Posterior Distribution**
$$
P(x\;|\;z_1,\dots,z_n) = \eta \times \prod_{i=1}^n \Big(\; P(z_i\;|\;x) \;\Big) \times P(x)
$$

## Door Example (second measurement)

![](/assets/images/P1K.Lecture11.Slide-23.png)

## A Typical Pitfall

![](/assets/images/P1K.Lecture11.Slide-24.png)

**BE CAREFUL ! Are the reading truly independent ? $\implies$ OVERCONFIDENCE**

# Bayes' Filters

![](/assets/images/P1K.Lecture11.Slide-25.png)

## Actions

![](/assets/images/P1K.Lecture11.Slide-26.png)

## Typical Actions 

![](/assets/images/P1K.Lecture11.Slide-27.png)

Actions increase uncertainty because they usually introduce new uncertainties.

## Modeling Acitons

![](/assets/images/P1K.Lecture11.Slide-28.png)

## Example: Closing the door

![](/assets/images/P1K.Lecture11.Slide-29.png)

## State Transitions

![](/assets/images/P1K.Lecture11.Slide-30.png)

## Integrating Outcome of Actions

![](/assets/images/P1K.Lecture11.Slide-31.png)

## Example: The Resulting Belief

![](/assets/images/P1K.Lecture11.Slide-32.png)

## Measurements

![](/assets/images/P1K.Lecture11.Slide-33.png)

## Bayes Fitlers: Framework

![](/assets/images/P1K.Lecture11.Slide-34.png)

## Markov Assumption

![](/assets/images/P1K.Lecture11.Slide-35.png)

## Bayes Filters Development

![](/assets/images/P1K.Lecture11.Slide-36.png)

## Bayes Filters Algorithm

![](/assets/images/P1K.Lecture11.Slide-37.png)

## Summary

![](/assets/images/P1K.Lecture11.Slide-38.png)

## Example: Robot Localization

![](/assets/images/P1K.Lecture11.Slide-39.png)

# Gaussians

![](/assets/images/P1K.Lecture11.Slide-40.png)

## Outline

![](/assets/images/P1K.Lecture11.Slide-41.png)

## Univariate Gaussian

![](/assets/images/P1K.Lecture11.Slide-42.png)

## Properties of Gaussians

![](/assets/images/P1K.Lecture11.Slide-43.png)

## Central Limit Theorem

![](/assets/images/P1K.Lecture11.Slide-44.png)

## Multivariate Gaussians

![](/assets/images/P1K.Lecture11.Slide-45.png)

> **"Symmetric Matrices are just a rotation away from being Diagonal Matrices"**

### Multivariate Gaussians Expectation

![](/assets/images/P1K.Lecture11.Slide-46.png)

### Multivariate Gaussians Examples

![](/assets/images/P1K.Lecture11.Slide-47.png)
![](/assets/images/P1K.Lecture11.Slide-48.png)
![](/assets/images/P1K.Lecture11.Slide-49.png)
![](/assets/images/P1K.Lecture11.Slide-50.png)
![](/assets/images/P1K.Lecture11.Slide-51.png)