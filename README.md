# MIE1517-Project-3 - Image Colourization

This project explores deep learning methods to automatically colorize grayscale images using:
- A custom-built **Autoencoder**
- A **Conditional GAN (cGAN)**
Apply both models to the **CIFAR-10 dataset** and compare their colorization capabilities.

---
Run this notebook directly in **Google Colab** (recommended).
> [Open in Colab](https://drive.google.com/file/d/1EOCKZz2-DNnCZCk3SbMOcOWcTMZPz3RB/view?usp=sharing)
---

## Dataset

- Dataset: **CIFAR-10**
- Image size: `32x32` pixels
- Training set: 50,000 images
- Test set: 10,000 images
- Preprocessing: Converted images to **grayscale** for input, and **color (RGB)** for target output

---

## Part A – Autoencoder for Colourization

### Model Overview
- The encoder compresses grayscale input to latent space.
- The decoder reconstructs the RGB channels from this latent representation.

### Training
- Loss: Mean Squared Error (MSE)
- Optimizer: Adam
- Epochs: 20

### Results
- Model successfully restored general color tones
- Some minor artifacts and smoothing observed
- **Reconstruction fidelity** was evaluated visually and via pixel-wise loss

---

## Part B – Colourization with Conditional GAN (cGAN)

### Model Architecture
- **Generator**: Learns to produce realistic color outputs conditioned on grayscale input
- **Discriminator**: Learns to distinguish real vs. fake colorizations

### Training Strategy
- Conditional input: grayscale image
- Target output: RGB color image
- Losses:
  - Generator: BCE (adversarial) + L1 (reconstruction)
  - Discriminator: BCE loss

### Improvements Over AE
| Metric        | Autoencoder | cGAN |
|---------------|-------------|------|
| Color accuracy | Moderate    | Higher vibrancy, realism |
| Sharpness      | Low         | High (edges better defined) |
| Visual Realism | Acceptable  | Significantly better |

---

## Discussion
- Autoencoder is simpler and trains faster but lacks color vibrancy
- cGAN greatly enhances realism but is harder to train
