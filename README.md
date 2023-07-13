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
4. Change directories into `jetson-inference/python/training/classification/data`.
5. Create a directory named "mushroom".
6. Inside the directory create a file name "labels.txt".
7. Write the name of nine species into the file labels.txt. Each name should be in a different line and leave an empty line below.
8. Inside the directory "mushroom" create three directories named "train", "val", and "test".
9. Create 9 directories named "Agaricus", "Amanita", "Boletus", "Cortinarius", "Entoloma", "Hygrocybe", "lactarius", "Russula", "Suillus" iside each of the three directories "train", "val", and "test".
10. Put 5% of "Agaricus" images into the directory `val/Agaricus`.
11. Put 5% of different "Agaricus" images into the directory `test/Agaricus`.
12. Put the rest "Agaricus" images into the directory `train/Agaricus`
13. Do the similar thing to the other 8 sets of images from step 8~10.
14. Make a new directory called "mushroom" in `jetson-inference/python/training/classification/models`

Execution
1. Go to directory `jetson-inference`.
2. Run a docker by typing `./docker/run.sh`.
3. Change directories to `jetson-inference/python/training/classification`
4. Train the model by running this command in the terminal `python3 train.py --model-dir=models/mushroom data/mushroom --epochs=200`. This step will take a few hours, or maybe a day.
5. Once the model is trained, export it by typing in the terminal `python3 onnx_export.py --model-dir=models/mushroom`.
6. exit the docker by pressing ctrl d.
7. Change directories to `jetson-inference/python/training/classification`.
8. In the terminal type `NET=models/mushroom` and `DATASET=data/mushroom`.
9. Then enter in `imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/Agaricus/009_mrv34Sn4WiQ.jpg output.jpg` to test the model.
10. look at your test result in the directory `classification`.
