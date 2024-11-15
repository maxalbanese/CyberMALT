### Algorithm: `getEvents(W, α, s, d, p, g)`

#### Input:
- Set of windows `W`
- Anomaly score function `α`
- Threshold mapping `τ`
- Source IP `s`
- Destination IP `d`
- Destination port `p`
- Minimum gap `g` between distinct anomalous events

#### Output:
- Set `E` of anomalous events

---

1. Initialize:
   - `E` ← ∅ (set of events)
   - `current_event` ← ∅ (used to track an individual event instance)
   - `count` ← 0 (number of consecutive data points below the threshold)
   
2. **For** each window `w ∈ W` **do**
   
   3. **If** `α(w, s, d, p) > τ(p)` **then**
   
      - Add `w` to `current_event`
      - Reset `count` to 0

   4. **Else If** `α(w, s, d, p) ≤ τ(p)` **and** `current_event ≠ ∅` **then**

      5. **If** `count < g` **then**
      
         - Add `w` to `current_event`
         - Increment `count` by 1

      6. **Else If** `count = g` **then**
      
         - Trim `current_event` to remove trailing data points with scores below the threshold
         - Add `current_event` to `E`
         - Reset `current_event` to ∅ and `count` to 0

7. **If** `current_event ≠ ∅` after the last window is processed **then**
   - Trim `current_event`
   - Add `current_event` to `E`

8. **Return** `E`


To do so, we use algorithm `getEvents(W, α, s, d, p, g)`, which identifies anomalous events as sequences of one or more consecutive windows in `W`, separated by at least `g` windows with an anomaly score below the port-specific threshold `τ(p)`. The intuition behind this algorithm is that consecutive anomalous data points are likely part of the same malicious event, even when some intermediate data points have scores below the threshold. A malicious event is considered to have concluded after at least `g` windows with a score below the threshold.

The algorithm takes as input the set of windows `W`, the anomaly score function `α`, the threshold mapping `τ`, a source IP `s`, a destination IP `d`, a destination port `p`, and the minimum gap `g` between distinct anomalous events, and returns a set `E` of anomalous events. The set of events `E` and the variable `current_event`, which is used to track an individual event instance, are initialized as empty sets and the `count` of consecutive data points below the threshold is set to 0.

The algorithm iterates over each window `w ∈ W`. If the anomaly score `α(w, s, d, p)` is above the threshold `τ(p)`, the window `w` is added to `current_event` and the `count` of consecutive data points below the threshold is reset. Otherwise, if the score is below the threshold and `current_event` is not empty (i.e., the algorithm is tracking an anomalous event), the algorithm evaluates whether `count` has already reached the maximum gap `g`. If not, window `w` is added to `current_event` and `count` is incremented. Otherwise, if `count` has reached `g`, `current_event` is trimmed to remove the trailing data points with anomaly score below the threshold, and `current_event` and `count` are reset.

Finally, if the algorithm is tracking an event when the last window is processed, `current_event` is trimmed and added to the set of events.
