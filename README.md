# FeatureFlow

[Paper](https://github.com/CM-BF/FeatureFlow/blob/master/paper/FeatureFlow.pdf) | [Supp](https://github.com/CM-BF/FeatureFlow/blob/master/paper/Supp.pdf)

A state-of-the-art Video Frame Interpolation Method using deep semantic flows blending.

FeatureFlow: Robust Video Interpolation via Structure-to-texture Generation (IEEE Conference on Computer Vision and Pattern Recognition 2020)

## To Do List
- [x] Preprint
- [ ] Training code

## Table of Contents

1. [Requirements](#requirements)
1. [Demos](#video-demos)
1. [Installation](#installation)
1. [Pre-trained Model](#pre-trained-model)
1. [Download Results](#download-results)
1. [Evaluation](#evaluation)
1. [Test your video](#test-your-video)
1. [Citation](#citation)

## Requirements

* Ubuntu
* PyTorch (>=1.1) 
* Cuda (>=10.0) & Cudnn (>=7.0)
* mmdet 1.0rc (from https://github.com/open-mmlab/mmdetection.git)
* visdom (not necessary)
* NVIDIA GPU

## Video demos

Click the picture to Download one of them or click [Here(Google)](https://drive.google.com/open?id=1QUYoplBNjaWXJZPO90NiwQwqQz7yF7TX) or [Here(Baidu)](https://pan.baidu.com/s/1J9seoqgC2p9zZ7pegMlH1A)(key: oav2) to download **360p demos**.

**360p demos**(including comparisons):

[<img width="320" height="180" src="https://github.com/CM-BF/FeatureFlow/blob/master/data/figures/youtube.png"/>](https://github.com/CM-BF/storage/tree/master/videos/youtube.mp4 "video1")
[<img width="320" height="180" src="https://github.com/CM-BF/FeatureFlow/blob/master/data/figures/check_all.png"/>](https://github.com/CM-BF/storage/tree/master/videos/check_all.mp4 "video2")
[<img width="320" height="180" src="https://github.com/CM-BF/FeatureFlow/blob/master/data/figures/tianqi_all.png"/>](https://github.com/CM-BF/storage/tree/master/videos/tianqi_all.mp4 "video3")
[<img width="320" height="180" src="https://github.com/CM-BF/FeatureFlow/blob/master/data/figures/video.png"/>](https://github.com/CM-BF/storage/tree/master/videos/video.mp4 "video4")
[<img width="320" height="180" src="https://github.com/CM-BF/FeatureFlow/blob/master/data/figures/shana.png"/>](https://github.com/CM-BF/storage/tree/master/videos/shana.mp4 "video5")

**720p demos**:

[<img width="320" height="180" src="https://github.com/CM-BF/FeatureFlow/blob/master/data/figures/SYA_1.png"/>](https://github.com/CM-BF/storage/tree/master/videos/SYA_1.mp4 "video6")
[<img width="320" height="180" src="https://github.com/CM-BF/FeatureFlow/blob/master/data/figures/SYA_2.png"/>](https://github.com/CM-BF/storage/tree/master/videos/SYA_2.mp4 "video7")

## Installation
* clone this repo
* git clone https://github.com/open-mmlab/mmdetection.git
* install mmdetection: please follow the guidence in its github
```bash
$ cd mmdetection
$ pip install -r requirements/build.txt
$ pip install "git+https://github.com/cocodataset/cocoapi.git#subdirectory=PythonAPI"
$ pip install -v -e .  # or "python setup.py develop"
$ pip list | grep mmdet
```
* Download [test set](http://data.csail.mit.edu/tofu/testset/vimeo_interp_test.zip)
```bash
$ unzip vimeo_interp_test.zip
$ cd vimeo_interp_test
$ mkdir sequences
$ cp target/* sequences/ -r
$ cp input/* sequences/ -r
```
* Download BDCN's pre-trained model:bdcn_pretrained_on_bsds500.pth to ./model/bdcn/final-model/
```
$ pip install scikit-image visdom tqdm prefetch-generator
```

## Pre-trained Model

[Google Drive](https://drive.google.com/open?id=1S8C0chFV6Bip6W9lJdZkog0T3xiNxbEx)

[Baidu Cloud](https://pan.baidu.com/s/1LxVw-89f3GX5r0mZ6wmsJw): ae4x

Place FeFlow.ckpt to ./checkpoints/.

## Download Results

[Google Drive](https://drive.google.com/open?id=1OtrExUiyIBJe0D6_ZwDfztqJBqji4lmt)

[Baidu Cloud](https://pan.baidu.com/s/1BaJJ82nSKagly6XZ8KNtAw): pc0k

## Evaluation
```bash
$ CUDA_VISIBLE_DEVICES=0 python eval_Vimeo90K.py --checkpoint ./checkpoints/FeFlow.ckpt --dataset_root ~/datasets/videos/vimeo_interp_test --visdom_env test --vimeo90k --imgpath ./results/
```

## Test your video
```bash
$ CUDA_VISIBLE_DEVICES=0 python sequence_run.py --checkpoint checkpoints/FeFlow.ckpt --video_path ./yourvideo.mp4 --t_interp 4 --slow_motion
```
`--t_interp` sets frame multiples, only power of 2(2,4,8...) are supported. Use flag `--slow_motion` to slow down the video which maintains the original fps.

The output video will be saved as output.mp4 in your working diractory. 

## Citation
```
@InProceedings{FeatureFlow,
author = {Gui, Shurui and Wang, Chaoyue and Chen, Qihua and Tao, Dacheng},
title = {FeatureFlow: Robust Video Interpolation via Structure-to-texture Generation},
booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
month = {June},
year = {2020}
}
```

## Contact
[Shurui Gui](mailto:citrinegui@gmail.com); [Chaoyue Wang](mailto:chaoyue.wang@sydney.edu.au)

## License
See [MIT License](https://github.com/CM-BF/FeatureFlow/blob/master/LICENSE)
