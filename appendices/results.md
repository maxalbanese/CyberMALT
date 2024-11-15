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
The results confirm the approach's effectiveness in detecting and classifying attacks with high recall and manageable false positive rates. Future work will focus on extending the framework to cover more attack types and enhancing real-time capabilities.

### Figures and Tables
- **Figures 1, 2, and 3:** Show anomaly scores for traffic to ports 21, 22, and 80.
![Figure 1: Results for Traffic to Port 21](https://github.com/maxalbanese/CyberMALT/blob/main/images/FTP-Patator-PortScan-21.jpg)
![Figure 2: Results for Traffic to Port 22](https://github.com/maxalbanese/CyberMALT/blob/main/images/SSH-Patator-PortScan-22.jpg)
![Figure 3: Results for Traffic to Port 80](https://github.com/maxalbanese/CyberMALT/blob/main/images/DoS-PortScan-DDoS-Web-Attack-80.jpg)

- **Table I & II:** Report clustering results with Euclidean and Manhattan distances, demonstrating the purity and separation of events into meaningful clusters.

 **Euclidean**                                                                                                                 
| Label | # Number of Events | Description                                                                                      | Purity |
|-------|--------------------|--------------------------------------------------------------------------------------------------|--------|
| 4     | 510                | False Positive Events                                                                            | 100%   |
| 13    | 312                | False Positive Events, 3 PortScan Events                                                         | 96%    |
| 0     | 264                | False Positive Events, 3 PortScan Events                                                         | 98%    |
| 11    | 99                 | False Positive Events, 4 PortScan Events                                                         | 96%    |
| 2     | 57                 | False Positive Events                                                                            | 100%   |
| 8     | 39                 | False Positive Events                                                                            | 100%   |
| 7     | 25                 | False Positive Events                                                                            | 100%   |
| 5     | 15                 | False Positive Events                                                                            | 100%   |
| 9     | 9                  | False Positive Events                                                                            | 100%   |
| 3     | 8                  | False Positive Events                                                                            | 100%   |
| 14    | 7                  | False Positive Events                                                                            | 100%   |
| 1     | 5                  | False Positive Events                                                                            | 100%   |
| 10    | 4                  | DDoS Event, FTP-Patator Event, SSH-Patator Event, False Positive Event                           | 75%    |
| 6     | 2                  | Dos Window Event, False Positive Event                                                           | 50%    |
| 12    | 2                  | False Positive Events                                                                            | 100%   |

**Manhattan**
| Label | # Number of Events | Description                                                                                      | Purity |
|-------|--------------------|--------------------------------------------------------------------------------------------------|--------|
| 0     | 510                | False Positive Events                                                                           | 100%   |
| 3     | 252                | False Positive Events, 2 PortScan Events                                                        | 99%    |
| 8     | 247                | False Positive Events, 2 PortScan Events                                                        | 99%    |
| 5     | 105                | False Positive Events, 4 PortScan Events                                                        | 96%    |
| 10    | 86                 | False Positive Events, 2 PortScan Events                                                        | 97%    |
| 14    | 56                 | False Positive Events                                                                           | 100%   |
| 11    | 49                 | False Positive Events                                                                           | 100%   |
| 7     | 22                 | False Positive Events                                                                           | 100%   |
| 13    | 9                  | False Positive Events                                                                           | 100%   |
| 9     | 9                  | False Positive Events                                                                           | 100%   |
| 1     | 5                  | False Positive Events                                                                           | 100%   |
| 6     | 4                  | DDoS Event, False Positive Events                                                               | 75%    |
| 2     | 2                  | FTP-Patator Event, SSH-Patator Event                                                            | 100%   |
| 4     | 1                  | Dos Window Event                                                                                | 100%   |
| 12    | 1                  | False Positive Event                                                                            | 100%   |

