# Bitcoin vs. Traditional Assets: Efficient Frontier and Correlation Analysis

## Overview

This project examines Bitcoin's diversification benefits compared to traditional assets (like S&P 500, bonds, gold, and other commodities) using the efficient frontier approach and correlation analysis. By analyzing the relationship between Bitcoin and these assets, we explore its potential role in portfolio optimization.

## Table of Contents

- [Project Structure](#project-structure)
- [Installation](#installation)
- [Data Sources](#data-sources)
- [Methodology](#methodology)
  - [Data Collection](#data-collection)
  - [Efficient Frontier Calculation](#efficient-frontier-calculation)
  - [Correlation Analysis](#correlation-analysis)
- [Results](#results)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Project Structure

```
bitcoin-vs-traditional-assets/
├── data/                  # Raw and processed data files
├── figures/               # Plots and charts
├── README.md              # Project documentation
├── .gitignore             # Files and directories to ignore in git
├── requirements.txt       # Required packages
└── Modulo_S.2_Bitcoin_vs_Gold_FINTECH.ipynb  # Main notebook with code
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/bitcoin-vs-traditional-assets.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Data Sources

Data is downloaded from Yahoo Finance, covering:
- **Equity**: S&P 500 (`^GSPC`)
- **Bonds**: Aggregate Bond Index (`AGG`)
- **Cryptocurrency**: Bitcoin (`BTC-USD`)
- **Gold**: (`GC=F`)
- **Additional Assets**: Crude Oil (`CL=F`), Dollar Index (`DX-Y.NYB`), Treasury Bonds (`TLT`), and Apple Stock (`AAPL`)

## Methodology

### Data Collection

Historical adjusted closing prices are retrieved from Yahoo Finance. Daily returns are computed using logarithmic returns:
\[
R_t = \ln \left( \frac{P_t}{P_{t-1}} \right)
\]
where \( P_t \) is the price at time \( t \) and \( P_{t-1} \) is the price at time \( t-1 \).

### Efficient Frontier Calculation

The efficient frontier represents optimal portfolios that offer the highest expected return for a given level of risk. We calculate portfolios with varying weight allocations among the assets and plot the efficient frontier.

#### Steps:

1. **Portfolio Returns**:
   Portfolio return \( \mu_p \) is calculated as:
   \[
   \mu_p = \sum_{i=1}^n w_i \mu_i
   \]
   where \( w_i \) is the weight of asset \( i \) and \( \mu_i \) is the mean return of asset \( i \).

2. **Portfolio Risk (Standard Deviation)**:
   Portfolio risk \( \sigma_p \) is calculated as:
   \[
   \sigma_p = \sqrt{\sum_{i=1}^n \sum_{j=1}^n w_i w_j \sigma_{ij}}
   \]
   where \( \sigma_{ij} \) is the covariance between asset \( i \) and asset \( j \).

3. **Sharpe Ratio**:
   The Sharpe Ratio \( S \) is calculated to assess risk-adjusted returns:
   \[
   S = \frac{\mu_p}{\sigma_p}
   \]
   Higher Sharpe Ratios indicate more desirable portfolios.

4. **Optimization**:
   Using Monte Carlo simulations with 10,000 random portfolios, we identify portfolios on the efficient frontier and the portfolio with the maximum Sharpe Ratio.

#### Efficient Frontier Visualization

The efficient frontier is visualized by plotting the standard deviation against returns for each portfolio, with color indicating the Sharpe Ratio.

### Correlation Analysis

To assess Bitcoin's role as a diversifier, we compute and visualize the correlation matrix between Bitcoin and traditional assets over the last decade.

1. **Daily Returns**: 
   Daily percentage returns are computed as:
   \[
   R_t = \frac{P_t - P_{t-1}}{P_{t-1}}
   \]

2. **Correlation Matrix**:
   The correlation matrix provides insights into the co-movement between Bitcoin and other assets. Values close to 1 indicate a strong positive correlation, whereas values close to -1 indicate a strong negative correlation.

#### Correlation Matrix Visualization

The correlation matrix is visualized using a heatmap, where colors represent the strength of correlations. The results illustrate Bitcoin's unique relationship with traditional assets, potentially serving as a diversification tool.

## Results

### Portfolio Optimization

1. **Efficient Frontier Plot**: Displays the risk-return trade-off for optimal portfolios.
2. **Max Sharpe Ratio Portfolio**: Highlights the portfolio with the best risk-adjusted return.

### Correlation Analysis

The correlation matrix illustrates Bitcoin’s relatively low correlation with traditional assets, supporting its potential as a diversifier in a portfolio.

#### Example Outputs

1. **Efficient Frontier Plot**
   ![Efficient Frontier](figures/efficient_frontier.png)

2. **Correlation Matrix Heatmap**
   ![Correlation Matrix](figures/correlation_matrix.png)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- **Yahoo Finance** for providing financial data.
- **Pandas, NumPy, Matplotlib, and SciPy** for data handling and visualization.
