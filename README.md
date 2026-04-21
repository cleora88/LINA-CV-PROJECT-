# License Plate Deblurring with Cepstral Analysis

This repository contains a notebook-based project for restoring motion-blurred license plate images using:

- Cepstral analysis for blur parameter estimation (length and angle)
- Estimated PSF (Point Spread Function) reconstruction
- Wiener deconvolution for non-blind restoration
- Quantitative evaluation with PSNR and SSIM

## Project Structure

```text
project/
  code/
    License_Plate_Deblurring_Cepstral.ipynb
    results/
      cepstral_analysis.png
      fft_analysis.png
      K_parameter_effect.png
      psf_kernels.png
      psnr_analysis.png
      psnr_comparison.png
      restoration_pipeline.png
      sample_plates.png
  data/
    original/
    blurred/
    restored/
    README.txt
  report.pdf
```

## Dataset

The dataset is described in `data/README.txt`.

In short:

- `data/original/`: clean synthetic license plate images
- `data/blurred/`: motion-blurred + noisy versions
- `data/restored/`: restored outputs

## Method Overview

The notebook follows this workflow:

1. Load blurred input image
2. Compute FFT and log-spectrum
3. Compute cepstrum and detect blur peaks
4. Estimate motion blur parameters (`L`, `theta`)
5. Build estimated PSF
6. Apply Wiener deconvolution
7. Evaluate with PSNR/SSIM and visualize results

## Requirements

Install dependencies with:

```bash
pip install numpy opencv-python matplotlib scipy notebook
```

## Run

From the repository root:

```bash
jupyter notebook code/License_Plate_Deblurring_Cepstral.ipynb
```

Run cells in order to reproduce the full restoration pipeline and plots in `code/results/`.

## Notes

- Paths in the notebook are expected to be relative to the repository structure above.
- If your local paths differ, update path variables in the first configuration cells.
