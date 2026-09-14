# Global-Gold-Market-Analysis

## 1. Overview of the Empirical Analysis

The objective of this study is to examine the short-run price transmission and return relationships among five major gold markets: the Shanghai Futures Exchange (SHFE), Shanghai Gold Exchange (SGE), Multi Commodity Exchange of India (MCX), COMEX in the United States, and the London Bullion Market Association (LBMA) gold market.

The analysis uses daily data for the period from January 2023 to August 2024 for the common five-market sample. The common sample contains 376 observations after matching the trading dates across all five markets. The analysis is based on daily returns rather than price levels because return series are more suitable for studying short-run transmission and are stationary in the present dataset.

Several complementary methods were used. First, descriptive statistics and correlation analysis were used to understand the basic relationships among the markets. Second, one-day lead-lag correlations were calculated to identify whether movements in one market were associated with movements in another market on the following trading day. Third, pairwise Granger causality tests were used to examine whether past returns in one market contained useful information for predicting another market. Fourth, a multivariate Vector Autoregression (VAR) model was estimated so that the markets could be studied jointly. Finally, impulse-response functions (IRFs), forecast error variance decomposition (FEVD), and robustness analysis were used to examine the strength and stability of the observed relationships.

The results should be interpreted as evidence of **return transmission and predictive temporal precedence**, rather than as definitive proof of economic causality.

---

# 2. Descriptive Statistics

The descriptive statistics provide an initial picture of the behaviour of daily gold-market returns.

| Market | Mean Return | Standard Deviation |   Minimum |   Median |  Maximum |
| ------ | ----------: | -----------------: | --------: | -------: | -------: |
| SHFE   |    0.000807 |           0.006449 | -0.029729 | 0.000792 | 0.029279 |
| SGE    |    0.000774 |           0.007851 | -0.033673 | 0.000784 | 0.038874 |
| MCX    |    0.000545 |           0.007828 | -0.057867 | 0.000752 | 0.026572 |
| COMEX  |    0.000776 |           0.008923 | -0.027866 | 0.000590 | 0.031081 |
| LBMA   |    0.000903 |           0.008699 | -0.030771 | 0.000526 | 0.032081 |

The average daily returns of all five markets are positive but relatively small. The mean return ranges from approximately 0.000545 for MCX to 0.000903 for LBMA. This indicates that, over the sample period, the markets experienced a small positive average daily return.

The standard deviations show differences in daily volatility. COMEX has the highest standard deviation at approximately 0.008923, followed by LBMA at 0.008699. MCX and SGE have similar volatility, while SHFE has the lowest standard deviation at approximately 0.006449.

This suggests that the U.S. and London markets experienced somewhat larger day-to-day return fluctuations than the Chinese SHFE market during the common sample period.

The minimum return for MCX is particularly notable. MCX records a minimum daily return of approximately **−0.057867**, or about **−5.79%**, on 23 July 2024. This observation was investigated separately because it is substantially larger than most other observations in the sample.

The investigation showed that this was not a calculation error. The original MCX source data show a fall from approximately 72,718 on 22 July to 68,510 on 23 July, corresponding to approximately a −5.79% return. Therefore, the observation was retained in the main sample rather than being removed simply because it was unusually large.

---

# 3. Contemporaneous Correlation Analysis

The contemporaneous correlation matrix provides information about how markets move together on the same trading date.

|       |  SHFE |   SGE |   MCX | COMEX |  LBMA |
| ----- | ----: | ----: | ----: | ----: | ----: |
| SHFE  | 1.000 | 0.698 | 0.139 | 0.062 | 0.228 |
| SGE   | 0.698 | 1.000 | 0.352 | 0.301 | 0.459 |
| MCX   | 0.139 | 0.352 | 1.000 | 0.824 | 0.660 |
| COMEX | 0.062 | 0.301 | 0.824 | 1.000 | 0.752 |
| LBMA  | 0.228 | 0.459 | 0.660 | 0.752 | 1.000 |

The strongest contemporaneous relationship is between **MCX and COMEX**, with a correlation of **0.824**. This indicates that the two markets tend to move in the same direction on the same trading day.

The correlation between **COMEX and LBMA is 0.752**, showing a strong relationship between the U.S. and London gold markets.

The two Chinese markets, **SHFE and SGE**, also show a strong contemporaneous correlation of **0.698**.

The relationships between SHFE and the international markets are weaker. For example, the correlation between SHFE and COMEX is only **0.062**, while SHFE and LBMA have a correlation of **0.228**.

This difference is important. A low same-day correlation does not necessarily mean that SHFE is disconnected from the international markets. Because the markets operate at different times of the day and in different time zones, information from one market may appear in another market on the following trading day. Therefore, lead-lag analysis is necessary.

---

# 4. One-Day Lead-Lag Analysis

To investigate this issue, one-day lead-lag correlations were calculated. In this analysis, the return of the leading market on day t−1 is compared with the return of the target market on day t.

The strongest relationships were:

| Previous-Day Lead | Current-Day Target | Correlation |
| ----------------- | ------------------ | ----------: |
| COMEX             | SHFE               |   **0.728** |
| LBMA              | SHFE               |   **0.664** |
| MCX               | SHFE               |   **0.604** |
| COMEX             | SGE                |   **0.550** |
| MCX               | SGE                |   **0.428** |
| SGE               | SHFE               |   **0.385** |
| LBMA              | SGE                |   **0.360** |

The strongest one-day relationship is **COMEX → SHFE**, with a correlation of **0.728**. This means that a positive or negative movement in COMEX on one day is strongly associated with a movement in the same direction in SHFE on the following trading day.

The second strongest relationship is **LBMA → SHFE**, with a correlation of **0.664**.

The relationship **MCX → SHFE** is also relatively strong, with a correlation of **0.604**.

For SGE, the strongest one-day lead-lag relationship is **COMEX → SGE**, with a correlation of **0.550**.

In contrast, many reverse relationships are weak or negative. For example, SHFE → COMEX has a correlation of **−0.082**, while SGE → COMEX is **−0.156**.

These results provide initial evidence that information may travel from the U.S. and other international markets toward the Chinese markets with a time delay.

However, correlation alone cannot establish causality. Therefore, formal Granger causality tests were conducted.

---

# 5. Granger Causality Results

Pairwise Granger causality tests were conducted using one and two lags. The purpose of these tests is to determine whether past returns in one market contain statistically significant information for predicting returns in another market.

The results show several important directional relationships.

## 5.1 COMEX and SHFE

The evidence for **COMEX → SHFE** is particularly strong.

For one lag:

* F-statistic = **415.808**
* p-value < **0.001**

For two lags:

* F-statistic = **213.181**
* p-value < **0.001**

The reverse relationship, **SHFE → COMEX**, is not statistically significant:

* Lag 1: F = 2.210, p = **0.138**
* Lag 2: F = 1.123, p = **0.326**

Therefore, the results provide strong evidence that past COMEX returns contain information useful for predicting SHFE returns, while the reverse predictive relationship is not supported.

This is one of the strongest findings of the study.

---

# 5.2 COMEX and SGE

The relationship between COMEX and SGE is also strong.

For **COMEX → SGE**:

* Lag 1: F = **187.599**, p < **0.001**
* Lag 2: F = **97.241**, p < **0.001**

The reverse direction, **SGE → COMEX**, is also statistically significant:

* Lag 1: F = **7.042**, p = **0.008**
* Lag 2: F = **3.140**, p = **0.044**

Therefore, unlike the COMEX-SHFE relationship, the COMEX-SGE relationship shows evidence of **two-way predictive interaction**.

However, the strength is clearly asymmetric because the evidence from COMEX to SGE is much stronger than from SGE to COMEX.

---

# 5.3 COMEX and MCX

The Granger results do not provide strong evidence that COMEX predicts MCX.

For **COMEX → MCX**:

* Lag 1: F = 1.669, p = **0.197**
* Lag 2: F = 2.894, p = **0.057**

The lag-2 result is close to the 5% significance level but does not cross it. Therefore, it should not be described as statistically significant at the conventional 5% level.

For **MCX → COMEX**:

* Lag 1: F = 0.352, p = **0.553**
* Lag 2: F = 2.057, p = **0.129**

Thus, neither direction provides strong evidence of Granger predictive causality at the 5% level.

This is an important result because MCX has a very high contemporaneous correlation with COMEX, but high same-day correlation does not automatically mean that one market predicts the other.

---

# 5.4 COMEX and LBMA

The relationship between COMEX and LBMA is strongly directional.

For **COMEX → LBMA**:

* Lag 1: F = **35.074**, p < **0.001**
* Lag 2: F = **24.551**, p < **0.001**

For **LBMA → COMEX**:

* Lag 1: F = 0.143, p = **0.706**
* Lag 2: F = 0.000, p = **1.000**

Therefore, the results provide strong evidence of predictive transmission from COMEX toward LBMA, but not from LBMA toward COMEX.

---

# 5.5 LBMA and SHFE

The relationship **LBMA → SHFE** is also strong:

* Lag 1: F = **288.623**, p < **0.001**
* Lag 2: F = **142.667**, p < **0.001**

The reverse direction is not significant:

* SHFE → LBMA, Lag 1: p = **0.146**
* SHFE → LBMA, Lag 2: p = **0.278**

Thus, the evidence indicates that previous LBMA returns contain useful predictive information for SHFE returns.

---

# 5.6 SGE and SHFE

The results also provide strong evidence for **SGE → SHFE**:

* Lag 1: F = **87.649**, p < **0.001**
* Lag 2: F = **44.167**, p < **0.001**

The reverse direction is not significant:

* Lag 1: F = 1.688, p = **0.195**
* Lag 2: F = 0.568, p = **0.567**

Therefore, SGE appears to have predictive information for SHFE, while the evidence for SHFE predicting SGE is weak.

---

# 5.7 MCX, SGE and LBMA

The MCX-SGE relationship is more complicated.

For **MCX → SGE**:

* Lag 1: F = **99.646**, p < **0.001**
* Lag 2: F = **52.812**, p < **0.001**

For **SGE → MCX**:

* Lag 1: F = 2.882, p = **0.090**
* Lag 2: F = **5.266**, p = **0.006**

Thus, there is evidence of predictive interaction in both directions, but the MCX → SGE relationship is considerably stronger.

For **LBMA → SGE**:

* Lag 1: F = **74.701**, p < **0.001**
* Lag 2: F = **37.217**, p < **0.001**

The reverse relationship, SGE → LBMA, is not significant.

For **MCX → LBMA**:

* Lag 1: F = **10.658**, p = **0.001**
* Lag 2: F = **11.119**, p < **0.001**

However, the individual VAR coefficients later provide a more cautious interpretation of this relationship when all five markets are considered jointly.

---

# 6. Overall Interpretation of Granger Results

The Granger results do not support a simple chain such as:

**COMEX → LBMA → SGE → SHFE**

Instead, the five markets form a more complicated network.

The strongest directional evidence is concentrated around:

**COMEX → SHFE**

**COMEX → SGE**

**COMEX → LBMA**

**LBMA → SHFE**

**SGE → SHFE**

There is also meaningful interaction involving MCX, especially with SGE and SHFE. However, the evidence that MCX acts as an independent external source of price discovery is considerably less consistent.

Therefore, the Granger results suggest that **COMEX is the most consistently influential market in terms of short-run predictive transmission**, particularly toward SHFE, SGE and LBMA.

This does not mean that COMEX is proven to be the fundamental cause of every movement in these markets. The term "Granger causality" refers to predictive information contained in past observations, not economic causality in the strict sense.

---

# 7. Stationarity Test

Before estimating the VAR model, Augmented Dickey-Fuller (ADF) tests were performed on the five return series.

| Market | ADF Statistic |  p-value | Result     |
| ------ | ------------: | -------: | ---------- |
| SHFE   |        -6.424 |   <0.001 | Stationary |
| SGE    |        -7.539 |   <0.001 | Stationary |
| MCX    |       -12.396 |   <0.001 | Stationary |
| COMEX  |        -7.452 |   <0.001 | Stationary |
| LBMA   |        -5.348 | 0.000004 | Stationary |

All five p-values are below the 1% significance level.

Therefore, the null hypothesis of a unit root is rejected for every return series.

This means that the return series are stationary and can be used directly in the VAR analysis.

---

# 8. VAR Lag Selection

Several information criteria were used to determine an appropriate VAR lag length.

The results were:

* AIC → **3 lags**
* BIC → **1 lag**
* HQIC → **2 lags**
* FPE → **3 lags**

The information criteria therefore do not select exactly the same lag length.

BIC favours a more parsimonious VAR(1), while AIC and FPE favour VAR(3). HQIC lies between them at VAR(2).

The VAR(1) model was initially estimated because of its parsimony and because BIC selected one lag. However, residual diagnostic tests showed that residual autocorrelation remained. VAR(2), VAR(3) and VAR(4) were therefore examined.

VAR(3) was selected as the principal specification for the detailed dynamic analysis because it was supported by AIC/FPE and provided a richer representation of short-run dynamics, while remaining stable.

---

# 9. VAR(3) Stability

The estimated VAR(3) model satisfies the stability condition.

The stability test returned:

**VAR stability = True**

This means that the estimated VAR system is dynamically stable. In practical terms, shocks to the system do not cause the model to explode indefinitely. Instead, their effects gradually decline over time.

This property is important for interpreting impulse-response functions.

---

# 10. VAR(3) Results

The VAR model allows all five markets to be considered simultaneously. This is important because a pairwise Granger test considers only two markets at a time, while the VAR controls for the past returns of all five markets.

The main results are as follows.

## 10.1 SHFE equation

In the SHFE equation, the first lag of:

* SHFE is negative and significant: p = **0.000**
* SGE is positive and significant: p = **0.000**
* COMEX is positive and significant: p = **0.000**
* LBMA is positive and significant: p = **0.000**

The MCX coefficient is not significant at the first lag.

This indicates that SHFE returns are strongly related to previous returns in COMEX, SGE and LBMA after controlling for the other markets.

The COMEX effect is particularly important.

---

# 10.2 SGE equation

For SGE, the first lag of COMEX is positive and highly significant:

**COMEX L1 coefficient = 0.579545, p < 0.001**

The own lag of SGE is negative and significant.

The results therefore indicate a strong relationship between previous COMEX returns and current SGE returns.

This is consistent with the earlier Granger causality results.

---

# 10.3 MCX equation

The MCX equation is different.

The first lag of SHFE is positive and significant:

**0.242611, p = 0.006**

The first lag of SGE is negative and significant:

**−0.260916, p = 0.001**

However, the first lag of COMEX is not statistically significant:

**0.099920, p = 0.285**

This suggests that MCX has a strong relationship with other markets but does not behave as a simple market receiving a direct significant lagged effect from COMEX after all five markets are considered jointly.

---

# 10.4 COMEX equation

In the COMEX equation, the lagged SGE return is statistically significant:

**−0.210675, p = 0.020**

However, the coefficients for SHFE, MCX and LBMA are not statistically significant at the first lag.

This indicates some feedback from SGE to COMEX, which is consistent with the pairwise Granger result showing a statistically significant SGE → COMEX relationship.

---

# 10.5 LBMA equation

The LBMA equation shows a particularly strong relationship with COMEX.

The first lag of COMEX is:

**0.471324, p < 0.001**

The own lag of LBMA is:

**−0.348963, p < 0.001**

Thus, previous COMEX returns have a significant positive relationship with current LBMA returns.

This is consistent with the strong COMEX → LBMA Granger result.

---

# 11. Important Difference Between Pairwise Granger and VAR Results

One important point should be highlighted.

The pairwise Granger test found strong evidence for **MCX → SHFE**.

However, the individual first-lag MCX coefficient in the multivariate SHFE equation is not statistically significant.

This is not necessarily a contradiction.

The reason is that the two methods answer slightly different questions.

The pairwise Granger test asks whether MCX's past returns help predict SHFE when considering those two markets.

The VAR model asks whether MCX's past returns provide additional information for SHFE **after simultaneously controlling for SHFE, SGE, COMEX and LBMA**.

Therefore, the VAR result suggests that some of the apparent MCX → SHFE predictive relationship may overlap with information already contained in the other markets.

This is one reason why the study should not rank markets using a single statistical test.

---

# 12. Impulse-Response Analysis

Impulse-response functions were used to examine how the markets respond over time to shocks in another market.

The VAR(3) model was used for the main IRF analysis.

The strongest responses occurred after a shock to COMEX.

## COMEX shock

A one-unit innovation in COMEX generated the following Day-1 responses:

| Market responding | Day-1 response |
| ----------------- | -------------: |
| SHFE              |   **0.447906** |
| SGE               |   **0.638989** |
| MCX               |   **0.103980** |
| LBMA              |   **0.647351** |

The strongest Day-1 response was observed in LBMA, followed closely by SGE and SHFE.

This provides strong dynamic evidence that COMEX innovations are transmitted rapidly across the other major gold markets.

The response of SHFE is particularly important because the contemporaneous SHFE-COMEX correlation was very low at 0.062. The IRF therefore shows why same-day correlation alone can be misleading: information can be transmitted with a time delay because the markets operate during different trading sessions.

---

# 13. SGE Shock

A shock to SGE produces a positive Day-1 response in SHFE:

**SGE → SHFE = 0.228357**

At the same time, SGE shocks produce negative Day-1 responses in MCX, COMEX and LBMA.

The most important point here is not necessarily the sign of every response, but the fact that the SGE shock produces a meaningful response in SHFE.

This is consistent with the Granger result showing significant SGE → SHFE predictive transmission.

---

# 14. LBMA Shock

A shock to LBMA produces the following Day-1 responses:

* SHFE = **0.106972**
* SGE = **−0.090865**
* MCX = **0.089294**
* COMEX = **0.049535**

The response of SHFE is meaningful but smaller than the response generated by a COMEX shock.

This is consistent with the broader conclusion that COMEX has the strongest and most consistent short-run transmission effects in the system.

---

# 15. MCX Shock

MCX shocks generally produce relatively small Day-1 responses in the other markets.

For example:

* MCX → SHFE = **−0.046398**
* MCX → SGE = **−0.001675**
* MCX → COMEX = **−0.009629**
* MCX → LBMA = **−0.045929**

These effects are considerably smaller than the responses generated by a COMEX shock.

This provides further evidence against treating MCX as the dominant external source of price discovery.

---

# 16. Persistence of the Shocks

Most impulse responses become much smaller by Day 5 and approach zero by Day 10.

For example, following a COMEX shock:

* COMEX → SHFE: Day 1 = **0.447906**, Day 5 = **−0.022823**, Day 10 = **0.003951**
* COMEX → SGE: Day 1 = **0.638989**, Day 5 = **0.035123**, Day 10 = **−0.006234**
* COMEX → LBMA: Day 1 = **0.647351**, Day 5 = **0.038347**, Day 10 = **−0.007507**

Therefore, the effects of shocks are primarily short-lived.

This suggests that the five gold markets adjust relatively quickly to new information rather than maintaining large deviations for a long period.

It should be noted that IRF values represent responses to a one-unit innovation in the VAR return system. They should not be interpreted directly as percentage changes in market prices.

---

# 17. Forecast Error Variance Decomposition

FEVD was used to examine how much of the forecast uncertainty of each market can be associated with shocks originating in the different markets.

For the VAR(3) model using the original ordering, the 10-day decomposition was:

| Target |   SHFE |    SGE |    MCX |  COMEX |   LBMA |
| ------ | -----: | -----: | -----: | -----: | -----: |
| SHFE   | 42.83% | 14.40% | 23.57% | 16.77% |  2.42% |
| SGE    | 28.87% | 34.36% | 22.31% | 13.58% |  0.88% |
| MCX    |  5.53% |  9.25% | 80.42% |  4.24% |  0.55% |
| COMEX  |  6.01% | 11.49% | 51.50% | 30.73% |  0.27% |
| LBMA   |  6.31% |  8.91% | 31.33% | 17.44% | 36.02% |

These numbers show that each market retains a substantial amount of its own forecast variance, particularly MCX.

However, these results must be interpreted carefully.

The FEVD is based on an orthogonalization procedure, and the results are sensitive to the ordering of variables when a Cholesky decomposition is used.

This is especially important in this study because the residual correlations between some markets are very high. For example, the VAR residual correlation between MCX and COMEX is approximately **0.832**, while the correlation between COMEX and LBMA is approximately **0.799**.

When the variable ordering was changed, the FEVD contributions changed substantially.

Therefore, FEVD is used here as a **supporting diagnostic**, rather than as the sole method for determining which market is the price-discovery leader.

The study therefore does not conclude that MCX "causes" 51.5% of COMEX forecast variance merely because that percentage appears in one FEVD ordering.

---

# 18. VAR Diagnostic Tests

Several diagnostic tests were conducted to evaluate the VAR specification.

## 18.1 Residual autocorrelation

The Portmanteau test for VAR(1) gave:

* Test statistic = **344.2**
* p < **0.001**

Therefore, residual autocorrelation was present.

VAR(2) also rejected the null hypothesis of no residual autocorrelation:

* Statistic = **282.9**
* p < **0.001**

VAR(3) also showed residual autocorrelation:

* Statistic = **233.9**
* p = **0.002**

VAR(4) continued to reject the null:

* Statistic = **208.1**
* p = **0.001**

Therefore, increasing the number of lags does not completely eliminate the residual autocorrelation.

This suggests that the daily five-market system contains dynamics that are not completely captured by a small VAR specification.

However, the model remains stable, and the main transmission relationships are sufficiently consistent to support the use of VAR(3) as the primary dynamic specification.

---

# 19. Durbin-Watson Results

The Durbin-Watson statistics for the VAR(3) residuals were:

| Market | Durbin-Watson |
| ------ | ------------: |
| SHFE   |         2.014 |
| SGE    |         2.014 |
| MCX    |         2.006 |
| COMEX  |         1.997 |
| LBMA   |         1.994 |

These values are all close to 2.

This indicates that there is little evidence of strong first-order residual autocorrelation in the individual equations.

However, the multivariate Portmanteau test still detects higher-order or joint residual dependence.

Therefore, the Durbin-Watson results should be viewed as supplementary rather than as a replacement for the multivariate whiteness test.

---

# 20. Normality of Residuals

The VAR(3) residual normality test strongly rejects multivariate normality:

* Test statistic = **31,610**
* Degrees of freedom = **10**
* p < **0.001**

Thus, the residuals are not normally distributed.

This is not unusual for financial return data because financial returns often contain extreme observations, heavy tails and departures from normality.

Therefore, the non-normality result is reported as a limitation of the model rather than as a reason to completely reject the VAR analysis.

---

# 21. Robustness Test: Excluding the Extreme MCX Observation

The observation on 23 July 2024 was particularly unusual because MCX recorded a return of approximately −5.79%.

To determine whether this single observation was driving the main results, a robustness VAR(3) model was estimated after removing only this observation.

The original sample contained:

**376 observations**

The robustness sample contained:

**375 observations**

The robustness VAR(3) remained stable:

**VAR(3) robustness stability = True**

This is an important result.

---

# 22. Robustness Impulse Responses

The main COMEX transmission relationships remain strong after removing the extreme MCX observation.

| Shock → Response | Baseline Day 1 | Robustness Day 1 |
| ---------------- | -------------: | ---------------: |
| COMEX → SHFE     |       0.447906 |     **0.465437** |
| COMEX → SGE      |       0.638989 |     **0.591467** |
| COMEX → LBMA     |       0.647351 |     **0.600647** |
| SGE → SHFE       |       0.228357 |     **0.240823** |

The values are very similar in magnitude.

For example, the COMEX → SHFE response actually increases slightly from 0.447906 to 0.465437.

The COMEX → SGE and COMEX → LBMA responses decrease somewhat, but remain large.

The SGE → SHFE response also remains strong.

Therefore, removing the extreme MCX observation does not change the central interpretation of the study.

---

# 23. Robustness VAR Coefficients

The robustness model also continues to show strong relationships involving COMEX.

In the SHFE equation:

**L1 COMEX = 0.465437, p < 0.001**

In the SGE equation:

**L1 COMEX = 0.591467, p < 0.001**

In the LBMA equation:

**L1 COMEX = 0.600647, p < 0.001**

These results demonstrate that the major COMEX transmission relationships are not being produced solely by the extreme MCX observation.

The robustness analysis therefore increases confidence in the main findings.

---

# 24. Overall Interpretation of the Five-Market System

When all the results are considered together, the evidence does not support a simple linear chain of price discovery.

Instead, the five markets appear to form a **connected but asymmetric transmission network**.

The strongest and most consistent evidence is associated with COMEX.

COMEX shows:

1. Strong one-day lead-lag relationships with SHFE and SGE.
2. Strong Granger predictive relationships toward SHFE and SGE.
3. Strong Granger predictive relationship toward LBMA.
4. Large impulse responses in SHFE, SGE and LBMA.
5. Significant lagged coefficients in the SHFE, SGE and LBMA VAR equations.
6. Robust transmission effects even after removing the extreme MCX observation.

This makes COMEX the most consistently influential market in the short-run return-transmission analysis.

---

# 25. Role of LBMA

LBMA also plays an important role, especially in relation to SHFE.

The evidence for **LBMA → SHFE** is strong in the lead-lag analysis and Granger tests.

The one-day correlation is:

**0.664**

The Granger tests are highly significant at both one and two lags.

The VAR also shows a significant lagged LBMA coefficient in the SHFE equation.

Therefore, LBMA appears to be an important international source of information for SHFE.

However, the evidence for LBMA driving COMEX is weak.

Thus, LBMA should be viewed as an important transmission market rather than as an unquestioned intermediary between COMEX and the Asian markets.

---

# 26. Role of SGE

SGE has a particularly important relationship with SHFE.

The evidence for:

**SGE → SHFE**

is strong in the Granger tests and remains visible in the VAR and IRF results.

At the same time, SGE also has feedback with COMEX and MCX.

Therefore, SGE is not simply a passive receiver of international information.

It appears to function as an important regional transmission market within the Asian gold market network.

---

# 27. Role of MCX

MCX is highly connected to the international gold markets, especially COMEX.

The contemporaneous MCX-COMEX correlation is the highest in the sample:

**0.824**

However, high correlation does not automatically imply that MCX is a leading market.

The Granger and VAR evidence for MCX as an external source of price discovery is less consistent.

MCX has important relationships with SGE and SHFE, but the evidence that MCX predicts COMEX is weak.

Therefore, MCX should be described as a **highly interconnected market**, rather than as a dominant global price-discovery leader.

---

# 28. Important Time-Zone Limitation

One of the most important limitations of the daily analysis is that the five markets operate in different geographical time zones and trading sessions.

For example, the trading hours of COMEX, London, India and China do not completely overlap.

As a result, a relationship such as:

**COMEX at t−1 → SHFE at t**

may partly reflect the fact that COMEX closes after or at a different point in the global trading cycle than SHFE.

Therefore, the daily results should be interpreted as evidence of **predictive temporal precedence** rather than definitive economic causality.

A future extension using intraday data would allow the timing of information transmission to be examined more precisely.

---

# 29. Final Empirical Conclusion

The overall evidence indicates that the global gold markets are strongly interconnected, but the strength and direction of transmission differ across markets.

The most consistent evidence is found for **COMEX as a major source of short-run return transmission**.

COMEX significantly precedes SHFE, SGE and LBMA in predictive tests and generates relatively large impulse responses in these markets. The COMEX → SHFE relationship is particularly strong, despite the relatively low contemporaneous SHFE-COMEX correlation. This suggests that differences in trading sessions and information arrival times are important when examining international gold-market relationships.

LBMA and SGE also have important transmission roles. LBMA provides strong predictive information for SHFE, while SGE shows strong transmission toward SHFE and meaningful feedback with COMEX and MCX.

MCX is strongly interconnected with COMEX and the other markets, but the evidence is less consistent for MCX acting as an independent source of price discovery. Its high contemporaneous correlation with COMEX should therefore not be interpreted as proof that MCX leads COMEX.

The results also do not support a simple market sequence such as COMEX → LBMA → SGE → SHFE. Instead, the evidence points to a **network of asymmetric and partially bidirectional relationships**.

Finally, the robustness analysis shows that removing the unusually large MCX return on 23 July 2024 does not materially change the main transmission results. The VAR remains stable and the major COMEX → SHFE, COMEX → SGE, COMEX → LBMA and SGE → SHFE impulse responses remain strong.

Overall, the findings support the conclusion that **COMEX is the most consistently influential market in short-run global gold return transmission within the five-market system studied**, while recognizing that this conclusion represents predictive and dynamic evidence rather than definitive proof of causal price discovery. The different trading hours, residual autocorrelation, non-normal residuals and sensitivity of Cholesky FEVD to variable ordering should be considered when interpreting the results.
