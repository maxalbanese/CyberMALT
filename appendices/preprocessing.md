# Preprocessing

The Preprocessing Module performs several steps to ensure data integrity and usability. These steps include handling empty or otherwise unusable values to improve data quality and removing constant attributes to facilitate effective feature normalization. Data normalization, achieved through min-max normalization, prepares the dataset for model training. Flows are organized temporally, enabling sequential analysis essential for anomaly detection. Flows are sorted based on timestamps to enable sequential analysis and grouped into small sets of consecutive flows for further processing to reduce the sensitivity to small variations in normal traffic. The preprocessing steps are detailed below.

**Handling missing values**  
We remove any data points with missing values for one or more features to prevent incomplete data from skewing the model's learning process.

**Replacing Inf values**  
Inf values are substituted with the maximum value of their respective feature. This ensures that the model does not encounter values that can compromise the subsequent normalization step.

**Handling negative values**  
None of the features in a typical network dataset is expected to have negative values, thus negative values indicate invalid or corrupt data points that must be removed.

**Removing constant columns**  
Columns with constant values across all data points are removed. Such columns do not contribute useful information and can cause issues during normalization.

**Normalization**  
We apply min-max normalization to scale the feature values between 0 and 1. This step ensures that the features contribute equally to the model's learning process.

**Grouping and indexing**  
To reduce the sensitivity of our solution to small variations in normal traffic behavior and facilitate subsequent data retrieval and analysis, we index the dataset by grouping data points (i.e., network flows) with timestamps falling in the same fixed-size temporal window. This allows us to analyze the data using a moving window technique, with the pace set to the same value as the window size, and quickly retrieve all data points falling in each window, effectively partitioning the data into sets of flows for subsequent analysis. Thus, the dataset can be modeled as a sequence $W = \langle w_0, w_1, \ldots, w_n \rangle$ of sets of network flow records grouped by temporal window, as illustrated in Figure 1.

![Example of flow record grouping and indexing.](Images/indexing.pdf)

By implementing these preprocessing steps, we ensure that the data fed into our machine learning models is clean, consistent, and ready for accurate analysis and anomaly detection.

