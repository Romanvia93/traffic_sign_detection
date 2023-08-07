## AASD4015 - Advance Applied Mathematical Concepts for Deep Learning

# Project: Traffic Sign Detection

## Group 3
* Thien An Trinh
* Roman Burekhin
* Athira Devan
* Lester Azinge

## Overview
This project aims to train, benchmark and deloy an object detection model to detect 4 types of traffic signs: `traffic light`, `stop`, `speed limit`, and `crosswalk`.

The chosen models for the project are `YOLOv5`, `EfficientDet D1`, `SSD MobileNet FPNLite`, `SSD ResNet50 FPN`, and `Faster R-CNN ResNet50`. There are two frameworks: `YOLOv5` belongs to [Ultralytics](https://github.com/ultralytics/yolov5) and the rest belong to [Tensorflow](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2_detection_zoo.md).

Therefore, this repo consists of two main folders, `yolo` and `Tensorflow`, containing the notebooks of this two frameworks.

Besides, the models were also trained with and without data augmentation (`image scaling`).

The experiment notebooks are also served as HTML pages at:

| With augmentation | Without Augmentation |
|:-|:-|
|[YOLOv5](https://romanvia93.github.io/traffic_sign_detection/Yolov5_w_augmentation.html)|[YOLOv5 w/o aug](https://romanvia93.github.io/traffic_sign_detection/Yolov5_w_o_augmentation.html)|
|[EfficientDet D1](https://romanvia93.github.io/traffic_sign_detection/EfficientDet_D1_640x640.html)|[EfficientDet D1 w/o aug](https://romanvia93.github.io/traffic_sign_detection/EfficientDet_D1_640x640_w_o_augmentation.html)|
|[SSD MobileNet FPNLite](https://romanvia93.github.io/traffic_sign_detection/SSD_MobileNet_v2_FPNLite_640x640.html)|[SSD MobileNet FPNLite w/o aug](https://romanvia93.github.io/traffic_sign_detection/SSD_MobileNet_v2_FPNLite_640x640_w_o_augmentation.html)|
|[SSD ResNet50 FPN](https://romanvia93.github.io/traffic_sign_detection/SSD_ResNet50_V1_FPN_640x640_RetinaNet50.html)|[SSD ResNet50 FPN w/o aug](https://romanvia93.github.io/traffic_sign_detection/SSD_ResNet50_V1_FPN_640x640_RetinaNet50_w_o_augmentation.html)|
|[Faster R-CNN ResNet50](https://romanvia93.github.io/traffic_sign_detection/Faster_RCNN_Resnet50_v1_640x640.html)|[Faster R-CNN ResNet50 w/o aug](https://romanvia93.github.io/traffic_sign_detection/Faster_RCNN_Resnet50_v1_640x640_w_o_augmentation.html)|


## Results
Our experiments showed that, among the tested models, `YOLOv5` is the best. It won in all criteria including precision, speed, size, and training time. 

Therefore, `YOLOv5` was chosen for:
* Video inference (available in `yolo/videos` directory).
* [Streamlit deployment](https://trafficsigns.streamlit.app/) 
About the Streamlit app usage, please refer to the `README.md` file in the `yolo` directory for more details.

Among the TensorFlow models, `SSD MobileNet FPNLite` is the best candidate. Hence, we also chose it to run a realtime webcam test on a local machine. The screen recording of this demo is available in `tensorflow/videos`.


### Comprehensive Report

A comprehensive report that discusses the introduction, methodology, experiments, results and discussion and conclusion of this project was written by the team and is avaible in the `report` directory, both in `pdf` format and in the form of a `Jupyter Notebook`.

The `Jupyter Notebook report` is also served as an [HTML](https://romanvia93.github.io/traffic_sign_detection/traffic_sign_detection_report.html).


### Important Note: 
The notebooks are strongly recommended to be run in Google Colab (click on the link provided at the top of each notebook). There are 2 reasons for this:

* Training these models requires a GPU; otherwise it takes an extremely long time to finish.
* The TensorFlow Model Zoo Object Detection API is deprecated, although it is still a main source fo the TensorFlow pretrained object detection models.

Because the TensorFlow object detection API is no longer supported, there are many package-related conflicts during the training, evaluation, and inference.  
For example: training and evaluating the same model require different Pillow versions. (Please refer to the notebooks for more details and instructions).

When doing our experiments, we solved this problem by putting necessary cells in a correct order and executing cell by cell in a notebook. Therefore, our recommendation is not to run the TensorFlow notebooks locally, but rather train the model on Google Colab and save the trained model for later inference, as we did in the notebooks.

For the same reasons, the `requirements.txt` file only lists the packages required for converting a notebook to a HTML (because we do not train the models locally) and for producing the project report in the form of a Jupyter Notebook.  
In the `yolo` folder, there is another `requirements.txt` that lists the packages for deploying the YOLO model.

## Additional Information
* Python version: 3.10
* SSL error on Mac: open a terminal and run `/Applications/Python\ 3.10/Install\ Certificates.command`
