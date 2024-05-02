# CycleGAN for Image Dehazing

CycleGAN is a type of Generative Adversarial Network (GAN) used for image-to-image translation tasks without needing paired examples. This implementation is specifically tailored for image dehazing, which aims to remove haze from images.

<p align="center">
  <img src="https://raw.githubusercontent.com/engindeniz/Cycle-Dehaze/master/figs/model.png" alt="Model Architecture" width="1048" height="508"/>
</p>

## Overview

The CycleGAN for dehazing consists of two main components:
1. **Generators**: Convert images from domain A (hazy images) to domain B (dehazed images) and vice versa.
2. **Discriminators**: Differentiate between real images and generated images in both domains.

### Network Architecture

- **Generator (G)**: Each generator is an encoder-decoder network with residual blocks. The encoder part downsamples the input image, the residual blocks transform the features, and the decoder upsamples the features to generate an output image of the same size as the input.
- **Discriminator (D)**: Each discriminator is a PatchGAN classifier, which classifies whether 70x70 overlapping patches are real or fake. This architecture helps the model focus on high-frequency features, which are crucial in understanding textures and details in images.

### Loss Functions

- **Adversarial Loss**: Ensures the generated images are indistinguishable from real images within each domain.
- **Cycle Consistency Loss**: Ensures that each image that has been translated from one domain to the back to the original domain remains the same (e.g., A -> B -> A).
- **Identity Loss**: When an image from the target domain is fed to the generator, it should yield the real image itself (e.g., B -> B).

### Training

Training involves updating the weights of both generators and discriminators using backpropagation based on the loss functions. It's a challenging process as it involves maintaining a balance between two competing networks.

### Implementation Steps

1. **Load Dataset**: Load and preprocess the dataset. The hazy images are domain A, and the clear images are domain B.
2. **Define Models**: Define the architecture for both generators and discriminators.
3. **Compile Models**: Set up the training with appropriate optimizers and loss functions.
4. **Train Models**: Train the models using the dataset.
5. **Evaluate Models**: Use metrics such as PSNR (Peak Signal-to-Noise Ratio) and SSIM (Structural Similarity Index) to evaluate the quality of dehazing.

### Usage

To use the trained CycleGAN for dehazing, input a hazy image to the generator that translates from hazy to clear images. The output will be the dehazed image.

## Conclusion

This CycleGAN approach provides a powerful tool for image dehazing without the need for paired training samples, leveraging the capabilities of GANs to learn deep representations and translate images from one domain to another.
