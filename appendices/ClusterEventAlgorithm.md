### Algorithm: `clusterEvent(E, K, D)`

#### Input:
- `E`: Set of anomalous events
- `K`: Set of candidate values for the optimal `k`
- `D`: Family of distance metrics to use for clustering

#### Output:
- `optimal_clusters`: Optimal clusters for each distance metric

---

1. Initialize:
   - `optimal_clusters ← ∅` (Optimal Clusters for each distance metric)
   - `features ← ∅` (Features extracted from each event)
   - `inertias ← ∅` (Set of inertia values)

2. **For** each event `e ∈ E`:
   - `a_count ← |{w ∈ e | α(w) > τ(p)}| / τ(p)`  (Count of windows in `e` with anomaly score above threshold)
   - `a_max ← max_{w ∈ e} {α(w)}` (Maximum anomaly score in event `e`)
   - `a_mean ← avg_{w ∈ e | α(w) > τ(p)} {α(w)} / τ(p)` (Mean of scores above threshold)
   - `a_median ← median_{w ∈ e | α(w) > τ(p)} {α(w)} / τ(p)` (Median of scores above threshold)
   - `a_stdev ← stdev_{w ∈ e | α(w) > τ(p)} {α(w)} / τ(p)` (Standard deviation of scores above threshold)
   
   - `vector ← {a_count, a_max, a_mean, a_median, a_stdev}`
   - `features ← features ∪ vector`

3. Normalize `features` (Line 14)

4. **For** each distance metric `d ∈ D`:
   - **For** each candidate value `k ∈ K`:
     - `clusters ← k-means(features, k, d)` (Line 19)
     - `inertias ← inertias ∪ {(k, computeInertia(clusters))}` (Line 20)
   
   - `optimal_k ← findElbow(inertias)` (Line 22)
   - `clusters ← k-means(features, optimal_k, d)` (Line 23)
   - `optimal_clusters ← optimal_clusters ∪ {(d, clusters)}` (Lines 23-25)

5. **Return** `optimal_clusters`

The algorithm iterates over the family `D` of distance metrics to use for clustering and over the set `K` of candidate values for the optimal `k`. We use K-means clustering on the features and experiment with two distance metrics — Euclidean and Manhattan — to validate our approach's effectiveness in clustering anomalous events. For each distance metric and each value of `k`, we use the K-means algorithm to determine a set of `k` clusters (Line 19) and compute the corresponding value of the inertia (Line 20).

The inertia is determined by measuring the distance between each data point and its centroid and summing the squared errors across all data points. Using the elbow method, we compute the optimal value of `k` (Line 22). This method allows us to identify the point where the rate of decrease sharply slows, forming an *elbow* in the curve. Finally, the set of optimal clusters for the current metrics is added to `optimal_clusters` (Lines 23-25).
