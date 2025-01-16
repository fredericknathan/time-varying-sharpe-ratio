# Time-Varying Sharpe Ratio Based on Conditional Volatility from GARCH Model
To establish a clear foundation for our analysis, we will adopt the following assumptions:

1. **Standard Deviation as a Measure of Risk**: The standard deviation of returns will be used as the primary metric to quantify risk.

2. **Non-IID Stock Data**: Stock market data will be treated as non-independent and non-identically distributed (non-IID), acknowledging the inherent dependencies and varying distributions over time.

These assumptions align with real-world financial market dynamics and provide a robust framework for subsequent modeling and analysis.

## Sharpe Ratio
The Sharpe Ratio is widely used to assess the risk-adjusted return of investments, including options, by calculating return over risk. However, this method overlooks the non-IID nature of stock data, which is crucial in real-world financial markets. Stock prices exhibit autocorrelation, where past returns influence future returns, leading to phenomena like momentum or mean reversion. Ignoring this correlation can distort risk and return calculations, ultimately providing a misleading assessment of an asset’s true performance. While the Sharpe Ratio is useful for general purposes, it is important to incorporate models that account for time-varying volatility and the non-IID behavior of stock data to more accurately evaluate risk-adjusted returns.

## Conditional Volatility
Conditional volatility refers to the time-varying risk of asset returns, adjusting for changing market conditions over time. Unlike standard deviation, which assumes constant volatility, conditional volatility reflects the influence of past returns and market shocks on future risk. In the context of the Sharpe ratio, conditional volatility is used to replace constant volatility in the denominator, offering a more accurate measure of risk that adapts to fluctuating market environments. The formula for conditional volatility in a GARCH model incorporates past return shocks and prior volatility to estimate future risk. Using conditional volatility in the Sharpe ratio calculation results in a more dynamic and precise evaluation of an asset’s risk-adjusted return.

![sharpe_ratio2.jpg](https://github.com/fredericknathan/time-varying-sharpe-ratio/blob/main/sharpe_ratio2.jpg)

The only modification to the original formula lies in the denominator, where the standard deviation (
) is replaced by conditional volatility 
.

![conditional_var.jpg](https://github.com/fredericknathan/time-varying-sharpe-ratio/blob/main/conditional_var.jpg)

In a GARCH(p, q) model (Generalized Autoregressive Conditional Heteroskedasticity), the conditional volatility, often denoted as 
, is modeled as a function of past squared residuals (ARCH terms) and past conditional variances (GARCH terms).

## Downside
Keep in mind that the GARCH model can suffer from overfitting when high values of p and q are selected. To mitigate this risk, it's crucial to perform hyperparameter tuning and use techniques such as cross-validation to identify the optimal model parameters. This will ensure better generalization and prevent the model from fitting noise in the data.

## Conclusion
The time-varying volatility can be modeled using a GARCH(p, q) framework to capture the non-IID nature of asset returns, with conditional volatility (
) serving as a dynamic risk measure. This allows for a more accurate calculation of the Sharpe ratio, incorporating time-varying risk in the denominator. To mitigate overfitting, it is essential to employ cross-validation and a rolling window approach for optimal hyperparameter selection.
