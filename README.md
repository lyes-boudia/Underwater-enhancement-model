# Underwater images Enhancement Model

This repository contains my personal implementation of the third stage of my Master’s thesis on the topic of **Combination of Deep Learning Techniques and
Classical Methods for Underwater Images Enhancement**, proposed and supervised by Professor: **José Luis Lisani Roca**.

It includes three **UNet-based architectures** for underwater image enhancement, each implemented as a Jupyter Notebook. These notebooks are designed to be easy to follow and work in most environments and operating systems.

These implementations are partially based on assignments I completed for a deep learning subject provided by Professor: **Miguel Ángel Calafat Torrens**. 
All of them are also available in my [Deep Learning repository](#), which contains a collection of powerful implementations and carefully designed challenges.

This repository serves as a strong foundation for anyone looking to build expertise and excel in the field of deep learning.

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
