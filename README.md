### Developed by: KANISHKAR M
### Register Number: 212222240044
### Date :

# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on Water temperature for water quality data.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.

### PROGRAM:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```
```py
file_path = '/content/waterquality.csv'
data = pd.read_csv(file_path)
```

```py
data['Date'] = pd.to_datetime(data['Date'])  # Convert 'date' to datetime
data.set_index('Date', inplace=True)  # Set 'date' as index
data.fillna(method='ffill', inplace=True)  # Forward fill missing values
```

```py
watertemp_data = data['WaterTemp (C)']
```
```py
# Plot Original Data for WaterTemp (C)
plt.figure(figsize=(14, 8))
plt.plot(watertemp_data, label='WaterTemp (C)')
plt.title('Original WaterTemp (C) Data')
plt.legend()
plt.show()
```
```py
# Regular Differencing for WaterTemp (C)
watertemp_diff = watertemp_data.diff().dropna()
```
```py
# Plot Differenced Data for WaterTemp (C)
plt.figure(figsize=(14, 8))
plt.plot(watertemp_diff, label='WaterTemp (C) (Diff)')
plt.title('Differenced WaterTemp (C) Data')
plt.legend()
plt.show()
```
```py
# Log Transformation for WaterTemp (C)
watertemp_log = np.log(watertemp_data + 1)  # Adding 1 to avoid log(0)
```
```py
# Plot Log-Transformed Data for WaterTemp (C)
plt.figure(figsize=(14, 8))
plt.plot(watertemp_log, label='WaterTemp (C) (Log)')
plt.title('Log-Transformed WaterTemp (C) Data')
plt.legend()
plt.show()
```
```py
# Seasonal Adjustment (using moving average) for WaterTemp (C)
watertemp_seasonal_adjustment = watertemp_log - watertemp_log.rolling(window=7).mean()
watertemp_seasonal_adjustment.dropna(inplace=True)
```
```py
plt.figure(figsize=(14, 8))
plt.plot(watertemp_seasonal_adjustment, label='WaterTemp (C) (Seasonally Adjusted)')
plt.title('Seasonally Adjusted Log-Transformed WaterTemp (C) Data')
plt.legend()
plt.show()
```

### OUTPUT:

![image](https://github.com/user-attachments/assets/5470a9db-1ca0-4cb9-b910-7cb00fec02d4)



REGULAR DIFFERENCING:

![image](https://github.com/user-attachments/assets/d06f564f-7be9-4146-a561-33de4b7fe386)

SEASONAL ADJUSTMENT:

![image](https://github.com/user-attachments/assets/a1e326e2-7846-46f0-9e16-589547163702)


LOG TRANSFORMATION:

![image](https://github.com/user-attachments/assets/41ba288d-ba31-446c-a68b-53d7c70a3240)


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on Water Quality data.

