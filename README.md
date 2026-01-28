# Predictive Maintenance via Anomaly Detection

## 1. Problem Statement
Unexpected equipment failure leads to high operational and maintenance costs.
This project builds an anomaly detection system to identify early signs of degradation
in turbofan engines using time-series sensor data.

## 2. Decision Framing
The model supports the decision to trigger preventive maintenance
before catastrophic engine failure occurs.

- False Negative: missed failure → expensive downtime
- False Positive: unnecessary maintenance → operational cost

## 3. Dataset
NASA CMAPSS turbofan engine dataset (FD001 subset).
The dataset contains multivariate time-series sensor readings under
controlled operating conditions with gradual degradation.

Key challenges:
- No explicit anomaly labels
- Gradual degradation rather than abrupt failure
- Sensor noise and redundancy

## 4. Defining “Normal” Behavior
Only early lifecycle engine data is treated as healthy behavior.
Anomalies are defined as deviations from this learned healthy state,
not as direct failure labels.

## 5. Baseline Methods
- Statistical thresholding (rolling mean, z-score)
These baselines establish whether ML models provide meaningful improvement.

## 6. Models
- Isolation Forest (trained on healthy windows)
- Autoencoder (reconstruction-error–based anomaly scoring)

Model choices prioritize robustness and interpretability over complexity.

## 7. Evaluation Strategy
Evaluation focuses on:
- Precision–Recall trade-offs
- Detection lead time before failure
- False alarm rate

ROC-AUC is avoided due to class imbalance and delayed labels.

## 8. Results and Failure Analysis
Includes:
- Cases of early detection
- Late or missed detections
- Sensors contributing to false alarms

## 9. Production Considerations
- Threshold adaptation over time
- Data drift monitoring
- Human-in-the-loop validation
- Integration with maintenance workflows

## 10. Conclusion
This project demonstrates an applied anomaly detection pipeline
designed for real-world operational decision-making rather than
offline accuracy optimization.
