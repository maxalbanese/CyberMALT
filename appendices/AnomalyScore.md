Each set of flows `w(s,d,p)` is fed to the autoencoder to obtain the corresponding reconstruction error. As this error increases when the autoencoder is presented with data that deviates from normal data, we use the reconstruction error as the anomaly score. Formally, we define the anomaly score as a function $\alpha: W \times S \times D \times P \rightarrow \mathbb{R}^+$ that associates a window `w` and a triple `(s,d,p)` with a real number $\alpha(w,s,d,p)$ defined as the Root Mean Squared Error (RMSE) between the autoencoder inputs and outputs, as shown in Eq.~(1) below.

$$
\alpha\left(w,s,d,p\right) = \sqrt{\frac{1}{m} \cdot \sum_{i=1}^{m}\left(y_{i} - x_{i}\right)^{2}}
$$

If `w(s,d,p) = ∅`, we set $\alpha\left(w,s,d,p\right) = 0$.

If the anomaly score for a set `w(s,d,p)` of flow records is above the predefined threshold value `τ(p)`, then `w(s,d,p)` is marked as an anomaly by the Anomaly Detection Module. Otherwise, it is marked as normal. A low threshold may result in the detection of more attacks, but it increases the risk of false positives. Conversely, a high threshold may reduce the number of false positives, but it could also mean that some attacks remain undetected.
