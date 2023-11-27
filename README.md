# deep-learning-challenge
Deep Learning Challenge

## Report on the Neural Network Model

### Performance of the Deep Learning Model Created for Alphabet Soup

### Overview

A neural network tool was created for the nonprofit Alphabet Soup to help select applicants for funding with the best chance of success in theri ventures. A CSV containing more than 34,000 organizations that received funding from Alphabet Soup over the years was provided, and within the dataset a number of columns that captured metadata about each organization was captured, such as:

* EIN and NAME—Identification columns
* APPLICATION_TYPE—Alphabet Soup application type
* AFFILIATION—Affiliated sector of industry
* CLASSIFICATION—Government organization classification
* USE_CASE—Use case for funding
* ORGANIZATION—Organization type
* STATUS—Active status
* INCOME_AMT—Income classification
* SPECIAL_CONSIDERATIONS—Special considerations for application
* ASK_AMT—Funding amount requested
* IS_SUCCESSFUL—Was the money used effectively

### Results

## Original Nueral Network Model:

# Data Preprocessing
The data was preprocessed and the EIN and NAME columns were dropped, and bins were created based on APPLICATION_TYPE and CLASSIFICATION. Each categorical data was converted to numeric data, and our preprocessed data was split into features and target arrays, and scaled using StandardScalar. 

The original model used the following target and features:
* Model Target: 'IS_SUCCESSFUL'
* Model Features: Everything except 'EIN' and 'NAME'

# Compiling, Training, and Evaluating the Model:
The original model was developed using the following:
* 2 hidden layers
* 1st hidden layer = 80 neurons, activation function: "tanh"
* 2nd hidden layer = 30 neurons, activation function: "relu"
* Output layer = 1 neuron, activation function: "relu"

An evaluation of this model revealed that the model performance had a loss of 59.2% and an accuaracy of 72.4% which was below the target of 75%. 

## Neural Network Optimization 1
To increase the performance of the model, the following changes were made:

# Data Preprocessing
The 'NAME' category was reintroduced, so the optimized model used the following target and features:
* Model Target: 'IS_SUCCESSFUL'
* Model Feature: Everthing except 'EIN'

# Compiling, Training, and Evaluating the Optimized Model:
The optimized model was developed using the following:
* 4 hidden layers
* 1st hidden layer = 80 neurons, activation function: "relu"
* 2nd hidden layer = 40 neurons, activation function: "sigmoid"
* 3rd hidden layer = 20 neurons, activation function: "sigmoid"
* 4th hidden layer = 10 neurons, activation function: "sigmoid"
* Output layer = 1 neuron, activation function: "sigmoid"

An evaluation of the optimized model revealed that model had an increase in accuracy at 78.2%, and decrease in loss at 48.4%. This met the 75% requirement for the optimized model. 

## Neural Network Auto Optimization
To further optimize the model, an auto optimization was performed.

# Data Preprocessing
The 'NAME' category was kept for the auto optimization, so the auto optimized model used the following target and features:
* Model Target: 'IS_SUCCESSFUL'
* Model Feature: Everthing except 'EIN'

# Compiling, Training, and Evaluating the Auto Optimized Model:
The data was tuned using the kerastuner library. The best model based on the auto optimization used the following:

* 'activation': 'sigmoid',
* 'first_units': 6,
* 'num_layers': 2,
* 'units_0': 6,
* 'units_1': 1,
* 'units_2': 1,
* 'tuner/epochs': 6,
* 'tuner/initial_epoch': 2,
* 'tuner/bracket': 1,
* 'tuner/round': 1,
* 'tuner/trial_id': '0002',
* 'units_3': 6

The performance of the auto optimized model had a loss of 48.8% and an accuracy of 80.1% which met the requirement of > 75%, and had a higher accuracy than the optimized model.

### Summary
The original model used 2 layers at 80 and 30 neurons but was unable to achieve the 75% accuracy target. By adding the 'NAME' category, and increasing the hidden layers to 4 and adjusting the activation function, we were able to achieve a 78.2% accuracy. However, using the kerastuner to auto optimize our model revealed that we could achieve 80.1% accuracy using only 2 layers, with 6 neurons in the first layer, and 1 neuron in the 2nd, with the 'sigmoid' activation function. This reveals that while adding hidden layers can improve the accuracy of the model, it is not necessary to increase accuracy. Additionally, adding the 'NAME' category back into the preprocessed data gave us a bigger increase in accuracy which indicates that the shape of the dataset before preprocessing has a big impact on the accuracy of a nerual network model.   