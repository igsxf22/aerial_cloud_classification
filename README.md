[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/igsxf22/aerial_cloud_classification/blob/main/Aerial_Clouds_Clear_Classification_Experiment.ipynb)


# Aerial Cloud / Clear Classification
Research project - create a prototype classification model to identify cloudy and clear aerial imagery frames, without a purpose-made "cloud" vs "clear" dataset, using only publicly available data.

This project uses YOLOv11n classification model with open-source labeled datasets to create a small, binary classification model for "clouds" or "clear". 

> Since we don't actually want to label any data, we'll jam together a nice ground-to-sky angle dataset of different types of clouds, which usually fill the entire frame, with an aerial land use dataset, which has limited or no clouds in the frames.

Inference against drone video, not part of dataset:

![Video Test Results](https://github.com/igsxf22/aerial_cloud_classification/blob/main/cloud_class_test_640.gif)
<br>`source: https://www.youtube.com/watch?v=1DOc8aZDtGU`

Limitations: Doesn't work well on clear images where you can see the horizon - its intended mostly for steep or nadir image angles

Datasets:
  - [RESISC45 data from HuggingFace](https://huggingface.co/datasets/tanganke/resisc4)
    > 31,500 images, 45 classes, including one 'cloud' category<br>
    > 256x256 RGB<br>
  - [TJNU-Ground-based-Cloud-Dataset](https://github.com/shuangliutjnu/TJNU-Ground-based-Cloud-Dataset/tree/main)
    > 19000 images: 7 classes, 6 for different types of clouds and 1 for clear sky.<br>
    > 512x512 RGB

Merged dataset:
  - **Clouds**: the one cloud class from the aerial dataset and the 6 cloud classes from the ground dataset
  - **Clear**: the 44 other classes from the aerial dataset showing land features and the 1 "clear sky" class from the ground-based cloud dataset
  - Resized the cloud dataset to the res45 image size of 256x256 RGB

Inference against random test set sample:
![Mosaic Test Results)](https://github.com/igsxf22/aerial_cloud_classification/blob/main/mosaic.jpg)

Limits:
  1. Doesn't work well on clear images where you can see the horizon - its intended for steep image angles
