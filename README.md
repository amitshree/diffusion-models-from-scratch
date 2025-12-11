### Diffusion Models – Modular Implementations and Variants

This repository provides clear, modular, extensible implementations of diffusion-based generative models.

The goal is to offer a collection of architectures, schedulers, building blocks, and utilities that allow researchers and learners to understand, experiment with, and extend diffusion models in a unified framework.

The code is designed to be readable, minimal where possible, and structured in a way that makes modifications easy.

---
#### Overview
Diffusion models are generative models that learn to reverse a gradual noising process applied to data.
They consist of two main components:

- A noise scheduler that defines how noise is added and removed
- A neural network that predicts the noise at each timestep
- This repository offers multiple implementations and architectural variations of these components.

---
### Core Components

#### 1. Noise Schedulers
Different schedulers define how noise evolves across timesteps.
Included variants may include:

- DDPM Scheduler
Linear beta schedule with exact forward and reverse equations.

- Cosine Schedule
A smoother noise schedule inspired by improved DDPMs.

- DDIM Deterministic Sampling
A non-Markovian reverse process for faster generation.

Schedulers are implemented as lightweight, numerically stable modules and can be swapped easily.

---
#### 2. Model Architectures
Multiple architectures are provided to explore how model structure affects diffusion performance.

##### UNet-Based Models

UNets are widely used in diffusion models thanks to their:
- Multi-scale feature hierarchy
- Skip connections
- Ability to integrate time embeddings
- Flexibility in channel size and depth

Variants include:
- Basic UNet
- UNet with residual blocks
- UNet with attention layers
- UNet with transformer blocks at selected resolutions

#### Transformer-Based Models

These architectures replace or augment convolutional layers with:
- Self-attention
- Multi-head attention
- Spatial or token-based transformer blocks

Variants may include:
- Pure Vision Transformer diffusion models
- Hybrid Conv-Transformer backbones
- Local attention and global attention variants

#### Hybrid Architectures
Composable building blocks allow mixing:
- Residual blocks
- Attention modules
- Time embedding modules
- Upsampling / downsampling strategies

---
### 3. Time Embeddings

The repository includes implementations of:
- Sinusoidal time embeddings
- MLP-expanded embeddings
- Learnable position embeddings

These embeddings enable the model to condition on diffusion timesteps and learn how noise evolves over time.

---
### Building Blocks

Common building blocks are implemented in isolation for reuse:

- Residual blocks
- GroupNorm / LayerNorm configurations
- Self-attention modules
- Multi-head attention
- Transformer encoder blocks
- Upsample and downsample modules
- Each block is written in a way that is easy to extend or replace.