# Mushroom-specie-separator

This project separates some of the common mushrooms into 9 species.

![A picture of an Amanita (mushroom)](https://github.com/WalmartbagLu/Mushroom-specie-separator/assets/138505874/4a6f0f4e-938e-48e4-a06a-b5139bb22d0b)

## The Algorithm

The project is a network based on jetson-nano and uses a resnet 18 model. The network is retrained with 9 datasets including 9 different species of mushrooms wich are Agaricus, Amanita, Boletus, Cortinarius, Entoloma, Hygrocybe, lactarius, Russula, Suillus. The final model is exported using ONNX format. When the model finished training the first epoch, the accuracy was about 11%. When the model was trained for 50 epochs, the accuracy reached 50%. Since the size of datasets were massive and their were 9 groups, it takes a long time for the model to increase its accuracy.

jetson-nano is a computer designed to power entry-level edge AI applications and devices with a single tegra x1 GPU.
![A picture of jetson-nano](https://github.com/WalmartbagLu/Mushroom-specie-separator/assets/138505874/32851ff6-9252-4b41-a2a3-ec96c145d6bf)

The dataset used for this project: https://www.kaggle.com/datasets/lizhecheng/mushroom-classification?select=archive

## Running this project

Preparation
1. Connect PuTTY and VSCode to the jetson-nano.
2. Download the jetson-inference container from github to the jetson-nano: https://github.com/dusty-nv/jetson-inference
3. Download dataset of mushrooms from the website: https://www.kaggle.com/datasets/lizhecheng/mushroom-classification?select=archive
4. Change directories into `jetson-inference/python/training/classification/data`
5. create a folder 
6. Create three folders named "train", "val", and "test".
7. Create 9 folders named "Agaricus", "Amanita", "Boletus", "Cortinarius", "Entoloma", "Hygrocybe", "lactarius", "Russula", "Suillus".
8. Put 5% of "Agaricu"s images into the val/

[View a video explanation here](video link)
