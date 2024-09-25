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
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data = pd.read_csv('/content/weather_classification_data.csv')
print("FIRST FIVE ROWS:")
print(data.head())
result = seasonal_decompose(data['Temperature'], model='additive', period=12)
print("\nPLOTTING THE DATA:")
plt.figure(figsize=(10, 5))
plt.plot(data['Temperature'])
plt.title('Temperature Data (Sequential)')
plt.xlabel('Index')
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


![Screenshot 2024-09-25 083749](https://github.com/user-attachments/assets/548042c8-966d-4096-b72d-21165c479a8f)

PLOTTING THE DATA:

![plot data](https://github.com/user-attachments/assets/7fbf4f29-256f-406d-890a-c5fe3e458934)

SEASONAL PLOT REPRESENTATION :



![seasonal decomposition](https://github.com/user-attachments/assets/44a48193-5036-4537-be2e-cc772ae3949f)

TREND PLOT REPRESENTATION :

![trend decomposition](https://github.com/user-attachments/assets/93da1c77-9a74-4736-ad56-6f00df52b893)

OVERAL REPRESENTATION:

![overall](https://github.com/user-attachments/assets/e0f1dcff-9995-4353-8a9b-2a4a76dd5f26)




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
