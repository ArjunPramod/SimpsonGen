# SimpsonGen

## Overview

This repository contains the code for training a Generative Adversarial Network (GAN) to generate images of Simpson characters. The GAN architecture consists of a generator and discriminator trained on a dataset of cropped Simpson faces. The goal is to generate realistic images that resemble characters from the Simpsons TV show.

## Dataset

The dataset used for training the GAN consists of cropped images of Simpson characters. The images are preprocessed using various transformations, such as resizing, rotation, and horizontal flipping. Invalid images are removed during dataset loading.

### Dataset Structure

The dataset structure is as follows:
```
|-- extracted_data
| |-- cropped
| |-- image1.jpg
| |-- image2.jpg
| |-- ...
```

## Model Architecture

### Generator

The generator architecture is defined as follows:

1. Input: Random noise vector of size Z.
2. Fully connected layer: Z to 1024*8*8.
3. Batch normalization and LeakyReLU activation.
4. Reshape to (1024, 8, 8).
5. Transposed convolution layers with batch normalization and LeakyReLU activation.
6. Output: RGB image.

### Discriminator

The discriminator architecture is defined as follows:

1. Convolutional layers with batch normalization and LeakyReLU activation.
2. Linearization and fully connected layer to output a single value.
3. Sigmoid activation for binary classification.

## Training

The GAN is trained for a specified number of epochs with Adam optimizer. Both generator and discriminator have separate optimizers. Adversarial loss (BCELoss) is used for training.

### Hyperparameters

- Epochs: 50
- Learning rate for generator: 0.0002
- Learning rate for discriminator: 0.0002

## Visualization

During training, generated images are displayed at regular intervals. The progress of the generator and discriminator losses is visualized in a loss curve plot. Additionally, generated images are saved as GIFs for each epoch.

## Usage

1. Install dependencies: `pip install -r requirements.txt`
2. Download and extract the dataset.
3. Run the training script: `python train.py`

## Results

Generated images and loss curves are available in the `generated_images` and `loss_curves` directories, respectively.

## License

This project is licensed under the Attribution-NonCommercial-NoDerivs 4.0 International (CC BY-NC-ND 4.0) [License](https://github.com/ArjunPramod/SimpsonGen/blob/main/LICENSE.md).
