# Aerial Cloud Classification
Research project - prototype classification model to identify cloudy and clear aerial imagery frames

This project uses YOLOv11n classification model with open-source labeled datasets to create a small, binary classification model for "clouds" or "clear"

Datasets:
  - [Datasets: neerajxa/Aerial-Image](https://huggingface.co/datasets/neerajx0/Aerial-Image)<br><br>
    > 4500 images: 45 classes with 100 images each, including one 'cloud' category<br>
    > 256x256 RGB<br>
    > This appears to be a subset of the [RESISC45 dataset](https://github.com/tensorflow/datasets/blob/master/docs/catalog/resisc45.md) but is labeled AID
  - [TJNU-Ground-based-Cloud-Dataset](https://github.com/shuangliutjnu/TJNU-Ground-based-Cloud-Dataset/tree/main)
    > 19000 images: 7 classes, 6 for different types of clouds and 1 for clear sky.

Merged dataset:
  - **Clouds**: the one cloud class from the aerial dataset and the 6 cloud classes from the ground dataset
  - **Clear**: the 44 other classes from the aerial dataset showing land features and the 1 "clear sky" class from the ground-based cloud dataset

Inference against drone video, not part of dataset:

![Video Test Results](https://github.com/igsxf22/aerial_cloud_classification/blob/main/cloud_class_test_640.gif)

Inference against random test set sample:
![Mosaic Test Results)](https://github.com/igsxf22/aerial_cloud_classification/blob/main/mosaic.jpg)

Limits:
  1. Doesn't work well on clear images where you can see the horizon - its intended for steep image angles
