# Pooling-or-Segmentation-Robot-Dispatch-in-Multi-Floor-Buildings


This repository contains the analytical frameworks, numerical verification models, and simulation suites for Chapter 3 of the Ph.D. dissertation **"Optimal Spatial and Temporal Decisions under Uncertainty"** (McMaster University, DeGroote School of Business).

The core research addresses a fundamental fleet architecture decision facing an autonomous delivery system operator: whether to dedicate robots to individual floors (Non-Pooling) or to share a combined fleet across all floors (Pooling) via a central vertical elevator.

## Research Overview

This study models a multi-floor facility where each floor is represented as a circular service region. We evaluate the trade-off between the ** pooling benefit** (capacity sharing to dampen demand variability) and the **vertical travel penalty** (service time inflation due to inter-floor elevator transit).

### Key Analytical Contributions

1. **Service Time Distributions:** We characterize exact service time formulations derived from floor disk geometry, distinguishing independent $M/M/1$ queues (Non-Pooling) from integrated $M/M/m$ queuing structures (Pooling).
2. **The Sandwich Policy:** We prove that when the vertical travel penalty $h$ is below a critical threshold $h_{max}(R)$, pooling is superior *only* within a bounded demand interval $[\Lambda_1^*, \Lambda_2^*]$. The system favors a dedicated architecture at low demand (due to travel overhead) and high demand (due to premature saturation of the slower pooled fleet)
3. **Critical Threshold Characterization:** We derive the explicit closed-form upper bound for pooling viability, proving that for a symmetric two-floor environment:
   $$h_{max}(R) = \frac{R}{3}$$
  When $h \ge R/3$, a dedicated architecture strictly dominates across all stable arrival rates.
4. **General $m$-Floor Extension:** We generalize the framework to buildings with an arbitrary number of floors $m \ge 2$, utilizing the exact expected vertical displacement $E[|Z_1 - Z_2|] = \frac{m^2-1}{3m}$.

## Repository Organization

The repository is structured as follows:

* `notebooks/chapter_3.5.1_validation_regimes.ipynb`: Code replicating the three-regime system behavior, generating the expected response time curves $E[T]$ against demand intensity $\Lambda$, and mapping the optimal pooling bubble zone[cite: 2391, 2392].
* `notebooks/chapter_3.5.2_sensitivity_analysis.ipynb`: Numerical evaluation mapping the sensitivity of boundaries $\Lambda_1^*$ and $\Lambda_2^*$ to variations in floor radius $R$, vertical penalty $h$, and structural demand asymmetry $p_1$[cite: 2419, 2420].
* `notebooks/chapter_3.6.1_extension_m_floors.ipynb`: Implementation of the general $m$-floor expansion ($m \in [2, 12]$) mapping the monotone decline of $h_{max}$ as building height scales[cite: 535, 539].

## Dependencies and Installation

The numerical computations and plots require a standard Python 3 data science stack. 

```bash
pip install numpy matplotlib
