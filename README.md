# 1Factor_Vasicek

![image](https://github.com/user-attachments/assets/b1e0d446-082a-4c93-86a2-991b9a7720f8)

The Vasicek model is a one-factor stochastic model to predit short rates (rates changing at very small intervals). It has the advantages of Mean reversion and being fairly simple to compute. However, it allows for negative rates which might not be suitable for all workcases.

The Model uses a basic Stochastic equation of,
```math
d(r_{t}) = a(b - r_{t})dt + {\sigma}dW_{t}
```
where,

a is the mean reversion speed

b is the long run mean 

sigma is the volatility of the rate
  
```math
r_{t + dt} = r_{t}e^{-adt} + b(1 - e^{-adt}) + {\sigma}e^{-adt}{\int_{0}^{dt} e^{-as} \, ds}
```
where,
```math
r_{t + dt} \thicksim N[r_{t}e^{-adt} + b(1 - e^{-adt}), \frac{\sigma^2}{2a} (1 - \exp(-adt))]
```

The model was used to predict TONAR (Tokyo Overnight Average Rate) for the next 3 years (considering start as 1-1-2025)

The Model's parameter were estimated with the help of 2 techniques, 
Maximum Likelihood Estimation 
```math
\hat{\theta}_{MLE} = \underset{\theta}{\arg\max} \, L(\theta | x)
```
and Ordinary Least Squares
```math
\hat{\boldsymbol{\beta}}_{OLS} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{y}
```

ultimately the OLS parameters were choosen for simulation.

![image](https://github.com/user-attachments/assets/37b71924-f00b-482f-a393-11f6384176c0)

However, the simulated rates do not seem to follow the trend post march-2024, as we see a sudden increase in the TONAR.
The Reason for the model to not capture the sudden spike in the TONAR, is entirely due to an external factor. 
Which is, the change in the monetary policy of Japan, where Negative interest rates where ended in march 2024.
Along with this, a demand pull inflation has been noticed which has been raising the interest rates higher due to the excessive demand.
Before these changes, the model did seem to capture the movement of the rates adequately.
