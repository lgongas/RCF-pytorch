### Richer Convolutional Features for Edge Detection
Thanks to <a href="https://github.com/yun-liu">yun-liu's</a> help.
Created by XuanyiLi, if you have any problem in using it, please contact:xuanyili.edu@gmail.com.
The best result of my pytorch model is *** ODS F-score now.
### For Fun：smile:
![gif](https://github.com/meteorshowers/RCF-pytorch/blob/master/doc/titannic.gif)
#### my model result
the following are the side outputs and the prediction example
Adam no tunelr 1e-4:
![prediction example](https://github.com/meteorshowers/RCF-pytorch/blob/master/doc/326025.jpg)
#### When I add dilation, the world changes, Look Here! what's up(TRAINING PROCESS! NOT RESULT) 
![train example](https://github.com/meteorshowers/RCF-pytorch/blob/master/doc/iter-450.jpg)
### When I add dilation, the world changes, Look Here! what's up(RESULT) 
![prediction example](https://github.com/meteorshowers/RCF-pytorch/blob/master/doc/2018.jpg)
### Citation
If you find our work useful in your research, please consider citing:

        @inproceedings{liu2017richer,
        title={Richer Convolutional Features for Edge Detection},
        author={Liu, Yun and Cheng, Ming-Ming and Hu, Xiaowei and Wang, Kai and Bai, Xiang},
        journal={Proceedings of the IEEE conference on computer vision and pattern recognition},
        year={2017}
        }

### Introduction
I implement the edge detection model according to the <a href="https://github.com/yun-liu/rcf">RCF</a>  model in pytorch. 

the result of my pytorch model will be released in the future

| Method |ODS F-score on BSDS500 dataset |ODS F-score on NYU Depth dataset|
|:---|:---:|:---:|
|ours(adam1e-4)| 0.764(epoch10) | *** |
|ours(adam1e-4-tunelr-caffecrop)| 0.786(epoch6) 0.786(epoch10) | *** |
|ours(sgd1e-6-tunelr-caffecrop)| 0.784(epoch10) | *** |
|ours(sgd1e-6-tunelr-caffecrop-fixbalanceweightto1.1)| 0.784(epoch10) | *** |
|ours(sgd5e-6-tunelr-caffecrop-fixbalanceweightto1.1)| 0.786(epoch10) | *** |
|ours(sgd1e-6-tunelr-centercrop-fixbalanceweightto1.1-adddilation)| notest because sideput5 error pattern i think is kai's trans and upsample' error | *** |
|ours(sgd1e-6-tunelr-centercrop-fixbalanceweightto1.1-adddilation-changetranscroptoupsample)| 0.780（epoch10）(error way stride is wrong with 16) | *** |
|ours(sgd1e-6-tunelr-centercrop-fixbalanceweightto1.1-adddilation-stridewith8)| 0.786（epoch9）| *** |
|ours(sgd5e-7-tunelr-centercrop-fixbalanceweightto1.1-adddilation-stridewith8)-MS-BSDS+pascal| 0.805（epoch7）0.804(epoch12) 0.804(epoch16) | *** |
|ours(sgd5e-7-tunelr-centercrop-fixbalanceweightto1.1-adddilation-stridewith8)-MS-BSDS+pascal-result-rescale| 0.805（epoch7） | *** |
|ours(sgd5e-7-tunelr-centercrop-fixbalanceweightto1.1-adddilation-stridewith8)-MS-BSDS+pascal-result-rescale-caffereadimgway| 0.807(epoch7) | *** |
|ours(sgd1e-6-tunelr(changeconv5 lr*80/lr*160 beacuse training collaps when add voc,this is different with caffe version told by liu, this is different and important)-centercrop-fixbalanceweightto1.1-adddilation-stridewith8)-MS-BSDS+pascal-result-rescale-caffereadimgway-stepsize2| 0.804(epoch7) | *** |
|ours(adam1e-5-tunelr-centercrop-fixbalanceweightto1.1-adddilation-stridewith8)-MS-BSDS+pascal-result-rescale-caffereadimgway| 0.801(epoch(9)) | *** |
|ours(sgd5e-6-tunelr-centercrop-fixbalanceweightto1.1-adddilation)| error learing(because wrong stride with 16) | *** |
| Reference[1]| 0.806(0.798)  | ***  |


### Installation

Install <a href="https://pytorch.org/">pytorch</a>. The code is tested under 0.4.1 GPU version and Python 3.6  on Ubuntu 16.04. There are also some dependencies for a few Python libraries for data processing and visualizations like `cv2` etc. It's highly recommended that you have access to GPUs.

### Usage

#### image edge detection

To train a RCF model on BSDS500:

        python train_RCF.py

If you have multiple GPUs on your machine, you can also run the multi-GPU version training:

        CUDA_VISIBLE_DEVICES=0,1 python train_multi_gpu.py --num_gpus 2

After training, to evaluate:

        python evaluate.py (for further work)

<i>Side Note:</i>  Hello mingyang, I love you

### License
Our code is released under MIT License (see LICENSE file for details).

### Updates

### To do 
* Add support for multi-gpu training for the edge detetion task.
* Improve the performance to 0.811 in the original paper.
* Add a gpu version of edge-eval code to accelerate the evaluation process.
* Note the difference between PIL(Image) and opencv read. RCF(caffe) use opnecv in training and PIL in test.
However, I use PIL all the time. this is different.

### Related Projects
[1] <a href="https://github.com/yun-liu/rcf">Richer Convolutional Features for Edge Detection</a> 

[2] <a href="https://github.com/s9xie/hed">HED</a> 

[3] <a href="https://github.com/zeakey/hed">HED</a> created by <a href="https://github.com/zeakey">zeakey's</a>
