# StatisticalStuff

This section contains external tabular data, visual materials, and theoretical explanations supporting the mathematical framework of my study.

## ADF Facts
For ADF stats, please reference the XLSX file. Just note that Schwert's lag was utilized to determine the optimal lag length because it was more precise in this dataset. That means for each annual window, maximum lag order was selected via upper-bound computation(s) pmax =⌊12(T/100)^0.25⌋ (Schwert, 1989), and optimal lag was determine by an Alkaline Information criterion (AIC) (all dependent on sample sizing, in this case, you have to understand that the average amount of days per year annually windowed for BTC-USD does not yield 365 days due to exchange hacks, exchange collapses, low liquidity, etc. Any dataset you manage to pull, you must account for that.) Furthermore, the approach for lag selection(s) was preferred for the precision given Bitcoin's properties at hourly granularity. Critical values for the constant-plus-trend specification are going to be referenced as "asymptotic values" (MacKinnon, 2010) which means the following information

1% --> -3.9600
5% --> -3.4100
10% --> -3.1300

These are going to be the most appropriate CVs given the various different sample sizes (remember, it is wise to calculate the critical values depending on your exact sample size, do not assume that these CV are static, and are expected to fit universally across different granularity level datasets, or different financial data) and it is also important to mention that "finite sample adjustments are negligible" (Cheung, et. al., 1995). All test statistics furthermore follow the Dickey fuller distribution (Fuller, 1996). You cannot use regular test statistics for this kind of test because the ADF test does not assume nor follow standard Student's t-distribution or normal distribution under the null hypothesis of a unit root. Using any kind of coventional t-tables are going to produce severely inflated Type I error rates and invalid inference. Please keep that in mind.

## Geometric Brownian Motion
The GBM test folder contains the yearly images for every simulation run. Although GBM is typically recalibrated on shorter intervals (weekly, monthly, or even daily), this project intentionally demonstrates the parameters on a year‑by‑year basis to show how the model evolves over longer horizons. You’ll also notice that there is no GBM parameter set for 2010. That is because there was not enough 2010 data to generate a valid walk‑forward projection for the start of 2011, so the first usable year begins in 2012.In a standard GBM pathway, prices generally remain within the central GBM cone shown in the images. Only a small number of years suggest that GBM would have produced reasonable forecasts for Bitcoin. However, because you cannot know future volatility in advance, and because past GBM results for BTC are so unreliable, it becomes difficult to trust the model’s forward path. Bitcoin’s volatility is simply too erratic for GBM to perform well. For context, the annualized volatility of the S&P 500 is far lower, while Bitcoin’s average annualized volatility is roughly 78%, which severely undermines GBM’s assumptions and predictive stability.

## LJUNG BOX TESTING 
The Ljung-box Q test xlsx file contains annual and full dataset statistics. Please note that for the lag selection for the size of the lag intervals determined by the Ljung-Box Q test were determined via box-pierce methods. The reason why this study went with lag selection choices utilizin gBox pierce methods were explicitly because the portmanteau framework was designed to test joint autocorrelation across multiple lags simultaneously, rather than relying on individual  
​significance tests that accumulate Type I error. The Box-Pierce lag rule m = 2ln(T) (Box & Pierce, 1970). For this study specifically, Box-Pierce selection was chosen over fixed-lag or information-criteria methods for two reasons. First, the lag count is deterministically set given the sample size, eliminating iterative fitting or arbitrary decisions across windows. Second, the logarithmic variant follows established refinements that yield approximately seventeen - 18 lags for 7k-8k, which can be helpful to detect any multi-day volatility clustering without issues. The Ljung-Box statistic was then applied with these lags to exploit its finite-sample correction. Furthremore a hybrid approach is the established standard in volatility diagnostics and was adopted here to maintain methodological consistency with the ARCH and GARCH literature while ensuring robust rejection thresholds across all test windows.

## Additional Notes
Please take great notice that you are not going to be able to use simple returns for the computational requirements of this project, and you must utilize log returns. If you use simple returns, it will result in loads of mathematical errors for replicability purposes.

_REFERENCES:
Schwert, G. W. (1988). Tests for unit roots: A Monte Carlo investigation. NBER Technical Working Paper No. 73.
Fuller, W. A. (1996). Introduction to statistical time series (2nd ed.). John Wiley & Sons.
Cheung, Y. W., & Lai, K. S. (1995). Lag order and critical values of the Augmented Dickey-Fuller test. Journal of Business & Economic Statistics, 13(3)
MacKinnon, J. G. (2010). Critical values for cointegration tests (Queen's Economics Department Working Paper No. 1227).
Box & Pierce (1970). Distribution of Residual Autocorrelations in Autoregressive-Integrated Moving Average Time Series Models. JASA 65(332), 1509-1526.
Bollerslev, T., Engle, R. F., & Nelson, D. B. (1994). ARCH models. In R. F. Engle & D. L. McFadden (Eds.), Handbook of Econometrics (Vol. 4, pp. 2959–3038). Elsevier Science B.V. 

