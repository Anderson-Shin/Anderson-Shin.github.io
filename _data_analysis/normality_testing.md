/Users/mino/Desktop/깃헙블로그/posts/Data science/normality test/Daily return times series.png

# Normality testing using python

```python
# Import necessary libraries.
import yfinance as yf
import pandas as pd
import scipy.stats as stats
import matplotlib.pyplot as plt

# Define the ticker symbol which you are interested in.
tickerSymbol = 'MSFT'

# Use yfinance to fetch the data.
tickerData = yf.Ticker(tickerSymbol)

# Fetch the data for a specific period. For instance, if you want to fetch the data for the last 5 years, do as follows:
df = tickerData.history(period='5y', interval = '1d')

# Calculate the daily return for the 'Close' column.
df['Return'] = df['Close'].pct_change()

# Plot the rate of return.
plt.figure(figsize=(14, 7))
plt.plot(df['Return'])
plt.title('Rate of Return Over Time')
plt.show()
```

![Daily%20return%20times%20series.png](https://github.com/Anderson-Shin/anderson-shin.github.io/blob/master/images/Daily%20return%20times%20series.png?raw=true)

```python
# Plot the histogram of returns and the normal distribution.
plt.figure(figsize=(14, 7))
plt.hist(df['Return'].dropna(), bins=100, density=True, alpha=0.75)

mu, std = stats.norm.fit(df['Return'].dropna())
xmin, xmax = plt.xlim()
x = np.linspace(xmin, xmax, 100)
p = stats.norm.pdf(x, mu, std)
plt.plot(x, p, 'k', linewidth=2)
plt.title("Normal Distribution Fit")
# plt.savefig("Normal distribution fit")
plt.show()

```

![Normal%20distribution%20fit.png](https://github.com/Anderson-Shin/anderson-shin.github.io/blob/master/images/Normal%20distribution%20fit.png?raw=true)

```python
# Conduct the Jarque-Bera test
jb_test = stats.jarque_bera(df['Return'].dropna())

print(f"JB statistic: {jb_test[0]}, p-value: {jb_test[1]}")

# Get the critical value from the chi-squared distribution
chi2_critical_value = stats.chi2.ppf(0.95, df=2)  # 95% confidence level

print(f"Chi-squared statistic at 95% confidence level: {chi2_critical_value}")

# Compare the JB statistic with the chi-squared statistic
if jb_test[0] > chi2_critical_value:
    print("The JB statistic is greater than the chi-squared statistic. We reject the null hypothesis.")
else:
    print("The JB statistic is less than the chi-squared statistic. We fail to reject the null hypothesis.")

```

![Normal%20Q-Q%20Plot.png](https://github.com/Anderson-Shin/anderson-shin.github.io/blob/master/images/Normal%20Q-Q%20Plot.png?raw=true)