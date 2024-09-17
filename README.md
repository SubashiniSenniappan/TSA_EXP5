# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:

```
# Import required packages
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Read the dataset
data = pd.read_csv('/content/weather_classification_data.csv')

# Display the first five rows of the dataset
print("FIRST FIVE ROWS:")
print(data.head())

# Reduce the size of the data for time series purposes (if needed)
# Let's restrict the dataset to the first 120 rows for 10 years of monthly data (adjust based on actual data size)
data = data.head(120)  # Adjust this number as per your dataset's requirement

# Create a DateTime index with a valid range
data['Date'] = pd.date_range(start='1/1/2010', periods=len(data), freq='M')

# Set Date column as index
data.set_index('Date', inplace=True)

# Perform decomposition on the Temperature column
result = seasonal_decompose(data['Temperature'], model='additive', period=12)

# PLOT THE DATA:
print("\nPLOTTING THE DATA:")
plt.figure(figsize=(10, 5))
plt.plot(data['Temperature'])
plt.title('Monthly Average Temperature Over Time')
plt.xlabel('Date')
plt.ylabel('Temperature')
plt.show()

# SEASONAL PLOT REPRESENTATION:
print("\nSEASONAL PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.seasonal.plot()
plt.title('Seasonal Decomposition')
plt.ylabel('Seasonal Component')
plt.show()

# TREND PLOT REPRESENTATION:
print("\nTREND PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.trend.plot()
plt.title('Trend Decomposition')
plt.ylabel('Trend Component')
plt.show()

# OVERALL REPRESENTATION (Observed, Trend, Seasonal, Residual):
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



PLOTTING THE DATA:


SEASONAL PLOT REPRESENTATION :



TREND PLOT REPRESENTATION :

OVERAL REPRESENTATION:



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
