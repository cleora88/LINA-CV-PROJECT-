================================================================
LICENSE PLATE DEBLURRING — DATASET DESCRIPTION
================================================================

STRUCTURE
---------
data/
  original/       20 synthetic license plate images (clean, 320x100 px, grayscale PNG)
  blurred/        Same 20 plates after motion-blur + Gaussian noise
  restored/       Deblurred versions (Wiener + estimated PSF via cepstral analysis)
  real/           1 real car photograph (Audi RS, Moroccan plate 50943 | B | 15)
                    audi_original.png  — sharp original (reference)
                    audi_blurred.png   — simulated horizontal motion blur (L=20, theta=0)
                    audi_restored.png  — restored with cepstral PSF + Wiener (K=0.01)
  README.txt      This file

SYNTHETIC DATASET (20 plates)
------------------------------
- 4 blur angles  : 0°, 15°, 30°, 45° (5 plates each)
- Blur lengths   : 10, 12, 15, 20, 25 pixels
- Noise std      : 1.5 gray levels (sigma = 1.5/255)
- Image size     : 320 x 100 pixels, 8-bit grayscale
- Format         : PNG (lossless)
- Naming         : plate_NN.png  (NN = 01 to 20)

REAL IMAGE
----------
- Source         : Synthetic photograph of Moroccan plate (Audi RS)
- Plate text     : 50943 | B | 15  (Arabic script region marker)
- Applied blur   : Linear motion blur, L=20 px, theta=0° (horizontal)
- Restoration    : Cepstral PSF estimation + Wiener deconvolution (K=0.01)

PIPELINE
--------
  Image floue
      |
      |--[Step 1]--> FFT --> log|spectrum| --> IFFT --> Cepstrum
      |                                                    |
      |--[Step 2]--> Peak detection --> L_hat, theta_hat --> PSF_estimated
      |                                                          |
      |--[Step 3]--> Wiener non-blind( G, PSF_estimated, K ) --> Restored image

QUALITY METRICS
---------------
- PSNR  : Peak Signal-to-Noise Ratio (dB)  — higher is better
- SSIM  : Structural Similarity Index [0,1] — higher is better

================================================================
