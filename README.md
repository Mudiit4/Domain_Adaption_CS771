# Domain Adaptation with ViT & RandMix

Prototype-based domain adaptation framework for handling sequential domain shifts using a frozen Vision Transformer and randomized data augmentation.

## Approach

### 1. Frozen Feature Extraction
Uses a pre-trained ViT-Base as a frozen backbone to extract stable semantic embeddings, avoiding catastrophic forgetting during domain shifts.

### 2. RandMix Augmentation
A lightweight CNN autoencoder injects AdaIN-style noise into the latent space, generating diverse stylistic variations to simulate unfamiliar domains.

### 3. Prototype-Based Self-Training
- **Initialization:** Compute class prototypes (centroids) from the first domain
- **Adaptation:** For new domains, assign pseudo-labels using existing prototypes, then update prototypes based on the new data
- **Result:** Class centers drift to align with new distributions without requiring ground-truth labels
