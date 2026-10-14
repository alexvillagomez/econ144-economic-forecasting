# Econ 144: Economic Forecasting in R

My problem sets and projects from Econ 144 (Economic Forecasting) at UCLA, Winter 2026. The course follows Gonzalez-Rivera's *Forecasting for Economics and Business* and Hyndman and Athanasopoulos's *Forecasting: Principles and Practice*, and all of the work is in R Markdown.

All of the work here is my own. Each folder has the `.Rmd` source and the knitted PDF, which has the code, output, plots, and my written answers together. The PDFs are the easiest way to read through it.

## Problem sets

The problem sets build up from descriptive time-series work to ARIMA, cointegration, volatility models, and dynamic regression.

**HW1: Growth rates, distributed lags, and seasonal adjustment** — [PDF](homework/hw1/hw1.pdf) · [source](homework/hw1/hw1.Rmd)

Quarterly real GDP growth vs. S&P 500 returns since 2000 (summary statistics, correlation test, distributed-lag regressions with `dynlm`), poverty vs. unemployment, and real consumption vs. disposable income growth from FRED. Also covers stationarity and log-differencing, `tsibble` work on Australian tourism data, and STL, X-11, and SEATS seasonal adjustment.

**HW2: Forecast efficiency, MA processes, and decomposition** — [PDF](homework/hw2/hw2.pdf) · [source](homework/hw2/hw2.Rmd)

Tests whether the Fed's Greenbook GDP forecasts are efficient by regressing forecast errors on their own lags. Compares theoretical and sample ACFs of a simulated MA(2), works through MA forecasts and invertibility by hand, fits an AR(1) to stock returns, and forecasts with classical decomposition and STL, checked with Ljung-Box tests and train/test accuracy.

**HW3: AR model selection and ARIMA** — [PDF](homework/hw3/hw3.pdf) · [source](homework/hw3/hw3.Rmd)

AR(p) selection by AIC and BIC on weekly 1-year Treasury yields from 1962 to 2009, with residual diagnostics, recursive residuals, and CUSUM. Also CPI forecasting with ARIMA, persistence of simulated AR/MA/ARMA processes, seasonal ARIMA, ARIMA forecasts computed by hand, and seasonal differencing.

**HW4: Cointegration and volatility** — [PDF](homework/hw4/hw4.pdf) · [source](homework/hw4/hw4.Rmd)

Cointegration between log GDP and consumption (ADF, Engle-Granger, Johansen) and a test of purchasing power parity between the US and Germany. Simulates ARCH(4) and low- vs. high-persistence GARCH(1,1) processes with `rugarch`, then fits and forecasts an ARMA(2,2)-GARCH(2,2) on S&P 500 returns for 2000-2010 vs. 2015-2025.

**HW5: Dynamic regression and harmonic models** — [PDF](homework/hw5/hw5.pdf) · [source](homework/hw5/hw5.Rmd)

Dynamic regression with a piecewise trend and ARIMA errors on Australian accommodation takings, Fourier-term regression with a search over the number of harmonics on US gasoline supply, dynamic harmonic regression on retail turnover, STL-ETS vs. harmonic regression on hourly pedestrian counts, and a comparison of neural network (NNETAR), ARIMA, and ETS forecasts.

## Projects

Three open-ended projects where I picked the data and built the full forecasting workflow.

**Project 1: US electricity prices** — [PDF](projects/project1/project1.pdf) · [source](projects/project1/project1.Rmd)

Monthly average US electricity price per kWh from FRED, 1978 to 2025. Linear vs. quadratic trend models compared with residual checks, ANOVA, and AIC/BIC; additive STL vs. multiplicative decomposition; seasonal factors (prices peak June through September); and a 12-month forecast.

**Project 2: Google Trends flu searches** — [PDF](projects/project2/project2.pdf) · [source](projects/project2/project2.Rmd)

Monthly Google search interest in "flu" and "flu symptoms", 2004 to 2026. STL, ETS, recursive residuals and CUSUM, ETS vs. `auto.arima` on a 12-month holdout, an ETS-ARIMA forecast combination, and a VAR(2) with impulse responses and Granger causality tests.

**Project 3: MLB payroll and wins** — [PDF](projects/project3/project3.pdf) · [source](projects/project3/project3.Rmd)

Total MLB payroll from 2006 to 2025, forecast with ARIMA, ETS, NNETAR, and Prophet and compared by test-set MAPE, then combined into an equal-weight forecast for 2026. Also a regression of team wins on payroll and dynamic regressions for Padres wins on lagged OPS, ERA, and payroll.

## Running it

Each `.Rmd` knits from its own folder and reads data from [data/](data/), which has the FRED series and textbook exercise files the assignments use. Stock prices are pulled from Yahoo Finance with `quantmod`, with end dates pinned so reruns match the PDFs.

Packages: tidyverse, readxl, tseries, forecast, fpp2, fpp3 (tsibble, fable, feasts), seasonal, dynlm, quantmod, tidyquant, gridExtra, strucchange, urca, rugarch, vars, forecastHybrid, prophet, and fable.prophet. Knitting to PDF also needs a LaTeX install.

## Layout

```
homework/   hw1 ... hw5, each with hwN.Rmd and hwN.pdf
projects/   project1 ... project3, each with projectN.Rmd and projectN.pdf
data/       input data for the assignments
```
