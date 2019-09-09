# Car_Breakdown_prediction
Car breakdown prediction for every unique vehicleId to happened within 30 days.
# Car_breakdown_prediction
Car breakdown prediction for every unique vehicleId to happened within 30 days.

**1• Eco mode-** In this mode small amount of fule is injected in the engine at longer interval of time, which results in good fuel economy at the expense of reduced pick up/performance.

**2• City mode-** In this mode is like "jogging" mode, in this mode there is a perfect balance between performance and fuel consumption.

**3• Sports mode-** In this mode is similar to "running" mode, you will get increased performance  at an  expense of increased fuel consumption.


### •	Step 1: Understanding data
### •	Step 2: EDA
### •	Step 3: Data preparation and feature engineering
### •	Step 4: Train and evaluate model
### •	Step 5: Prediction

Source data
Its takes three datasets as inputs.
**•	Training data:** It is each Vehicalid engine run-to-failure data.
**•	Testing data:** It is the Vehicalid engine operating data without failure events recorded.
**•	Ground truth test data:** It contains the information of Remaining Useful Day(RUL)  for a particular vehicleId in the testing data.

### Prepare the traning&testing data
In this section we will summarize the process of preparing the **test data** and explain relevant issues. The testing data is prepared mainly from two datasets, where the data from the second Reader module ("test_data") is used to generate aggregate features, and the data from the third Reader module ("test_truth_data") is used to generate labels.
Similar to the **training data**, the time series data in the testing data helps to generate aggregate features during the feature engineering process. Instead of having all time series data in the testing data, we only keep the the record with the maximum days for each Vehicle id. In other words, one record is retained for each Vehicle id. Eventually, the testing data contains 100 records, which matches the RUL in the ground truth data.

### Feature engineering
Another important task to generate training and testing features. The feature engineering process on the training and testing datasets respectively.
The features that are included or created in the training data can be grouped into two categories. 
•	Selected raw features
•	Aggregate features
Selected raw features The raw features are those that are included in the original input data. In this data, all the sensor measurements (s1-s21) are included in the training data. Other raw features get used are: days, ecoMode, cityMode, sportsMode
Aggregate features These features summarize the historical activity of each asset. In the template, two types of aggregate features are created for each of the 21 sensors. 
•	Predicted the **Remaining Useful Life** (RUL), or **Time to Failure** (TTF).
•	Predicted an asset have fail within certain time frame (e.g. days). 
for example, it may be best to aggergate sensor readings that occur every second - if failures occur only once every couple of months. 
for example - to day or week values before modeling (to get a more balanced dataset between rows that represent failure and rows that represent non-failure).

### Modeling & Prediction
After selecting the useful features, scaling, ready for training the model and choose Long short-term memory(LSTM)
**LSTM** 
* LSTM is a good choice for such sequences which have long term dependencies in it.
* LSTM networks are holding long term memories.
* The prediction of nth sample in a sequence of test samples can be influenced by an input that was given many time steps before. 

**Breakdown happend within 30 days**
We got breakdown prediction probability for every VehicleId.

