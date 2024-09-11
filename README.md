# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
# Name : Divakar R
# Register number : 212222240026
# Date: 

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

import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load the DataSet
power_consumption = pd.read_csv('powerconsumption.csv')

# Convert the 'Date' column to datetime format
power_consumption['Datetime'] = pd.to_datetime(power_consumption['Datetime'])

# Set the 'Date' column as the index
power_consumption.set_index('Datetime', inplace=True)

# Print the columns of the DataFrame to check their exact names
print(power_consumption.columns)

# Calculate mean and variance of the 'Temperature' column
price_data = power_consumption['Temperature'] # Assign the 'Temperature column to price_data
mean_price = np.mean(price_data)
var_price = np.var(price_data)

# Normalize the data (subtract mean and divide by standard deviation)
normalized_price = (price_data - mean_price) / np.sqrt(var_price)

# Compute the ACF for the first 35 lags
lags = range(35)
acf_values = [np.corrcoef(normalized_price[:-lag], normalized_price[lag:])[0, 1] if lag != 0 else 1 for lag in lags]

# Plot the ACF results
plt.figure(figsize=(10, 6))
plt.stem(lags, acf_values, use_line_collection=True)
plt.title('Autocorrelation Function (ACF) for Gold price')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.grid(True)
plt.show()

```

### OUTPUT:
![download](https://github.com/user-attachments/assets/ff0ca5b9-4d61-4dd3-96e6-d8c4ff53a061)




### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
