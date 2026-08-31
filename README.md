# Empirical Analysis of Corporate Disclosure Timing and Market Response

An empirical study of whether Korean listed firms systematically release unfavorable earnings information after market hours and how disclosure timing is associated with subsequent stock-price reactions.

## Full Interactive Analysis

For the complete analysis, including Python code, methodology, statistical tests, regression results, and visualizations:

[**View Full Interactive Analysis**](https://chaeyeonlee01.github.io/corporate-disclosure-timing-market-response/)

---

## Project Overview

Corporate disclosures affect not only what information reaches investors, but also when that information becomes available to the market. This project investigates whether unfavorable earnings disclosures are disproportionately released after market hours and whether disclosure timing is associated with differences in subsequent market reactions.

Using minute-level disclosure timestamps from Korea's DART system, the analysis combines disclosure records with firm-level stock prices and market indices to examine disclosure-timing patterns, abnormal returns, price-adjustment mechanisms, firm-level timing persistence, and industry-level differences.

### Research Questions

1. Are bad-news earnings disclosures more likely to be released after market hours than good-news disclosures?
2. How do abnormal stock returns differ across news type and disclosure timing?
3. What firm- and disclosure-level characteristics predict after-hours disclosure?
4. How are post-disclosure returns divided between overnight price gaps and intraday price adjustment?
5. Do firms exhibit persistent disclosure-timing behavior?
6. How do disclosure frequency and market impact differ across industries?

---

## Data

| Item | Description |
|---|---|
| **Core sample** | 7,978 earnings disclosures |
| **Firms** | 530 KOSPI/KOSDAQ-listed firms |
| **Main disclosure period** | 2019 Q1 – 2025 Q4 |
| **Stock-price coverage** | July 2018 – April 2026 |
| **Unit of analysis** | Firm-disclosure event |
| **Disclosure source** | DART OpenAPI and web scraping |
| **Market data** | FinanceDataReader |
| **Timing resolution** | Minute-level disclosure timestamps |

---

## Methodology

### 1. Data Collection and Preprocessing

- Built an automated pipeline integrating DART OpenAPI, web scraping, and FinanceDataReader.
- Collected and standardized earnings-related disclosures and firm-level market data.
- Engineered minute-level disclosure timestamps.
- Classified disclosures by news type and intraday/after-hours timing.

### 2. Disclosure-Timing Analysis

- Compared after-hours disclosure frequencies across good-news and bad-news events.
- Examined timing patterns across firms, markets, years, and industries.
- Applied statistical tests to evaluate differences in disclosure behavior.

### 3. Event Study

- Estimated expected returns using the **Market Model**.
- Calculated abnormal returns and **Cumulative Abnormal Returns (CAR)** around disclosure events.
- Compared market reactions across:
  - Good News – Intraday
  - Good News – After-hours
  - Bad News – Intraday
  - Bad News – After-hours

### 4. Price-Adjustment Decomposition

Post-disclosure returns were decomposed into:

- **Overnight gap:** previous close → next-day open
- **Intraday continuation:** next-day open → next-day close

This decomposition was used to examine when disclosure information is incorporated into stock prices.

### 5. Two-Stage Regression Framework

**Stage 1 — Logistic Regression**

Estimated the probability of after-hours disclosure using variables including:

- Bad-news status
- Bad-news severity
- Firm size
- Market classification
- Friday indicator
- Historical after-hours disclosure ratio

**Stage 2 — OLS Regression**

Examined the relationship between disclosure timing and abnormal returns while controlling for firm and disclosure characteristics.

### 6. Industry-Level Analysis

Compared industries using:

- Disclosure frequency
- After-hours disclosure frequency
- Bad-news concentration
- Market impact

These measures were used to construct an exploratory industry-level disclosure-risk framework.

---

## Key Findings

- **Bad-news disclosures were more concentrated after market hours:** 46.9% of bad-news disclosures occurred after hours, compared with 38.4% of good-news disclosures.
- Firms exhibited **persistent disclosure-timing behavior**, with historical after-hours disclosure patterns strongly associated with future timing choices.
- **Bad-news status** was associated with a higher probability of after-hours disclosure.
- Event-study results showed differences in abnormal returns across news-type and disclosure-timing groups.
- After controlling for other factors, the **Bad News × After-hours interaction was not statistically significant**, providing no evidence that bad news received an additional abnormal-return penalty specifically because it was disclosed after hours.
- Price decomposition showed that post-disclosure adjustment could be separated into **overnight-gap** and **intraday-continuation** components.
- Disclosure patterns and market impact varied across industries.

> **Interpretation note:** The empirical results should be interpreted as conditional associations rather than definitive causal effects.

---

## Tools and Techniques

**Programming & Data Processing**
- Python
- pandas
- NumPy
- Web Scraping
- DART OpenAPI
- FinanceDataReader

**Statistical Analysis**
- Market Model
- Event Study
- Cumulative Abnormal Returns (CAR)
- Chi-square Tests
- t-tests
- Kruskal-Wallis Tests
- Logistic Regression
- OLS Regression

**Visualization**
- Matplotlib
- Statistical and financial data visualization
