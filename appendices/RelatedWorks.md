# Intrusion Detection Techniques

## A. Traditional Intrusion Detection

Traditional intrusion detection methods can be divided into **signature-based detection** and **anomaly-based detection**:

### Signature-Based Detection
- Relies on predefined rules and patterns to identify known threats (e.g., Snort [1]).
- Compares incoming network traffic against a database of known attack signatures.
- **Advantages**:
  - High accuracy for previously identified attacks.
  - Low false positive rates.
- **Disadvantages**:
  - Cannot detect new or evolving threats (zero-day attacks).

### Anomaly-Based Detection
- Establishes a baseline of normal network behavior and flags deviations as potential threats.
- Can use statistical methods and rule-based systems [2].
- Monitors network parameters like:
  - Traffic volume
  - Connection patterns
  - Protocol usage
- **Advantages**:
  - Capable of detecting novel attacks.
- **Disadvantages**:
  - Higher false positive rates due to unusual but legitimate behavior being flagged as anomalies.

### Heuristic-Based Detection
- Utilizes expert-defined heuristics to identify suspicious activities.
- Example: Heuristic-based methods in [3] for intrusion detection.
- **Advantages**:
  - Effective in specific scenarios.
- **Disadvantages**:
  - Performance depends on the quality of heuristics.

---

## B. ML-Based Intrusion Detection

Several approaches leverage **machine learning (ML)** for threat detection:

### Supervised Learning
- Techniques used include:
  - GaussianNB (GNB)
  - BernoulliNB (BNB)
  - Decision Tree
  - KNN
  - Logistic Regression
  - SVM
  - SGD
  - Random Forest
- Tested on the CIC-IDS2017 Dataset [4][5].
- **Findings**:
  - Supervised learning techniques often achieve excellent results.

### Unsupervised Learning
- Models such as:
  - Expectation-Maximization (EM)
  - K-means
  - Self-Organizing Maps (SOM) [6].
- **Findings**:
  - Supervised techniques outperform unsupervised ones.
  - EM achieved 60% accuracy, the highest among unsupervised methods.

### Deep Learning with Autoencoders
- Used to predict attacks by training on normal behavior [7].
- **Method**:
  - Assigns anomaly scores to test data.
  - Predicts an attack if the score exceeds a threshold.
- **Challenges**:
  - Lower thresholds increase false positives.
  - Higher thresholds reduce detection accuracy.
  - Optimal threshold adjustment is critical.

### Advanced Deep Learning
1. **CNN with Feature Selection**:
   - Combines Convolutional Neural Network (CNN) with the Sigmoid Pigeon Optimization Algorithm [8].
   - Enhances accuracy through optimized feature selection.
2. **Transformer-Based Transfer Learning**:
   - Extracts detailed attack information from network interactions [9].
   - Implements:
     - Transformer-based feature interaction learning.
     - SMOTE for dataset balancing.
     - Hybrid CNN-LSTM model for deep feature extraction.

---

## Research Contributions
Our approach improves classification accuracy without relying on additional deep learning models. Key highlights:
- Accurately distinguishes between malicious and benign traffic sources.
- Reduces false positives by simplifying features in the classification phase.
- Eliminates the need for prior feature selection, as used in [8].
- **Advantages**:
  - Simplifies the process.
  - Reduces computational cost.

---

## References

[1] Zhou, Zhimin, et al. "The study on network intrusion detection system of Snort." *2010 International Conference on Networking and Digital Society*, vol. 2, 2010, pp. 194-196. DOI: [10.1109/ICNDS.2010.5479341](https://doi.org/10.1109/ICNDS.2010.5479341).

[2] Rastegari, Samaneh, et al. "A Statistical Rule Learning Approach to Network Intrusion Detection." *2015 5th International Conference on IT Convergence and Security (ICITCS)*, 2015, pp. 1-5. DOI: [10.1109/ICITCS.2015.7292933](https://doi.org/10.1109/ICITCS.2015.7292933).

[3] Wu, Kehe, et al. "The research of intrusion detection technology based on heuristic analysis." *2011 6th IEEE Joint International Information Technology and Artificial Intelligence Conference*, vol. 1, 2011, pp. 164-166. DOI: [10.1109/ITAIC.2011.6030176](https://doi.org/10.1109/ITAIC.2011.6030176).

[4] Panwar, Shailesh Singh, et al. "An Intrusion Detection Model for CICIDS-2017 Dataset Using Machine Learning Algorithms." *2022 International Conference on Advances in Computing, Communication and Materials (ICACCM)*, 2022, pp. 1-10. DOI: [10.1109/ICACCM56405.2022.10009400](https://doi.org/10.1109/ICACCM56405.2022.10009400).

[5] Maseer, Ziadoon Kamil, et al. "Benchmarking of Machine Learning for Anomaly Based Intrusion Detection Systems in the CICIDS2017 Dataset." *IEEE Access*, vol. 9, 2021, pp. 22351-22370. [Available here](https://api.semanticscholar.org/CorpusID:231914286).

[6] Roshan, Khushnaseeb, and Aasim Zafar. "An Optimized Auto-Encoder based Approach for Detecting Zero-Day Cyber-Attacks in Computer Network." *2021 5th International Conference on Information Systems and Computer Networks (ISCON)*, 2021, pp. 1-6. DOI: [10.1109/ISCON52037.2021.9702437](https://doi.org/10.1109/ISCON52037.2021.9702437).

[7] Zhang, Liang, and Chengxin Xu. "A Intrusion Detection Model Based on Convolutional Neural Network and Feature Selection." *2022 5th International Conference on Artificial Intelligence and Big Data (ICAIBD)*, 2022, pp. 162-167. DOI: [10.1109/ICAIBD55127.2022.9820384](https://doi.org/10.1109/ICAIBD55127.2022.9820384).

[8] Ullah, Farhan, et al. "IDS-INT: Intrusion detection system using transformer-based transfer learning for imbalanced network traffic." *Digital Communications and Networks*, vol. 10, no. 1, 2024, pp. 190-204. DOI: [10.1016/j.dcan.2023.03.008](https://doi.org/10.1016/j.dcan.2023.03.008).
