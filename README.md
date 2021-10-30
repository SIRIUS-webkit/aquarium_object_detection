# Aquarium Object Detection

Life in the sea: it’s a whole other world down there. Underwater animals are widely varied and have adapted to their different environments across our planet’s marine habitats.
In this repository, we will build an aquarium object detection system using [yolov5](https://github.com/ultralytics/yolov5).

There are 7 classes that we detected.

"fish", "jellyfish", "penguin", "puffin", "shark", "starfish", "stingray"

![test image](https://github.com/SIRIUS-webkit/aquarium_object_detection/blob/master/assets/test.jpg)

# Dataset

The dataset that we used in this repo was owned by Roboflow team from two aquariums in the United States: The Henry Doorly Zoo in Omaha (October 16, 2020) and the National Aquarium in Baltimore (November 14, 2020). The dataset consists of 638 images splitted into train, test and validation data. The dataset can be downloaded at [roboflow dataset](https://public.roboflow.com/object-detection/aquarium/2).
I also provide the dataset that I used at my github repo [dataset](https://github.com/SIRIUS-webkit/aquarium_object_detection/tree/master/dataset)

![image](https://images.twinkl.co.uk/tw1n/image/private/t_630/u/ux/butterfly-fish_ver_1.jpg)

# Model

We will be using yolov5s model. Yolov5s model is the smallest model and it has also good mAP. Larger models like YOLOv5x and YOLOv5x6 will produce better results in nearly all cases, but have more parameters, require more CUDA memory to train, and are slower to run. So, we used the smallest model for aquarium object detection.

| Model                                                     | size | mAP  | Speed | Params | FLOPs |
| --------------------------------------------------------- | ---- | ---- | ----- | ------ | ----- |
| [Yolov5s](https://github.com/ultralytics/yolov5/releases) | 640  | 37.2 | 98    | 7.2    | 16.5  |

**Recommed** => [yolov5s](https://github.com/ultralytics/yolov5/releases)

# Train Custom Data

If you don't use **google drive** for dataset, you don't need to run this,

```python
!unzip -q /content/drive/MyDrive/Aquarium/dataset.zip -d ../
```

Otherwise, you can directly use as my repo.

Before you run this,

```python
!python train.py --img 312 --data custom_data.yaml --epochs 300 --batch-size 16 --bbox_interval 1 --weights 'yolov5s.pt'
```

you must add [custom_data.yaml](https://github.com/SIRIUS-webkit/aquarium_object_detection/blob/master/custom_data.yaml) to the yolov5 -> data

You can change whatever you want like **img size**, **batch size**, **epoches** etc.

# Video Result

https://github.com/SIRIUS-webkit/aquarium_object_detection/blob/master/assets/lv_0_20211030123922.mp4

# Results

After training for 300 epoches,

![confusion matrix](https://github.com/SIRIUS-webkit/aquarium_object_detection/blob/master/assets/confusion_matrix.png)

![result](https://github.com/SIRIUS-webkit/aquarium_object_detection/blob/master/assets/results.png)

# References

[Train Custom Data Using Yolov5](https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data)
