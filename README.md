# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for weather classification.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:

```

import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data = pd.read_csv('/content/weather_classification_data.csv')
print("FIRST FIVE ROWS:")
print(data.head())
data = data.head(120)  # Adjust this number as per your dataset's requirement
data['Date'] = pd.date_range(start='1/1/2010', periods=len(data), freq='M')
data.set_index('Date', inplace=True)
result = seasonal_decompose(data['Temperature'], model='additive', period=12)
print("\nPLOTTING THE DATA:")
plt.figure(figsize=(10, 5))
plt.plot(data['Temperature'])
plt.title('Monthly Average Temperature Over Time')
plt.xlabel('Date')
plt.ylabel('Temperature')
plt.show()
print("\nSEASONAL PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.seasonal.plot()
plt.title('Seasonal Decomposition')
plt.ylabel('Seasonal Component')
plt.show()
print("\nTREND PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.trend.plot()
plt.title('Trend Decomposition')
plt.ylabel('Trend Component')
plt.show()
print("\nOVERALL REPRESENTATION:")
fig, (ax1, ax2, ax3, ax4) = plt.subplots(4, 1, figsize=(10, 10))
result.observed.plot(ax=ax1)
ax1.set_ylabel('Observed')
result.trend.plot(ax=ax2)
ax2.set_ylabel('Trend')
result.seasonal.plot(ax=ax3)
ax3.set_ylabel('Seasonal')
result.resid.plot(ax=ax4)
ax4.set_ylabel('Residual')
plt.tight_layout()
plt.show()
```

### OUTPUT:
FIRST FIVE ROWS:

![Screenshot 2024-09-17 210857](https://github.com/user-attachments/assets/77ca7d15-9da2-4a64-a1cb-92261a205df7)


PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/1414d633-f9f2-4c66-b497-461fb9e5c166)

SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/2d247834-32c2-455c-93c3-34622ed70493)


TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/3820cd53-524e-44ac-850f-9e8d177822c6)

OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/eb0dcdd0-d86e-405f-8c6b-e55bf1c19ddb)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
