# Results

The proposed method was evaluated using the CIC-IDS2017 dataset, processed into 20-second windows. The key findings from the experiments are as follows:

## Anomaly Detection
1. **Analyzed Attacks:** 
   - Observed attacks include FTP-Patator, SSH-Patator, DoS (Slowloris, SlowHTTPTest, Hulk, GoldenEye), web brute force, XSS, SQL injection, DDoS, and port scan.
   - The infiltration attack was excluded due to mislabeling.

2. **Anomaly Scoring:** 
   - Anomaly scores were computed for each window using a defined equation.
   - Windows were classified as anomalous if the normalized score exceeded 1.

3. **Threshold Adjustment:**
   - Low thresholds improved recall but increased false positives, which were mitigated during the clustering stage.

## Clustering
- **Methodology:** 
  - Clustering was performed on anomalous events using K-means with Euclidean and Manhattan distance metrics.
  - The optimal number of clusters was determined via the elbow method.

- **Results:** 
  - Events were successfully grouped into benign and attack-related clusters.
  - Small clusters primarily contained attack events, while larger clusters grouped false positives.

- **Purity:** 
  - Most clusters showed high purity, indicating accurate classification of benign and attack events.
  - Clustering allowed effective differentiation between true positives and false positives.

## Highlights
- The system effectively identified various attack types, including:
  - FTP-Patator and SSH-Patator
  - DoS and DDoS
  - Port scan attacks

- **Challenges:** 
  - The web attack generated low anomaly scores and was not detected effectively, as it is host-based rather than network-based.

## Conclusion
The results confirm the effectiveness of the approach in detecting and classifying attacks with high recall and manageable false positive rates. Future work will focus on extending the framework to cover more attack types and enhancing real-time capabilities.

### Figures and Tables
- **Figures 1, 2, and 3:** Show anomaly scores for traffic to ports 21, 22, and 80.
- **Table II & III:** Report clustering results with Euclidean and Manhattan distances, demonstrating the purity and separation of events into meaningful clusters.
