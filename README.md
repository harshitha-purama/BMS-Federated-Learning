# BMS-Federated-Learning
A Federated Learning (FL) framework designed to predict the State of Health (SOH) of Lithium-ion batteries across heterogeneous clients using GRU (Gated Recurrent Units).

## Project Overview
This project transitions battery health monitoring from isolated models to a collaborative **Federated Averaging (FedAvg)** architecture. It solves the problem of data heterogeneity and privacy by training a global model across different battery profiles without sharing raw data.

### Key Features
- **Federated Averaging**: 20 rounds of global weight aggregation.
- **Personalization Phase**: 10-epoch local fine-tuning to fix performance gaps in small/high-temp datasets.
- **Heterogeneous Handling**: Successfully manages datasets with varying cycle counts and thermal indexes (B05, B33, B48).

---

## Dataset: NASA Battery Profiles
The model was trained on three distinct battery datasets with different environmental conditions:

| Battery | Temp Index | Cycles | 
| :--- | :--- | :--- | 
| **B05** | Room Temp (24°C) | 125 | 
| **B33** | Variable Load | 133 | 
| **B48** | High Temp | 38 | 

---

## Architecture & Flow
The project follows a two-stage learning process:

1. **Global FL Stage**: 20 rounds of communication where the server aggregates weights from all clients to learn general aging physics.
2. **Personalization Stage**: Client 1 (B48) performs local transfer learning to adapt the global weights to its specific high-temperature decay curve.



---

## Results
The implementation successfully reduced error rates for the most challenging client (B48) by nearly **70%**.

| Client | Model | MSE | RMSE |
| :--- | :--- | :--- | :--- |
| **B48** | Global (Before) | 0.000759 | 0.027542 |
| **B48** | **Personalized (After)** | **0.000252** | **0.015883** |
| **B05** | Global | 0.000038 | 0.006176 |
