# Watermark-with-GAN
This project is a Deep Learning application designed to perform image inpainting and watermark removal on medical imaging data using Generative Adversarial Networks (GANs). Specifically, it focuses on removing QR code overlays from Chest X-ray images to restore the original anatomical details.

# Medical X-Ray Watermark Removal using GANs

This project implements a Deep Learning model based on **Generative Adversarial Networks (GANs)** to remove QR code watermarks from medical X-ray images and restore the underlying anatomical details.

## 🎯 Project Goal
The primary objective is to demonstrate image restoration capabilities in the medical domain. The model learns to:
1.  Take a **watermarked X-ray image** (corrupted with a QR code) as input.
2.  **Remove the watermark** effectively.
3.  **Inpaint/Restore** the occluded area to match the original tissue structure.

## 🏗️ Methodology

### 1. Dataset
* **Source:** [NIH Chest X-rays Dataset](https://www.kaggle.com/datasets/nih-chest-xrays/data) via KaggleHub.
* **Preprocessing:** Images are resized to `256x256` and converted to grayscale (`L` mode).

### 2. Synthetic Data Generation
To supervise the training, we generate synthetic training pairs on-the-fly:
* **Input:** Original X-ray + Randomly generated QR Code overlay.
* **Target:** Original clean X-ray.
* *Libraries used:* `qrcode`, `albumentations`.

### 3. Model Architecture (GAN)
* **Generator:** A U-Net based architecture that acts as an autoencoder to reconstruct the clean image.
* **Discriminator:** A PatchGAN classifier that distinguishes between real clean images and the generator's output.
* **Loss Function:** Combination of Adversarial Loss (for realism) and L1 Loss (for pixel-wise accuracy).

## 🛠️ Technologies & Libraries
* **Python 3**
* **PyTorch** (Deep Learning Framework)
* **Torchvision** (Image transformations)
* **KaggleHub** (Dataset downloading)
* **QRCode** (Watermark generation)
* **Scikit-Image** (Metrics: PSNR, SSIM)
* **OpenCV & PIL** (Image processing)

## 🚀 Installation & Usage

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/zeynepdemirtass/Medical-Watermark-GAN.git](https://github.com/zeynepdemirtass/Medical-Watermark-GAN.git)
    cd Medical-Watermark-GAN
    ```

2.  **Install dependencies:**
    ```bash
    pip install torch torchvision opencv-python qrcode kagglehub albumentations matplotlib scikit-image
    ```

3.  **Run the Notebook:**
    Open `Watermark_with_GAN_Zeynep.ipynb` in Jupyter or Google Colab. The notebook will automatically:
    * Download the dataset.
    * Generate watermarked samples.
    * Train the GAN model.
    * Display "Input vs. Generated vs. Ground Truth" results.

## 📊 Results & Metrics
The model performance is evaluated using standard image restoration metrics:
* **PSNR (Peak Signal-to-Noise Ratio)**
* **SSIM (Structural Similarity Index)**

---
