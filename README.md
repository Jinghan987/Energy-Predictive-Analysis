# Energy-ML
The aim of this project is to predict the energy demand after each set period. 

The flow of the project is as such : 

1) Since the data from 2016 to 2020 provided are contained in different folders, I firstly created a dataframe for each year. So initially, there were 5 dataframes.

2) After that, the 5 dataframes are combined to produce one dataframe. This new dataframe contains all the data from 2016 to 2020. Throughout the entire combination process, I also checked for null values, and it appears that there are none. Just that there were some columns that are missing in some of the dataframes, of which these issues are corrected.

3) I also noted down the categorical and continuous variables that are present in the dataframe.

4) This is followed by a correlation heatmap - this helps me decide if certain variables should be included. Highly correlated variables will likely cause multicollinearity and as such, one of the variables should be removed. In this scenario, there are no highly correlated variables. Hence, I will still continue with predicting using all the variables.

5) One hot encoding was then used to represent the categorical variables, else the variables will cause some problems to the ML models.

6) After that, data is split into 2 different sets - set A (2016 - 2019 data) and set B (testing data - 2020 data). Set A is then further split into training and validation data in the ratio of 4:1 via train_test_split.

7) Scaling of the continuous variables in the train, validation and test data is then conducted after step 6. Reason for this is so that we avoid the problem of data leakage.

8) After step 7, we feed the training data into different models and tweak the parameters of the models using the validation data until we reach the optimum point (lowest rmse for each of the model).

9) RMSE was used as a metric as it allows for more accurate results and is also easy for interpretation. For example, if the RMSE for SVR is x, then we can interpret it as the predicted results deviating from the actual result by x MW.  

10) After step 9, we pick the models and their respective parameters with the lowest RMSE and use the model to predict the demand of electricity in 2020 (test data). K-Nearest Regressors SVR (rbf kernel), SVR (poly kernel) are used in the predicting the demand of electricity.

11) After that, a graph showing the predicted vs actual demand in 2020 was plot and the best model was determined from the graph. Since predicted values using SVR (rbf kernel) does not have erratic spikes/ extreme values, I believe that we can use SVR (rbf kernel) to predict electricity demand.

![image](https://user-images.githubusercontent.com/64594029/120174910-377f9f80-c238-11eb-8935-ca190b1266ee.png)
