# Image Dehazing using Pix2Pix GAN

## Overview

This repository contains an implementation of Pix2Pix Generative Adversarial Network (GAN) for image dehazing. Pix2Pix GAN is a type of conditional GAN which is well-suited for image-to-image translation tasks, where the input and output images have a structured relationship. In the context of image dehazing, the input images are hazy images, and the goal is to generate clear, haze-free images as output.
<p align="center">
  <img src="https://www.mdpi.com/applsci/applsci-10-05898/article_deploy/html/images/applsci-10-05898-g002.png" alt="Model Architecture" width="1048" height="508"/>
</p>



## Features

1. **Conditional GAN Architecture**: Utilizes the Pix2Pix architecture, which consists of a generator network and a discriminator network. The generator takes in hazy images as input and generates clear images as output. The discriminator learns to distinguish between real clear images and generated clear images.

2. **Encoder-Decoder Networks**: The generator network employs an encoder-decoder architecture. The encoder downsamples the input hazy image to extract features, while the decoder upsamples the extracted features to generate the clear image.

3. **Adversarial Training**: The GAN is trained adversarially, where the generator aims to generate realistic clear images to fool the discriminator, while the discriminator aims to distinguish between real and generated images accurately.

4. **PatchGAN Discriminator**: The discriminator network uses a PatchGAN architecture, which classifies image patches rather than entire images. This enables the discriminator to capture local image details and provide more meaningful feedback to the generator.

5. **Training Loop**: The training loop consists of alternating optimization steps for the generator and the discriminator. The generator aims to minimize the discrepancy between the generated clear images and real clear images, while the discriminator aims to maximize its ability to distinguish between real and generated images.

6. **Evaluation and Visualization**: Provides functionality to evaluate the trained model by generating clear images from hazy inputs. Includes visualization tools to compare the input hazy images, generated clear images, and ground truth clear images.

## Implementation

1. **Data Loading**: The training data consists of pairs of hazy images and corresponding clear images. These images are loaded from the dataset and preprocessed for training.

2. **Model Architecture**: The generator and discriminator networks are defined using Keras with TensorFlow backend. The generator network follows an encoder-decoder architecture, while the discriminator network employs a PatchGAN architecture.

3. **Loss Function**: The adversarial loss function, along with additional loss terms such as L1 loss, are used to train the generator network. The discriminator network is trained with binary cross-entropy loss.

4. **Training**: The model is trained using a custom training loop, where batches of hazy-clear image pairs are fed into the network iteratively. The training loop alternates between updating the generator and the discriminator networks.

5. **Evaluation**: After training, the model's performance is evaluated by generating clear images from hazy inputs. These generated images are compared against ground truth clear images for qualitative assessment.

6. **Visualization**: Tools are provided to visualize the input hazy images, generated clear images, and ground truth clear images for evaluation purposes.

## Requirements

- TensorFlow
- Keras
- Matplotlib
- NumPy
- PIL
