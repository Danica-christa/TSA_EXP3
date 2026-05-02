# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 2/5/26

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
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv('NFLX.csv')

# Store OPEN values in 'data'
data = df['Open'].values

# Parameters
N = len(data)
lags = range(35)

autocorr_values = []

mean_data = np.mean(data)
variance_data = np.var(data)

# ACF calculation
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# Plot
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)

plt.title('Autocorrelation of Open Values')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')

plt.grid(True)
plt.show()
```
### OUTPUT:

<img width="1124" height="673" alt="image" src="https://github.com/user-attachments/assets/5f75e237-09d9-4218-9b8c-1161ae04a122" />


### RESULT:
Thus we have successfully implemented the auto correlation function in python.
