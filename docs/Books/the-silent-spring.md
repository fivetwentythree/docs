---
layout: default
title: The Silent Spring
parent: Books
nav_order: 4
---
# The Silent Spring

How can this happen and what made this happen

$$E=mc^2$$

this is the equation which hates cats

$$ i \hbar \frac{\partial}{\partial t} \Psi(\mathbf{r}, t) = \hat{H} \Psi(\mathbf{r}, t) $$


```python
import numpy as np
import matplotlib.pyplot as plt
x = np.linspace(0, 2*np.pi, 100)
y = np.sin(x)
plt.plot(x, y)
plt.show()
```

$$ i \hbar \frac{\partial}{\partial t} \Psi(\mathbf{r}, t) = \left[ -\frac{\hbar^2}{2m} \nabla^2 + V(\mathbf{r}, t) \right] \Psi(\mathbf{r}, t) $$

what can we do about it?

$$ i \hbar \frac{\partial}{\partial t} \Psi(x, t) = \left[ -\frac{\hbar^2}{2m} \frac{\partial^2}{\partial x^2} + V(x, t) \right] \Psi(x, t) $$



**Conceptual Framework:**

A sophisticated model needs to capture both **long-run equilibrium** drivers and **short-run dynamics/adjustments**. The housing market is characterized by:
1.  **Slow Supply Adjustment:** It takes time to build new houses.
2.  **Durability:** Houses last a long time.
3.  **Heterogeneity:** Location and type matter immensely (though we'll model an aggregate).
4.  **Significant Transaction Costs:** Stamp duty, agent fees, etc.
5.  **Importance of Credit and Leverage:** Most purchases involve mortgages.
6.  **Influence of Expectations:** Beliefs about future prices drive investment and purchasing decisions.
7.  **Government Policy Impacts:** Taxes, grants, zoning, monetary policy.

We can use an **Error Correction Model (ECM)** framework. This posits that while there's a long-run equilibrium relationship between house prices and fundamental drivers, prices can deviate in the short run. The ECM captures the speed at which prices adjust back towards this equilibrium, as well as short-run shocks.

**The Equation:**

Let `P_t` be a national house price index (e.g., Hedonic Home Value Index) at time `t`.
Let `I_t` be a measure of disposable income per capita.
Let `R_t` be a representative mortgage interest rate.
Let `Pop_t` be the working-age population or number of households (demand driver).
Let `H_t` be the housing stock.
Let `Cred_t` be a measure of credit availability/conditions (e.g., loan-to-value ratios, lending standards).
Let `Const_t` be housing completions or approvals (supply indicator).
Let `Rent_t` be a rental price index (alternative cost).
Let `Pol^D_t` represent demand-side policies (e.g., First Home Owner Grants, negative gearing settings).
Let `Pol^S_t` represent supply-side policies (e.g., land release, zoning changes).
Let `E_t[\Delta \ln P_{t+1}]` be the expected future growth rate of house prices formed at time t.

The model focuses on the *change* in the logarithm of house prices (`\Delta \ln P_t`), which approximates the percentage growth rate.

**The Error Correction Model (ECM) Structure:**

$\Delta \ln P_t = \alpha_0 + \lambda \left[ \ln P_{t-1} - \left( \beta_0 + \beta_1 \ln I_{t-1} + \beta_2 R_{t-1} + \beta_3 \ln Pop_{t-1} - \beta_4 \ln H_{t-1} + \beta_5 \ln Rent_{t-1} \right) \right] + \sum_{i=1}^{p} \gamma_i \Delta \ln P_{t-i} + \sum_{j=0}^{q} \delta_j \Delta \ln I_{t-j} + \sum_{k=0}^{r} \zeta_k \Delta R_{t-k} + \sum_{l=0}^{s} \eta_l \Delta \ln Const_{t-l} + \sum_{m=0}^{u} \theta_m \Delta Cred_{t-m} + \phi_1 Pol^D_t + \phi_2 Pol^S_t + \psi E_t[\Delta \ln P_{t+1}] + \epsilon_t$

**Explanation of Components:**

1.  $\Delta \ln P_t$: The growth rate of house prices in period `t`.
2.  $\alpha_0$: Constant term (long-run average growth not explained by other factors).
3.  $\lambda$: The speed of adjustment parameter (`\lambda < 0`). This dictates how quickly prices revert to equilibrium after a shock. A larger absolute value means faster adjustment.
4.  $\left[ \ln P_{t-1} - \left( ... \right) \right]$: The **Error Correction Term**. This is the deviation of the lagged log house price (`\ln P_{t-1}`) from its estimated long-run equilibrium value.
    *   $\beta_0 + \beta_1 \ln I_{t-1} + \beta_2 R_{t-1} + \beta_3 \ln Pop_{t-1} - \beta_4 \ln H_{t-1} + \beta_5 \ln Rent_{t-1}$: This represents the **long-run equilibrium relationship**.
        *   `\beta_1 > 0`: Higher income supports higher prices.
        *   `\beta_2 < 0`: Higher interest rates reduce affordability and prices.
        *   `\beta_3 > 0`: More people/households increase demand and prices.
        *   `\beta_4 > 0`: More housing stock relative to demand reduces prices (hence the negative sign in front of `\beta_4`).
        *   `\beta_5 > 0`: Higher rents make buying relatively more attractive, increasing demand and prices.
5.  $\sum_{i=1}^{p} \gamma_i \Delta \ln P_{t-i}$: **Short-run momentum/inertia**. Captures how past price growth influences current growth.
6.  $\sum_{j=0}^{q} \delta_j \Delta \ln I_{t-j}$: **Short-run income effects**. How changes in income growth affect price growth.
7.  $\sum_{k=0}^{r} \zeta_k \Delta R_{t-k}$: **Short-run interest rate effects**. How changes in interest rates affect price growth.
8.  $\sum_{l=0}^{s} \eta_l \Delta \ln Const_{t-l}$: **Short-run supply effects**. How changes in construction activity affect price growth (expect `\eta < 0`).
9.  $\sum_{m=0}^{u} \theta_m \Delta Cred_{t-m}$: **Short-run credit availability effects**. How changes in lending standards affect price growth (expect `\theta > 0`).
10. $\phi_1 Pol^D_t$: Impact of contemporaneous demand-side policies (could be lagged). Sign depends on policy (e.g., positive for grants).
11. $\phi_2 Pol^S_t$: Impact of contemporaneous supply-side policies (could be lagged). Sign depends on policy (e.g., negative for faster land release).
12. $\psi E_t[\Delta \ln P_{t+1}]$: **Expectations effect**. If people expect prices to rise faster, demand increases now (expect $\psi > 0$). This term is notoriously difficult to measure and often proxied, sometimes by lagged price changes (overlapping with the $\gamma$ terms) under adaptive expectations assumptions.
13. $\epsilon_t$: The error term, representing unobserved factors or random shocks. Assumed to be white noise.



$$
\begin{equation}
\begin{split}
\Delta \ln P_t = \alpha_0 &+ \lambda \left[ \ln P_{t-1} - \left( \beta_0 + \beta_1 \ln I_{t-1} + \beta_2 R_{t-1} + \beta_3 \ln Pop_{t-1} - \beta_4 \ln H_{t-1} + \beta_5 \ln Rent_{t-1} \right) \right] \\
&+ \sum_{i=1}^{p} \gamma_i \Delta \ln P_{t-i} + \sum_{j=0}^{q} \delta_j \Delta \ln I_{t-j} + \sum_{k=0}^{r} \zeta_k \Delta R_{t-k} \\
&+ \sum_{l=0}^{s} \eta_l \Delta \ln Const_{t-l} + \sum_{m=0}^{u} \theta_m \Delta Cred_{t-m} \\
&+ \phi_1 Pol^D_t + \phi_2 Pol^S_t + \psi E_t[\Delta \ln P_{t+1}] + \epsilon_t
\end{split}
\label{eq:AusHousingECM}
\end{equation}
$$

**Important Considerations:**

*   **Data:** Requires consistent time series data for all variables, which can be challenging. Variables like `Cred_t`, `Pol^D_t`, `Pol^S_t`, and especially `E_t[\Delta \ln P_{t+1}]` need careful construction or proxying.
*   **Estimation:** This model would typically be estimated using econometric techniques like Ordinary Least Squares (OLS) or more advanced time series methods, potentially involving cointegration analysis to confirm the long-run relationship.
*   **Lag Lengths:** The lag lengths (`p, q, r, s, u`) need to be determined empirically using information criteria (AIC, BIC) or other diagnostic tests.
*   **Aggregation:** This is a national-level equation. In reality, Australian housing markets are highly regional (Sydney vs. Melbourne vs. Perth vs. Regional areas), and a multi-market or panel data approach would be even more sophisticated but vastly more complex.
*   **Parameter Stability:** The relationships (the `\beta`, `\gamma`, etc. coefficients) might change over time due to structural breaks in the economy or market.
*   **Simplification:** This is still a simplification. It doesn't explicitly model investor vs. owner-occupier behaviour separately, foreign investment flows explicitly (though partially captured in Pop/Demand), or detailed micro-level dynamics.

This equation provides a sophisticated, theoretically grounded framework for analyzing the dynamics of the Australian housing market, integrating long-run fundamentals with short-run adjustments and policy effects.

