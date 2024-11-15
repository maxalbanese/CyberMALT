# Autoencoders
The autoencoder is trained to reconstruct the input data by adjusting its weights during the training phase. As shown in![Figure 1: Structure of the Autoencoder](CyberMALT/images/Autoencoder.jpg), the autoencoder consists of three main elements:

1. **Encoder**: Compresses the input data into a smaller representation called the *latent space*.
2. **Latent Space**: Represents the compressed version of the input data.
3. **Decoder**: Reconstructs the latent space back into the original input data.

The autoencoder is trained on normal traffic data, updating its weights to minimize the reconstruction error. This process enables the autoencoder to effectively reconstruct the input data it was trained on. The reconstruction error increases when the autoencoder is presented with data that deviates from the normal patterns it learned during training. This is because the autoencoder attempts to reconstruct inputs it was not trained to handle, leading to higher discrepancies between the input and the reconstructed output.

Thus, this method allows us to determine anomalies in the dataset that resulted in a higher reconstruction error.
