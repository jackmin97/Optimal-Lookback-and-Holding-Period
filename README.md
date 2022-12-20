# Optimal-Lookback-and-Holding-Period
In this notebook, we will find an optimal lookback and holding period for different securities using correlation and p-value..

### 1. Read data from CSV file
First, we will import the necessary libraries and then, we will read the csv file with the different security prices using the 'read_csv' method of pandas.

### 2. Calculate correlation coefficient and p-value
We create a function and pass securities prices, lookback period and holding period as arguments. Inside the function, we do the following steps.

1. Calculate the lookback returns
2. Calculate the hold returns
3. Use pearsonr function from scipy library and pass lookback and hold returns to calculate correlation coefficient and p-value.

### 3. Plot correlation coefficient and p-value
We use heatmap to plot the values of correlation coefficient and p-value. The heatmap is a way of representing the data in a 2-dimensional form. The goal of the heatmap is to provide a colored visual summary of the data values.

To create heatmap, we use the seaborn library.

### 4. Optimal lookback and holding period
To calculate the correlation coefficient and p-value, we will do the following steps.

1. Define lookback and holding period
2. Create a dataframe which stores the price of a security
3. Create two arrays which store the values of correlation and p-value for different lookback and holding period
4. Call calc_corr function and pass security price, lookback and holding period as arguments

#### Plot correlation coefficient
We will call the plot_grid function to plot the correlation coefficient heatmap.

As you can observe in the heatmap, with each value of lookback and holding period, there is a value of correlation coefficient. For example, with holding period of 5 and lookback period of 360, the correlation coefficient is -0.025.

If the value of the correlation coefficient is highly positive between lookback(past) and hold(future) returns, then past and future returns are positively correlated. This means that if the past returns are positive, future returns are also positive, and if past returns are negative, future returns are also negative. Therefore, we will choose the highest positive correlation coefficient.

In the heatmap, you can see that holding period of 30 and lookback period of 30 has the highest correlation coefficient, that is 0.27. Therefore 0.27 is the optimal lookback and holding period for Crude oil.

#### Plot p-value
Now we will call plot_grid function to plot the p-value heatmap.

The p-value is used to confirm that the relationship between lookback and hold returns are not observed by chance. We will use p-value of 0.1 to reject the null hypothesis and conclude that the correlation is statistically significant. Therefore, only lookback and holding periods with p-value less than 0.1 should be considered.

Among all p-values less than 0.1, the maximum value of correlation is 0.27 (from correlation coefficient heatmap) for lookback period of 30 and holding period of 30.

### 5. Calculate Strategy Returns
We have found the optimal lookback and holding period for crude oil. Now, we will calculate strategy returns as done in the time series momentum strategy. The steps are:

1. Calculate returns over a lookback period
2. Calculate future returns over a holding period
3. Define strategy logic
3.1 Buy when lookback returns are greater than 0
3.2  Sell when lookback returns are less than 0
4. Calculate Strategy returns

The time series momentum strategy on Crude oil generated good returns over the backtesting period for optimal lookback of 30 days and hold of 30 days.

### 6. Optimal lookback and holding period for all securities
We will calculate the correlation coefficient and p-value for all securities that have high Hurst value.

#### Filter securities based on correlation coefficient and p-value
We will filter securities which have positive correlation and p-value less than 0.1. For correlation, only a positive sign is desired as it explains that both the returns moved in the same direction. Thus there is no threshold for the correlation.

#### Lookback and hold period with the highest correlation
We will keep only those lookback and holding period for securities which have the highest correlation.

### 7. Calculate strategy returns for all securities
The strategy performed pretty well on the securities with high correlation between lookback and holding returns.
