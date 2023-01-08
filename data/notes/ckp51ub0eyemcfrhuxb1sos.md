
Source:

- Video: [Lecture 12 Kalman Filters -- CS287-FA19 Advanced Robotics at UC Berkeley](https://www.youtube.com/watch?v=eCjffhEeQyw)
- Slide: [CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters.pdf](https://raw.githubusercontent.com/TunnARK/UT3-AURO-2223-S10-Dendron/main/vault/assets/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters.pdf)
- Course given by Ignasi CLAVERA

---

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-01.png)

<!--
# Outline

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-02.png)
-->

# Gaussians

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-03.png)

## Mutlivariate Gaussians

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-04.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-05.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-06.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-07.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-08.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-09.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-10.png)

## Partitioned Multivariate Gaussian

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-11.png)

### Dual Representation

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-12.png)

## Marginalization

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-13.png)

## Recap

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-14.png)

### Self-quiz

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-15.png)

### Conditioning

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-17.png)

# Kalman Filtering

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-18.png)

## Presentation

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-19.png)

## Time Update

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-20.png)

### Joint Distribution

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-21.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-22.png)

### Recap

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-23.png)

## Generality

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-24.png)

## Observation Update

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-25.png)

## Complete Kalman Filtering Algorithm

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-26.png)

## Summary

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-27.png)

# Extend Kalman Filter (EKF)

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-28.png)

## Nonlinear Dynamical Systems

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-29.png)

## Linearity Assumption Revisited

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-30.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-31.png)

## Non-Linear Function

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-32.png)

## EKF Linearization

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-33.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-34.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-35.png)

### First Order Taylor Series Expansion

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-36.png)

## EKF Algorithm

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-37.png)

## Summary

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-38.png)

# Unscented Kalman Filter (UKF)

> **Also called "_signma-point filter_"**

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-39.png)

## Linearization via Unscented Transform

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-40.png)

## UKF Sigma-Point Estimate

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-41.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-42.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-43.png)

## Intuition

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-44.png)

## Original Unscented Transform

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-45.png)

## UKF Algorithm

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-46.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-47.png)

## Summary

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-48.png)

# Forthcoming

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-49.png)

## Things to be aware of

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-50.png)
![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-51.png)

## Kalman Filter Property

![](/assets/images/CS287FA19-AdvancedRobotics.Lecture12-KalmanFilters-52.png)


