# Realistic Image Generation with GANs (Generative Adversarial Networks)

## Project Overview

This project focuses on **creating realistic images using a Generative Adversarial Network (GAN)** trained on the MNIST handwritten digits dataset.  
The aim is to demonstrate the capability of GANs to learn complex data distributions and generate new, unseen samples that mimic real images.

---

## Abstract

Generative Adversarial Networks (GANs) are one of the most influential architectures in deep learning for generative modeling.  
This project implements a **GAN from scratch using PyTorch**, consisting of:
- **Generator:** Learns to generate realistic handwritten digit images from random noise (latent space).
- **Discriminator:** Learns to distinguish real MNIST images from fake (generated) images.

During training, these models compete in a **minimax game**:
- The Generator tries to fool the Discriminator.
- The Discriminator tries to detect fake images.

Over time, this adversarial process improves both models, leading the Generator to create high-quality, realistic images.

---

## Dataset and Preprocessing

- **Dataset Used:** MNIST Handwritten Digits (28x28 grayscale images)
- **Steps:**
  1. Normalized pixel values to range **[-1, 1]** for stable training.
  2. Used PyTorch’s `DataLoader` for efficient batch loading.
  3. Images flattened and later reshaped for visualization.

---

## Model Architectures

### **Generator**
- Input: 100-dimensional random noise vector (latent vector)
- Layers:
  - Fully Connected Layers
  - Batch Normalization
  - ReLU Activation
  - Final output reshaped to 28x28 pixels
- Output: Fake MNIST-like image

### **Discriminator**
- Input: 28x28 pixel image
- Layers:
  - Fully Connected Layers
  - LeakyReLU Activations
  - Dropout for regularization
- Output: Probability of image being real or fake

---

## Training Process

### Loss Function
- **Adversarial Loss:** Binary Cross Entropy (BCE) Loss

### Optimizers
- Adam optimizers for both Generator and Discriminator

### Techniques Used to Stabilize Training
1. **Label smoothing** to prevent overconfidence.
2. **Batch Normalization** in the Generator to stabilize gradients.
3. **LeakyReLU** activation in Discriminator to avoid dying neurons.

---

## Generated Outputs

### Sample Images
The training process saves generated images at intervals:
- `generated/epoch_0.png`
- `generated/epoch_10.png`
- `generated/epoch_20.png`
- ...
- `generated/epoch_50.png`

By **epoch 50**, the images resemble real handwritten digits very closely.

Example at Epoch 50:

<img width="267" height="350" alt="image" src="https://github.com/user-attachments/assets/e8947846-13e3-4e94-93bd-1b4ea7927932" />
<img width="267" height="350" alt="image" src="https://github.com/user-attachments/assets/04a7e578-0f54-419a-960a-0f1f411d3846" />
<img width="267" height="350" alt="image" src="https://github.com/user-attachments/assets/e8c8d711-00b7-4ad4-9e78-9bd7bd25e82f" />
<img width="267" height="350" alt="image" src="https://github.com/user-attachments/assets/60ee39af-9080-49db-93cc-b963298d08e3" />
<img width="267" height="350" alt="image" src="https://github.com/user-attachments/assets/f70fc65a-0d3d-4811-989c-73fd7b067c0e" />


---

## Results and Observations

- **Early Training (0-10 epochs):** Generated images appear as random noise.
- **Mid Training (20-30 epochs):** Numbers start forming recognizable shapes.
- **Later Training (40-50 epochs):** Digits become sharp and realistic.

GANs effectively learn data distribution without explicitly modeling it.
