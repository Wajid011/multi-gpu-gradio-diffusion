# Stable Diffusion Dual-Pipeline Gradio App

A multi-GPU Gradio web application for generating images and applying depth-based restyling using Stable Diffusion models, running on separate GPUs for optimized inference and zero interference.

## Features
- **Text-to-Image (GPU 0):** Generates high-quality images from text prompts using `runwayml/stable-diffusion-v1-5`.
- **Depth-to-Image Restyling (GPU 1):** Applies artistic styles or transformations to uploaded images using depth-aware image-to-image pipeline (`sd2-community/stable-diffusion-2-depth`).
- **Memory Management:** Includes utility functions for automatically freeing up unused VRAM after every inference sequence.
- **Sleek Web Interface:** Uses a custom, user-friendly Gradio interface with separate tabs for both pipelines.

## Prerequisites
To run this notebook, you will need a machine with:
- At least 2 GPUs with 14 GB+ VRAM each (e.g. 2x NVIDIA T4 or better). It is optimized to split the work across `cuda:0` and `cuda:1`.
- A Hugging Face account with an access token (for downloading weights).

## Installation
The notebook automatically installs all required dependencies:
```bash
pip install gradio diffusers transformers accelerate torch torchvision xformers safetensors Pillow opencv-python-headless
```

## Usage
1. Open the Jupyter Notebook `Wajid_stableDiffusion.ipynb`.
2. Add your Hugging Face API token in Kaggle/Colab Secrets under the name `HF_Token`, or modify the authentication cell to include your token explicitly.
3. Run all the cells progressively. 
4. A public Gradio link will be generated in the final cell, allowing you to use both models via an interactive user interface!
5. To shut down gracefully and flush the GPU's memory cache, run the final cleanup cell.
