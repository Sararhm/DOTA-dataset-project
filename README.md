# Project Documentation

## Introduction

This project explores the inspiration by the research paper "Adversarial Patch Camouflage against Aerial Detection." This README outlines the process of downloading data, training models, and experimenting with adversarial patches to evaluate their effectiveness.

## Downloading DOTA

Essential to the project was downloading the DOTA dataset and setting up Darknet to train YOLOv2. Downloading and unzipping the DOTA dataset proved to be a significant challenge due to the large size of high-resolution satellite images.

## Training YOLOv2 on DOTA

Training involved multiple attempts to install Darknet, particularly challenges related to compiling with CUDA on a Mac, as no Mac version was available. Alternative solutions involved using VMware to install Ubuntu and install CUDA on it, but memory issues persisted.

## Alternative Approaches

After encountering several obstacles with local setups, the project shifted to Google Colab using Roboflow, a platform that facilitated uploading, labeling, and training datasets.

## DOTA with YOLOv8

Further research led to the use of YOLOv8-OBB, optimized for oriented bounding boxes, providing a more straightforward and efficient training process on the DOTA dataset.

## Experimentation with Adversarial Patches

The final phase involved experimenting with adversarial patches based on the article's descriptions. The process included resizing and applying these patches to images and evaluating their effectiveness in evading detection by the trained model.

## Challenges and Learnings

This project underscored the difficulties in dataset management, the importance of model and data alignment, and the intriguing potential of adversarial patches in object detection evasion. Despite technological hurdles, the project showcased adaptability and continuous learning.

## Conclusion

This project highlights the intersection of AI and security, demonstrating both the capabilities and limitations of current adversarial techniques in machine learning.
