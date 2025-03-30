# Quark/Gluon Jet Classification using GIN

This task implements a **Graph Isomorphism Network (GIN)** to classify quark and gluon jets using graph-based representations of jet images. The model constructs graphs from nonzero pixel locations in jet images. GIN layers are then are then applied for classification.

##  Model Architecture
- **Graph Representation:**  
  - Nodes: Non-zero pixels with `[x, y, ECAL, HCAL, Tracks, m0, pt]`.  
  - Edges: Constructed using **k-NN (k=8)** based on spatial `(x, y)` coordinates.  

- **GIN-based Classifier:**
  - 3-layer GINConv with:
    - LeakyReLU(0.1), BatchNorm1d, Dropout (0.2).
  - Global Mean Pooling for final embeddings.
  - Binary classification with BCEWithLogitsLoss (class-weighted).

## Training Information
- Optimizer: AdamW (`lr=0.0015`, `weight_decay=5e-5`).
- Scheduler: ReduceLROnPlateau (`factor=0.5`, `patience=5`).
- Gradient Clipping: `max_norm=1.0` (for stability).
- Batch Size: 16.
- Early Stopping: `patience = 5 epochs`.
- Best Model Checkpoint: Saved as `/kaggle/working/best_gin_model.pt`.

## Performance Evaluation
| Metric            | Value (Final Epoch) |
|------------------|------------------|
| Validation Accuracy | ~72–75% |
| Validation AUC | ~0.80 |
| Training Stability | Smooth loss decay with early stopping |
- One anomaly at epoch 10, mostly due to data distribution shifts.  


## Observations
- Effective feature aggregation using GIN layers.
- Normalization improved training convergence.
- Potential improvements:
  - More expressive architectures (e.g., Graph Transformers).
  - Fine-tuning graph construction (adaptive k-NN, edge features).

