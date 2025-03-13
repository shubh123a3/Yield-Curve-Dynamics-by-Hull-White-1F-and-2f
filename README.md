# Yield Curve Dynamics using Hull-White 1F and 2F Models


https://github.com/user-attachments/assets/b039d0e3-8ae8-454b-a0e4-3fe0ddc8d4ca


## Introduction
This project explores yield curve dynamics using the **Hull-White One-Factor (1F) and Two-Factor (2F) models**. These models describe the evolution of short-term interest rates and are widely used in interest rate modeling and derivative pricing.

The Hull-White model is an extension of the Vasicek model, allowing for a time-dependent mean-reverting level, which provides a better fit to market data.

## Hull-White One-Factor (1F) Model
The **Hull-White 1F model** describes the short rate \( r(t) \) as a stochastic process:

$$
d r(t) = \lambda (\theta(t) - r(t)) dt + \eta dW_t
$$

where:
- \( \lambda \) is the mean reversion speed.
- \( \theta(t) \) is the time-dependent drift function ensuring the model fits the initial yield curve.
- \( \eta \) is the volatility of the short rate.
- \( W_t \) is a standard Brownian motion.

### Zero-Coupon Bond Pricing in Hull-White 1F Model
The price of a zero-coupon bond \( P(t,T) \) maturing at \( T \) is given by:

$$
P(t,T) = A(t,T) e^{-B(t,T) r(t)}
$$

where:

$$
B(t,T) = \frac{1 - e^{-\lambda (T-t)}}{\lambda}
$$

$$
A(t,T) = \frac{P(0,T)}{P(0,t)} e^{B(t,T) f(0,t) - \frac{\eta^2}{2 \lambda^2} (B(t,T) - (T-t))^2}
$$

## Hull-White Two-Factor (2F) Model
The **Hull-White 2F model** extends the 1F model by introducing an additional factor to capture movements in the term structure more accurately:

$$
 d r(t) = \lambda_1 (\theta_1(t) - r(t)) dt + \eta_1 dW_t^1 + \eta_2 dW_t^2
$$

$$
 d v(t) = \lambda_2 (- v(t)) dt + \eta_2 dW_t^2
$$

where:
- \( v(t) \) is a second factor that captures long-term trends in interest rates.
- \( \lambda_2 \) is the mean reversion speed of the second factor.
- \( \eta_2 \) is the volatility of the second factor.
- \( W_t^1 \) and \( W_t^2 \) are correlated Brownian motions.

### Zero-Coupon Bond Pricing in Hull-White 2F Model
The bond price under the 2F model is:

$$
P(t,T) = A(t,T) e^{-B_1(t,T) r(t) - B_2(t,T) v(t)}
$$

where:

$$
B_1(t,T) = \frac{1 - e^{-\lambda_1 (T-t)}}{\lambda_1}, \quad B_2(t,T) = \frac{1 - e^{-\lambda_2 (T-t)}}{\lambda_2}
$$

$$
A(t,T) = \frac{P(0,T)}{P(0,t)} e^{B_1(t,T) f(0,t) - \frac{\eta_1^2}{2 \lambda_1^2} (B_1(t,T) - (T-t))^2 - \frac{\eta_2^2}{2 \lambda_2^2} (B_2(t,T) - (T-t))^2}
$$

## Implementation
The project implements the following:
- **Monte Carlo simulations** for interest rate evolution under both 1F and 2F models.
- **Analytical pricing** of zero-coupon bonds using the derived formulas.
- **Yield curve fitting** to real market data.

## Files in the Repository
- `hull_white_1f.py` - Implements the 1F model.
- `hull_white_2f.py` - Implements the 2F model.
- `monte_carlo_simulation.py` - Performs Monte Carlo simulations.
- `yield_curve_fitting.py` - Fits the yield curve analytically.
- `README.md` - This documentation.

## Requirements
To run the project, install dependencies using:
```bash
pip install numpy scipy matplotlib pandas
```

## Usage
Run simulations with:
```bash
python hull_white_1f.py
```

For 2F model:
```bash
python hull_white_2f.py
```

## Conclusion
This project provides a quantitative approach to modeling interest rates using Hull-White models, with both Monte Carlo simulations and analytical solutions. It is a useful tool for pricing bonds, derivatives, and risk management in financial markets.
