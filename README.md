# Underwater images Enhancement Model

This repository contains my personal implementation of the third stage of my Master’s thesis on the topic of **Combination of Deep Learning Techniques and
Classical Methods for Underwater Images Enhancement**, proposed and supervised by Professor: **José Luis Lisani Roca**.

It includes three **UNet-based architectures** for underwater image enhancement, each implemented as a Jupyter Notebook. These notebooks are designed to be easy to follow and work in most environments and operating systems.

The U-Net architecture has proven especially effective for this task thanks to its symmetric encoder-decoder structure and skip connections, which preserve spatial information while facilitating deep contextual learning. 
This unique architecture enables the reconstruction of fine-grained details while maintaining a large receptive field, making U-Net ideally suited for underwater image enhancement.

The UIEB dataset serves as a valuable benchmark for these models, containing original low quality underwater images alongside their enhanced versions produced
by classical algorithms. This dataset was generated through a consensus of both expert and non-expert evaluators, who performed pairwise comparisons to select the best enhancement results.

These implementations are partially based on assignments I completed for a deep learning subject provided by Professor: **Miguel Ángel Calafat Torrens**. 
All of them are also available in my [Deep Learning repository](#), which contains a collection of powerful implementations and carefully designed challenges.
This repository serves as a strong foundation for anyone looking to build expertise and excel in the field of deep learning.

---
## Conventional Boundaries

Despite notable progress in deep learning for underwater image enhancement, researchers still encounter several challenges that constrain important progress. A key limitation is the lack of comprehensive datasets;  most publicly available ones, such as UIEB or EUVP, contain a relatively small number of images and often lack diversity in underwater conditions. 

Additionally, the field remains stuck in a repetitive loop of approaches: researchers frequently adopt similar CNN or GAN-based architectures with minor modifications, repackaged as novel contributions. This dogmatic adherence to established frameworks limits innovation.

Most works still rely on conventional preprocessing steps like resizing, cropping, or padding images to fixed dimensions, dictated largely by the constraints of frameworks like PyTorch, which require uniform input sizes within a batch. These technical limitations have created a methodological box, where almost all researchers operate within the same rigid boundaries, preventing the exploration of more flexible or adaptive models that could better handle the natural variability in underwater imagery.

The majority of deep learning-based approaches published in the field of underwater image enhancement rely on resizing, cropping, or padding input images to fixed dimensions prior to processing. However, resizing introduces irreversible detail loss, distortion, and interpolation artifacts, which are especially detrimental in underwater imagery. This convention stems from architectural constraints of frameworks like PyTorch and TensorFlow that do not natively support batch processing of images with varying resolutions.

This workaround highlights a broader constraint in standard deep learning ecosystems: variable-resolution batching is not supported by most mainstream frameworks, including PyTorch. Although PyTorch is the most widely adopted framework, it imposes a significant restriction by disallowing resolution diversity within batch-level training

## Custom Approach

To overcome the limitations of fixed-size image preprocessing, our architecture introduces a dynamic downsampling strategy that processes images at their native resolution, preserving spatial fidelity and overcoming the constraints of fixed-size preprocessing.

Since images vary in size and aspect ratio, the challenge is how to process all of them while preserving their native resolution and avoiding detail loss, distortion, or interpolation artifacts.

Each image has its own unique resolution (height and width), and The goal of this dynamic downsampling strategy is to process images at their native resolution without resizing, cropping, 
or padding prior to feeding them into the U-Net. A U-Net consists of successive encoder-decoder blocks that downsample and then upsample the image by factors of 2. 

For instance, a compact 234×276 image might be processed through four encoder-decoder blocks, whereas a larger 1007×1347 image could pass through six. In the case of non-square images like 289×1123, the model can adapt by applying downsampling four blocks along its width dimension, but continue downsampling to six blocks along only its height dimension effectively supporting symetric and asymetric downsampling for different aspect ratio.

This results in significantly better preservation of fine details compared to fixed-resolution pipelines. 
This allows the model to preserve fine-grained details of the input image, with the loss function comparing outputs directly to their corresponding native-resolution references


While dynamic resolution handling introduces challenges primarily because PyTorch and most deep learning frameworks do not natively support batch processing of images with varying resolutions, this limitation is addressed by setting the batch size to 1 with parametrable gradient accumulation.


This is a custom approach that challenges the conventions of fixed-size image preprocessing by adapting U-Net depth dynamically to each image’s native resolution. 
While it works within the constraints of existing deep learning frameworks, it avoid their batch-processing limitations and goes beyond standard preprocessing pipelines used in most research.

---

## Details on Implementation

For both **Single_Raw_Unet** and **Reference_Guided_Unet**, the `UnderwaterUnet` class is partially based on my own interpretation and implementation of the paper:

> *Underwater Color Restoration Using U-Net Denoising Autoencoder*  
> (https://arxiv.org/pdf/1905.09000.pdf)  

Since the authors did not release any public implementation.

---

## A Small Challenge to Understand the Logic

To help you better understand the complexity and structure of this project, I intentionally modified the custom ResNet18 model before publishing this repository so that it **cannot be trained on a GPU**. As a result, the version available here is limited to **CPU training only**.

### Challenge:  
Try to modify the code so that training can run on a GPU, such as a T4 GPU on Google Colab.

If you're able to make the necessary changes and get the model training on GPU, it means you've understood at least a small part of the internal logic and design choices of this project.

Feel free to use any resources, including AI tools like ChatGPT, Gemini, or others, and work individually or as a team. The goal is not just to run the code but to understand what prevents GPU training and how to properly enable it.

Good luck — and happy learning!

---

## Important Note

If you use this repository in your research, project, or publication, if you find this project useful whether in part or in whole. consider citing it as a sign of academic integrity:

Lyes, Boudia. 2025. Underwater-enhancement-model. Version 1.0. GitHub: https://github.com/lyes-boudia/Underwater-enhancement-model

It is important to recognize that value doesn’t appear from nowhere. Behind every working piece of code is time, thought, experimentation, and refinement.

This project is shared freely under an open license that requires attribution. That’s a minimal, fair ask in return for something that saves you time, effort, and cost.

## License

This repository is licensed under the [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/).

You are free to use, modify, and share this code for **non-commercial purposes** with proper attribution.  
Commercial use and redistribution are **not permitted**.
