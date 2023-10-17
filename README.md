# EX-no-10-Holt-Winters-method
# AIM:
To implement the holt winters method using python program

# Procedure:
1.Import necessary libraries , Matplotlib for plotting, and Pandas for data handling.

2.Create an Exponential Smoothing model (Holt-Winters) using statsmodels. Configure the model with trend and seasonal components.

3.Creating a time series plot with a specified time range that includes the forecast.

4.Generate a long-term forecast by forecasting future values for the entire time series.

# Program:
```
python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.api import ExponentialSmoothing, SimpleExpSmoothing, Holt
airline  = pd.read_csv('/content/AirPassengers.csv',index_col='Month',parse_dates=True)
airline.index.freq = 'MS'
airline.index
airline.tail()
len(airline)
train_airline = airline[:108]
test_airline = airline[108:]
len(test_airline)
fitted_model = ExponentialSmoothing(train_airline['#Passengers'],trend='mul',seasonal='mul',seasonal_periods=12).fit()
test_predictions = fitted_model.forecast(36).rename('HW Test Forecast')
test_predictions[:10]
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
plt.title('Train and Test Data');
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
test_predictions.plot(legend=True,label='PREDICTION')
plt.title('Train, Test and Predicted Test using Holt Winters');
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
test_predictions.plot(legend=True,label='PREDICTION',xlim=['1958-01-01','1961-01-01']);
from sklearn.metrics import mean_absolute_error,mean_squared_error
print(f'Mean Absolute Error = {mean_absolute_error(test_airline,test_predictions)}')
print(f'Mean Squared Error = {mean_squared_error(test_airline,test_predictions)}')
test_airline.describe()
final_model = ExponentialSmoothing(airline['#Passengers'],trend='mul',seasonal='mul',seasonal_periods=12).fit()

forecast_predictions = final_model.forecast(steps=36)
airline['#Passengers'].plot(figsize=(12,8),legend=True,label='Current Airline Passengers')
forecast_predictions.plot(legend=True,label='Forecasted Airline Passengers')
plt.title('Airline Passenger Forecast');
```
# Output:
airline.index:

![275251596-3e9d4d66-2676-4273-aed5-ecbe3f83e5f0](https://github.com/naramala-niharika/exp-10/assets/94165377/77281ec5-e47d-4790-85ed-bd4082822301)


airline.tail():

![275251726-675107e1-e371-44a1-8329-569626bfce72](https://github.com/naramala-niharika/exp-10/assets/94165377/e2e25967-d0e3-4194-8ae8-87316857c63c)


len(airline):

![275252544-25fa7ece-823a-42dc-b5fb-6f8f457f560a](https://github.com/naramala-niharika/exp-10/assets/94165377/62b53735-d194-4175-845f-4cab87339826)


len(test_airline):

![275252330-62b9448f-fc9c-4536-9f05-e97186b25cd7](https://github.com/naramala-niharika/exp-10/assets/94165377/d4d4dfd1-b6f6-439b-be6c-7a4a36c2cb92)


test_predictions[:10]:

![275252993-0b36516f-11df-42f3-8a0d-b7e420b435eb](https://github.com/naramala-niharika/exp-10/assets/94165377/bade8db0-b050-4fd9-8772-0b293ce7c894)


Train and Test Data Graph:

![275253902-6443beb2-577c-4773-a677-40e5efdc92cc](https://github.com/naramala-niharika/exp-10/assets/94165377/550521ea-5f6b-47d4-821d-d4d802c98008)


Train, Test and Predicted Test using Holt Winters graph:

![275254287-9b28465b-ea03-42f9-b0d9-ba0f2f9d2e6a](https://github.com/naramala-niharika/exp-10/assets/94165377/d823e657-2b73-4582-a4a5-43665f18e480)


Prediction Graph:

![275254754-188cea63-4669-468f-999d-c5fa46096680](https://github.com/naramala-niharika/exp-10/assets/94165377/f37afcd5-98c0-4bb8-adc1-f4f182d6aa1c)


Mean Absolute Error:

![275255004-148075be-7024-4cb0-936d-8314acf2d2c5](https://github.com/naramala-niharika/exp-10/assets/94165377/6a29c25b-f21b-40fb-b5c1-d41a62a0a571)


Mean Squared Error:

![275255229-7a9c6ca2-4040-4af9-a3fd-97b68c5d3aca](https://github.com/naramala-niharika/exp-10/assets/94165377/6903df88-f676-481b-9483-6e0375c6caa7)


test_airline.describe():

![275255422-e2f2932e-ce13-45c6-81eb-3e55bf6d2f46](https://github.com/naramala-niharika/exp-10/assets/94165377/ec4f0680-1e30-45e6-bf3c-a389218ce6bb)


Airline Passenger Forecast Graph:

![275255685-558067cc-1480-4b33-b31b-8f7a42f211ad](https://github.com/naramala-niharika/exp-10/assets/94165377/fda64fca-8894-47cc-9681-089c8f14426a)


# Result:
Thus the program to implement holt winters method is written and verified using python programming.
