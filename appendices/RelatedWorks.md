# Intrusion Detection Techniques

## A. Traditional Intrusion Detection

Traditional intrusion detection methods can be divided into **signature-based detection** and **anomaly-based detection**:

### Signature-Based Detection
- Relies on predefined rules and patterns to identify known threats (e.g., Snort [4]).
- Compares incoming network traffic against a database of known attack signatures.
- **Advantages**:
  - High accuracy for previously identified attacks.
  - Low false positive rates.
- **Disadvantages**:
  - Cannot detect new or evolving threats (zero-day attacks).

### Anomaly-Based Detection
- Establishes a baseline of normal network behavior and flags deviations as potential threats.
- Can use statistical methods and rule-based systems [5].
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
- Example: Heuristic-based methods in [6] for intrusion detection.
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
- Tested on the CIC-IDS2017 Dataset [7][8].
- **Findings**:
  - Supervised learning techniques often achieve excellent results.

### Unsupervised Learning
- Models such as:
  - Expectation-Maximization (EM)
  - K-means
  - Self-Organizing Maps (SOM) [9]
- **Findings**:
  - Supervised techniques outperform unsupervised ones.
  - EM achieved 60% accuracy, the highest among unsupervised methods.

### Deep Learning with Autoencoders
- Used to predict attacks by training on normal behavior [10].
- **Method**:
  - Assigns anomaly scores to test data.
  - Predicts an attack if the score exceeds a threshold.
- **Challenges**:
  - Lower thresholds increase false positives.
  - Higher thresholds reduce detection accuracy.
  - Optimal threshold adjustment is critical.

### Advanced Deep Learning
1. **CNN with Feature Selection**:
   - Combines Convolutional Neural Network (CNN) with the Sigmoid Pigeon Optimization Algorithm [11].
   - Enhances accuracy through optimized feature selection.
2. **Transformer-Based Transfer Learning**:
   - Extracts detailed attack information from network interactions [12].
   - Implements:
     - Transformer-based feature interaction learning.
     - SMOTE for dataset balancing.
     - Hybrid CNN-LSTM model for deep feature extraction.

---

## Research Contributions
Our approach improves classification accuracy without relying on additional deep learning models. Key highlights:
- Accurately distinguishes between malicious and benign traffic sources.
- Reduces false positives by simplifying features in the classification phase.
- Eliminates the need for prior feature selection, as used in [11].
- **Advantages**:
  - Simplifies the process.
  - Reduces computational cost.
