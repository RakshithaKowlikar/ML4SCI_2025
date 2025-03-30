# Model Training Results Comparison

This document compares the training results of two different models: a Graph Autoencoder (GAE) and a Variational Autoencoder (VAE) from common task 1.

## 1. Graph Autoencoder (GAE) Results

### Training and Validation Loss Trend

* **Training Loss:** Consistently decreased over epochs, starting from 0.5996 and ending at 0.5438.
* **Validation Loss:** THere were fluctuations and eventual plateauing, suggesting potential overfitting. It started at 0.5911 and ended at 0.5478.
* **Early Stopping:** Triggered due to lack of improvement in validation loss, indicating successful prevention of  overfitting.
* **Best Validation Loss:** Reached at epoch 17 (0.5464).

### Key Observations

* The model was learning, as evidenced by the decreasing training loss.
* Hyperparameter tuning and regularization could potentially improve performance.

## 2. Variational Autoencoder (VAE) Results

### Training and Validation Loss Trend

* **Training Reconstruction Loss:** Decreased rapidly in early epochs, then gradually stabilized. Training loss started at 1229.6902 and ended at 0.1313.
* **Training KL Divergence Loss:** Started high (12783.6965), then dropped significantly. This indicates initial difficulty in matching the latent distribution to a standard Gaussian (ending at 3.9510).
* **Validation Loss:** Followed a similar decreasing trend but showed plateauing after epoch 25. Validation Loss started at 0.7052 and ended at 0.2895.
* **Best Validation Loss:** Reached at epoch 48 (0.2893).

### Key Observations

* KL divergence was very low compared to the reconstruction loss, which can lead to blurry reconstructions.
* The first epoch had a strange loss difference.

