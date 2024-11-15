# Data Processing and Analysis

We processed the network flows in the **CIC-IDS2017 dataset** as discussed in **Section III-A** and indexed them into 20-second windows (\(\Delta t = 20s\)). We used data from **Monday**, which is known to be benign, for training the autoencoder to model benign traffic on each of the ports: **80**, **21**, and **22**.

Thus, the attacks we can observe include:

- **FTP-Patator**
- **SSH-Patator**
- **DoS Slowloris**
- **DoS SlowHTTPTest**
- **DoS Hulk**
- **DoS GoldenEye**
- **Web brute force attack**
- **XSS attack**
- **SQL-injection attack**
- **DDoS**
- **Port scan**

The **infiltration attack** was not studied because it was mislabeled. The **Botnet** and **Heartbleed** attacks utilized ports with no benign flows.

---

## Anomaly Detection Process

For each window from **Tuesday to Friday** (the days when attacks were executed), we grouped the flows based on their **source IP** (\(s\)), **destination IP** (\(d\)), and **port** (\(p\)), obtaining sets of flows \(w(s, d, p)\). 

For each triple \((s, d, p)\), we computed the anomaly score \(\alpha\) for all windows \(w \in W\) using **Eq. 2**:

\[
\alpha(w) = \text{<Insert your Eq. 2 here>}
\]

Then, we used **algorithm getEvents** to identify anomalous events, where we set \(g = 30\) in our experiments.

---

## Event Clustering

After identifying anomalous events for all triples \((s, d, p)\), we used **algorithm clusterEvent** to cluster these events into groups. This overall process is summarized in **Algorithm analyzeData (Algorithm 3)**, which provides a step-by-step approach to processing and analyzing network flow data for anomaly detection.

---

### Algorithms

#### Algorithm: **getEvents**
Identifies anomalous events for flows.

#### Algorithm: **clusterEvent**
Clusters anomalous events into meaningful groups.

#### Algorithm: **analyzeData**
Processes network flows to identify and cluster anomalous events.

---

This process ensures robust detection and analysis of anomalies within the CIC-IDS2017 dataset, leveraging machine learning models and clustering techniques to identify attack patterns and unusual behaviors effectively.
