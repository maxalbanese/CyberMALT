The autoencoder is trained to reconstruct the input data by adjusting its weights during the training phase. **Figure 1** illustrates the structure of the autoencoder:

![Figure 1: Structure of the Autoencoder](https://github.com/maxalbanese/CyberMALT/blob/main/images/Autoencoder.jpg?raw=true)

The autoencoder consists of three main components:

1. **Encoder**: Compresses the input data into a smaller representation called the *latent space*.
2. **Latent Space**: Represents the compressed version of the input data.
3. **Decoder**: Reconstructs the latent space back into the original input data.

During training, the autoencoder is trained on normal traffic data, adjusting its weights to minimize the reconstruction error. This training allows it to effectively reconstruct input data similar to the patterns it has learned.

When presented with data that deviates from normal patterns, the reconstruction error increases. This is because the autoencoder struggles to accurately reconstruct inputs it was not trained to handle, leading to noticeable discrepancies between the input and the reconstructed output.

**Anomaly Detection**: By observing the reconstruction error, anomalies in the dataset can be identified. Higher reconstruction errors indicate deviations from normal patterns, signaling potential anomalies in the data.
