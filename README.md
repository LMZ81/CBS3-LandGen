# CBS3-LandGen: Multi-Modal Deep Learning for Intelligent Landscape Design Generation

## Overview

CBS3-LandGen is a novel multi-modal deep learning framework for intelligent landscape design generation. By integrating image data, text data, and generative optimization techniques, CBS3-LandGen automatically produces landscape design plans that satisfy ecological, functional, and aesthetic requirements under complex design constraints.

This repository contains the implementation, training scripts, and evaluation code for CBS3-LandGen, based on the combination of ConvNeXt for image feature extraction, BART for text understanding, and StyleGAN3 for generative optimization.

## Features

- Multi-modal data fusion of landscape images and design text descriptions  
- State-of-the-art architectures: ConvNeXt, BART, StyleGAN3  
- High-quality and diverse landscape design image generation  
- Text generation consistent with design requirements  
- Comprehensive evaluation with metrics like FID, IS, BLEU, ROUGE, and CLIP Score  

## Keywords

Landscape Design, Multi-modal Deep Learning, ConvNeXt, BART, StyleGAN3, Generative Adversarial Networks, Image-Text Fusion, Intelligent Urban Planning

## Datasets

- **DeepGlobe Land Cover Classification Dataset**  
  High-resolution satellite remote sensing images covering urban, forest, agricultural, and water bodies. Provides spatial structure and geographical information for image modality.  
  [Download Link](https://datasetninja.com/deepglobe)

- **COCO Dataset**  
  Large-scale image dataset with object recognition, segmentation, and textual captions. Provides rich text data for functional requirements and design descriptions.  
  [Download Link](https://paperswithcode.com/dataset/coco)

## Experimental Results Summary

| Dataset    | Metric | CBS3-LandGen | Pix2Pix | CycleGAN | CLIP  | AttnGAN |
|------------|---------|--------------|---------|----------|-------|---------|
| DeepGlobe  | FID     | **25.5**     | 45.2    | 47.3     | 30.1  | 40.5    |
|            | IS      | **4.3**      | 3.4     | 3.2      | 3.8   | 3.6     |
|            | BLEU    | **0.42**     | 0.28    | 0.26     | 0.34  | 0.30    |
| COCO       | FID     | **30.2**     | 50.1    | 52.0     | 35.2  | 43.7    |
|            | IS      | **4.0**      | 3.1     | 2.9      | 3.6   | 3.3     |
|            | BLEU    | **0.45**     | 0.30    | 0.28     | 0.36  | 0.32    |

CBS3-LandGen significantly outperforms baseline methods in image quality, generation diversity, text consistency, and image-text semantic alignment.

## Quick Start

### Installation

```bash
git clone https://github.com/yourusername/CBS3-LandGen.git
cd CBS3-LandGen
pip install -r requirements.txt
````

### Example Python Code for Running Training and Inference

```python
import torch
from model.convnext_module import ConvNeXtModule
from model.bart_module import BARTModule
from model.stylegan3_module import StyleGAN3Module

# Initialize modules
convnext = ConvNeXtModule()
bart = BARTModule()
stylegan3 = StyleGAN3Module()

# Example input tensors
# Image tensor: batch_size x channels x height x width (e.g., 1x3x224x224)
image_input = torch.randn(1, 3, 224, 224)
# Text input token IDs (batch_size x sequence_length)
text_input = torch.randint(0, 30522, (1, 32))  # Assuming BERT tokenizer vocab size

# Extract image features
image_features = convnext(image_input)

# Extract text features
text_features = bart(text_input)

# Generate landscape design image using StyleGAN3
generated_image = stylegan3.generate(image_features, text_features)

# Save or display generated image
import torchvision.utils as vutils
vutils.save_image(generated_image, 'output/generated_landscape.png')
print("Landscape design image generated and saved.")
```

### Evaluation Metrics

* **FID (Fréchet Inception Distance):** Measures similarity between generated and real image distributions. Lower is better.
* **IS (Inception Score):** Measures image quality and diversity. Higher is better.
* **BLEU / ROUGE:** Text generation quality metrics. Higher values indicate better textual similarity.
* **CLIP Score:** Measures semantic alignment between images and text. Higher is better.


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
