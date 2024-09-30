# NAME: Pranave B
# REG NO: 212221240040
# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('WMT.csv')

# Convert 'Date' to datetime format and set it as the index
df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)

# Extract the 'Adj Close' column and drop NaN values
adj_close = df['Adj Close'].dropna()

# Compute the mean and variance of the data
data_mean = np.mean(adj_close)
data_var = np.var(adj_close)

# Normalize the data
normalized_data = (adj_close - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')

# Take only the positive lags
acf_result = acf_result[len(acf_result)//2:]

# Plot the ACF for the first 35 lags
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36], use_line_collection=True)
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) for Adjusted Close Prices')
plt.show()
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/2359b5ae-b10c-4b5e-aad2-80ee719bac7c)

### RESULT:
Thus ,the auto correlation function in python is implemented successfully.
