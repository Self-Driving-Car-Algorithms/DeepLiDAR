# DeepLiDAR
This repository contains the code (in PyTorch) for "[DeepLiDAR: Deep Surface Normal Guided Depth Prediction for Outdoor Scene
from Sparse LiDAR Data and Single Color Image](http://openaccess.thecvf.com/content_CVPR_2019/papers/Qiu_DeepLiDAR_Deep_Surface_Normal_Guided_Depth_Prediction_for_Outdoor_Scene_CVPR_2019_paper.pdf)" paper (CVPR 2019) by [Jiaxiong Qiu](https://jiaxiongq.github.io/), [Zhaopeng Cui](https://zhpcui.github.io/), [Yinda Zhang](https://www.zhangyinda.com/), [Xingdi Zhang](https://github.com/crazyzxd), [Shuaicheng Liu](http://www.liushuaicheng.org/), Bing Zeng and [Marc Pollefeys](https://www.inf.ethz.ch/personal/marc.pollefeys/index.html).
## Introduction
In this work, we propose an end-to-end deep learning system to produce dense depth from sparse LiDAR data and a color image taken from outdoor on-road scenes leveraging surface normal as the intermediate representation.
![image](https://github.com/JiaxiongQ/Need2Adjust/blob/master/pipline.PNG)
## Requirements
- [Python2.7](https://www.python.org/downloads/)
- [PyTorch(0.4.0+)](http://pytorch.org)
- torchvision 0.2.0 (higher version may cause issues)
- [KITTI Depth Completion](http://www.cvlibs.net/datasets/kitti/eval_depth.php?benchmark=depth_completion)
- [Our synthetic dataset based on CARLA](https://pan.baidu.com/s/1ayNWa7_9Ia2f6_lYzW8paA)
### The Details about Our Synthetic dataset
You could ignore the folders named 'lidar_m', 'normal_s', 'RGBright' and 'Boundary'. (Maybe you also can use the for your own purpose)
```
'DepthLeft': The raw depth generated by CARLA, you can see the details in here [CARLA](https://carla.readthedocs.io/en/latest/cameras_and_sensors/#sensorcameradepth)
'lidar': The lidar depth which projected into the camera coordinate. Each image is coded by 16-bit like KITTI.
'Lidar64': The raw lidar point cloud information.
'Normal_m': The surface normal calculated from 'DepthLeft'.
'RGBLeft': The RGB images.
```
### Pretrained Model
※NOTE: The pretrained model were saved in '.tar'; however, you don't need to untar it. Use torch.load() to load it.

[Download Link](https://drive.google.com/file/d/1eaOCtl_CGzqqqJDbVawsdniND255ZaP8/view?usp=sharing)
## Train
1. Get the surface normal of Lidar dataset by running the code in the project named ['surface_normal'](https://github.com/crazyzxd).
2. Use the training strategy in the folder named 'trainings'.
## Evaluation
1. Fill the names of the folders in 'test.py':
```
'gt_fold': the location of your groundtruth folder;
'left_fold': the location of your RGB image folder;
'lidar2_raw': the location of your Sparse(LiDAR) depth folder.
```
 
2. Use the following command to evaluate the trained on your own data.
```
python test.py --loadmodel (your trained model)
```
## Citation 
If you use our code or method in your work, please cite the following:
```
@InProceedings{Qiu_2019_CVPR,
author = {Qiu, Jiaxiong and Cui, Zhaopeng and Zhang, Yinda and Zhang, Xingdi and Liu, Shuaicheng and Zeng, Bing and Pollefeys, Marc},
title = {DeepLiDAR: Deep Surface Normal Guided Depth Prediction for Outdoor Scene From Sparse LiDAR Data and Single Color Image},
booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
month = {June},
year = {2019}
}
```
Please direct any questions to [Jiaxiong Qiu](https://jiaxiongq.github.io/) at qiujiaxiong727@gmail.com

