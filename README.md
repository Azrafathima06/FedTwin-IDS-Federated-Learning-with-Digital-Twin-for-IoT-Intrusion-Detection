# FedTwin-IDS-Federated-Learning-with-Digital-Twin-for-IoT-Intrusion-Detection


FedTwin-IDS is a privacy-preserving intrusion detection framework for IoT networks that combines **Federated Learning (FL)** with an **Autoencoder-based Digital Twin (DT)**.

The system uses a lightweight federated MLP classifier to learn attack patterns across distributed IoT clients while keeping data local. A Digital Twin models normal network behaviour using reconstruction error, and both signals are combined through a validation-calibrated decision-level gate.

The framework is evaluated on the **TON-IoT dataset** under seen-attack, unseen attack-family drift, and mixed-traffic scenarios. :contentReference[oaicite:0]{index=0}

---

## Overview

IoT intrusion detection is challenging because network data is distributed, heterogeneous, privacy-sensitive, and often non-IID across devices.

This project explores a hybrid detection framework with:

- Federated Learning across distributed IoT clients
- Non-IID client data partitioning
- FedAvg-based model aggregation
- Autoencoder-based behavioural Digital Twin
- Validation-calibrated FL-DT fusion
- Seen and unseen attack-family evaluation
- Component-level ablation
- Statistical significance analysis
- Robustness and calibration analysis
- Communication and inference overhead evaluation

---

## System Architecture

The framework contains five non-IID IoT edge clients that train a lightweight MLP locally.

The overall workflow is:

```text
IoT Client 1 ─┐
IoT Client 2 ─┤
IoT Client 3 ─┼──> FedAvg Server ───> Global MLP ──┐
IoT Client 4 ─┤                                  │
IoT Client 5 ─┘                                  │
                                                  ├──> DT-Gated Fusion
Normal Traffic ──> Autoencoder Digital Twin ──────┘
                                                  │
                                                  ▼
                                       Final Attack Decision
