# FedSOH: Personalized Federated Learning for Battery Health Prediction

A Federated Learning (FL) framework designed to predict the **State of Health (SOH)** of Lithium-ion batteries across heterogeneous clients using **GRU (Gated Recurrent Units)**, implemented on NVIDIA Orin Nano.

## Project Overview
This project implements a collaborative **Federated Averaging (FedAvg)** architecture to solve the problems of data privacy and heterogeneity in battery monitoring. It enables training a robust global model without centralizing raw data.

### Key Features
- **Federated Averaging**: 20 rounds of global weight aggregation to learn general aging physics.
- **Personalization Phase**: 10-epoch local fine-tuning to resolve performance gaps for specific battery conditions.
- **Heterogeneous Handling**: Successfully manages datasets with varying cycle counts and temperature indexes (B05, B33, B48).


##  Dataset: NASA Battery Profiles
The model utilizes three distinct battery datasets representing different environmental and usage conditions:

| Battery | Temp Index | Cycles | 
| :--- | :--- | :--- | 
| **B05** | Room Temp (24°C) | 125 | 
| **B33** | Variable Load | 133 | 
| **B48** | High Temp | 38 | 

## Performance Results
The personalization strategy successfully reduced error rates for the most challenging client (B48) by nearly **67%**.

| Client | Model Version | MSE | RMSE |
| :--- | :--- | :--- | :--- |
| **B48** | Global (Before) | 0.000759 | 0.027542 |
| **B48** | **Personalized (After)** | **0.000252** | **0.015883** |
| **B05** | Global Model | 0.000038 | 0.006176 |


  
