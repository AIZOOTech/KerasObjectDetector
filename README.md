# Keras Object Detection API (YOLK)

_You Only Look Keras :fried_egg:_

![Object](https://img.shields.io/badge/Object-Detector-Yellow.svg)
![Language](https://img.shields.io/badge/Language-Python-blue.svg)
[![DeepLearning](https://img.shields.io/badge/DeepLearning-Keras-red.svg)](https://keras.io)
[![KerasKorea](https://img.shields.io/badge/Community-KerasKorea-purple.svg)](https://www.facebook.com/groups/KerasKorea/)
[![KerasKorea](https://img.shields.io/badge/2019-Contributhon-green.svg)](https://www.kosshackathon.kr/)

<p align="center">
  <img width="509" height="276" src="https://user-images.githubusercontent.com/23257678/65056804-81fdb180-d9ac-11e9-931b-d027649c67cc.png" alt="">
</p>

As a 2019 Open Source Countibuthon Project, we create Kears Object Detection API.  
The purpose of Keras Object Detection API is to make it easy and fast so that everyone can create their own Object Detection model without difficulty.
Detailed instructions for use will be updated at a later. You can look forward to it. 🤓

## Contents
* [Directory Structure](#Directory-Structure)
* [Installation](#Installation)
* [Testing](#Testing)
<<<<<<< HEAD
* ~~[Training](#Training)~~
* ~~[Usage](#Usage)~~
=======
* [Training](#Training)
* [Usage](#Usage)
>>>>>>> ef208bb6ea843ab0b70842f851daeac477405f6f
* [Dependencies](#Dependencies)
* [Release information](#Release-information)
* [Contributors](#Contributors)

## Directory Structure
<<<<<<< HEAD
<!--need to edit-->
=======
>>>>>>> ef208bb6ea843ab0b70842f851daeac477405f6f
```
KerasObjectDetector
├── README.md
├── setup.py
├── setup.md
├── datasets
├── utils
│   ├── image1.png
│   ├── image2.jpeg
│   ├── result_image.png
│   ├── show_bbox.py
│   ├── test.py...
```

## Installation (On Linux)

<<<<<<< HEAD
First, [Download YOLK API](https://github.com/KerasKorea/KerasObjectDetector) that help to set up development environment for working on object detection. Enter the following command in terminal.

```bash
  # Download YOLK API
=======
First, [Download YOLK package](https://github.com/KerasKorea/KerasObjectDetector). And, Set up development environment for working on YOLK. 터미널에서 밑의 명령어를 입력하시오

```bash
>>>>>>> ef208bb6ea843ab0b70842f851daeac477405f6f
  $ git clone https://github.com/KerasKorea/KerasObjectDetector.git
  $ cd KerasObjectDetector

  # If there is no 'setuptools' in docker, please download This package.
  # pip install setuptools
  # install library
  $ apt-get install libatlas-base-dev libxml2-dev libxslt-dev python-tk
  
  # build setup code
  # ./KerasObjectDetector
  $ python setup.py install
```

<<<<<<< HEAD
If you want to running on Docker, Get Docker Image we made and easily configure development environment.(Later, It will be upload on Docker Hub)
=======
If you want to use Docker, Get Docker Image we made and easily configure development environment.
>>>>>>> ef208bb6ea843ab0b70842f851daeac477405f6f

```bash
  # ./KerasObjectDetector
  $ docker run --name=yolk -Pit
  # start yolk container
  $ docker start yolk
```
<<<<<<< HEAD
=======
<!-- 이미지 다운로드-->
```python
  # 코드 형식 참고 - https://keras.io/applications/#fine-tune-inceptionv3-on-a-new-set-of-classes
  import keras
  import yolk

  voc_train, voc_valid = yolk.datasets.pascal_voc07()

  load_model = load_model(model_path, backbone_name='resnet50')

  preds = model.predict_detection(x) # preds = (boxes, scores, labels)
  # ㄴmodel.convert2pred_model() 
  #   ㄴmodel.add(yolk.layers.yolo_predict_layer())
  #     yolk.models.yolov3() 선언할 때 Sequential(name="yolov3") 해주고
  #     여기에 맞춰서 각 모델에 맞는 convert_model() 함수 호출

  # bbox 포함한 결과 plotting
  plt = yolk.plotter(preds)
  plt.plot()
```
>>>>>>> ef208bb6ea843ab0b70842f851daeac477405f6f

## Testing
<!-- used by inference -->
You can test your image with YOLK API. Enter the following command in terminal.

<<<<<<< HEAD
```bash
  # ./
  # python examples/retinanet_inference_example.py --filepath 000000008021.jpg
```
`retinanet_inference_example.py` is as follows. If you want to know object detection more logically, Go to [this tutorial]().

```python
  import sys, os
  sys.path.insert(0, os.path.abspath('..'))
  import yolk
  from PIL import Image

  # import miscellaneous modules
  import matplotlib.pyplot as plt
  import cv2
  import numpy as np

  def main():
      # Enter your image path for test (in `Image.open(here!!)`)
      image = np.asarray(Image.open('000000008021.jpg').convert('RGB'))
      image = image[:, :, ::-1].copy()
      # Return image info and scale
      image, scale = yolk.detector.preprocessing_image(image)

      # Approach a pretrained-retinanet (inference)
      model_path = os.path.join('..', 'resnet50_coco_best_v2.1.0.h5')
      model = yolk.detector.load_model(model_path)

      # Return bounding box, score, classes(it's labels) passed by the model
      boxes, scores, labels = model.predict_on_batch(np.expand_dims(image, axis=0))

      # Print bounding box in image
      print(boxes)
      
  if __name__ == '__main__':
      main()
```
## Training
_to be added later..._

## Dependencies
|Name|Version(Min)|
|---|---|
|Tensorflow|1.14.0|
|Keras|2.3.0|
|Python|3.6|
|Numpy|1.14|
|Matplotlib||
|SciPy|0.14|
|h5py||
|Pillow||
|progressbar2||
|opencv-python|3.3.0|
|six|1.9.0|
|PyYAML||
|Cython||

## Release information
#### ver 1.0.0 (November 20, 2019) 
Finally, API that can detect multiple objects in keras has been completed!! There are still many things to supply, but we plan to continue to update. This release includes: 

1. A three of object detetion model and a data generator that changes in a suitable data format for selected model. 
    - Object Detection Models : [SSD](https://github.com/pierluigiferrari/ssd_keras), [YOLOv3](), [RetinaNet](https://github.com/fizyr/keras-retinanet)
    - Dataset and data generator : [PASCAL VOC2012](), [COCO](), [Custom dataset]() <!--need to description-->
      ㄴ Yolk's dataset downloader is 3X faster than existing downloader.
2. Docker files that help to set up easliy development environment.
3. Easy & Detail Obejct Detection Tutorial (SSD+VOC2012)

## Contributors
Thanks goes to these beautiful peaple (github ID) :
[@fuzzythecat](), [@mijeongjeon](), [@tykimos](), [@SooDevv](), [@karl6885](), [김준영](), [@minus31](), [김형섭](), [최민영](), [@mike2ox](), [홍석주](), [박근표](), [박아정](), [@parkjh688](), [유원상](), [@simba328](), [@visionNoob](), [이혜리](), [임재곤](), [전지영](), [@ahracho]()
=======
## Training

## Usage

## Dependencies

|Tool|Version|
|---|---|
|python|3.6|
|tensorflow|1.14.0|
|keras|2.3.0|

## Release information

## Contributors
>>>>>>> ef208bb6ea843ab0b70842f851daeac477405f6f
