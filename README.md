# Detailed Human Shape Estimation from a Single Image by Hierarchical Mesh Deformation

Hao Zhu, Xinxin Zuo, Sen Wang, Xun Cao, Ruigang Yang &nbsp; &nbsp; CVPR 2019 Oral

**[[project page]](http://cite.nju.edu.cn/human_shape.html)** &nbsp; &nbsp; **[[paper]](http://cite.nju.edu.cn/Haozhu/Detailed%20Human%20Shape%20Estimation%20from%20a%20Single%20Image%20by%20Hierarchical%20Mesh%20Deformation.pdf)**

<img src="https://github.com/zhuhao-nju/hmd/blob/master/demo/results/2726.gif" width="200"> <img src="https://github.com/zhuhao-nju/hmd/blob/master/demo/results/0002.gif" width="200"> <img src="https://github.com/zhuhao-nju/hmd/blob/master/demo/results/0477.gif" width="200"> <img src="https://github.com/zhuhao-nju/hmd/blob/master/demo/results/2040.gif" width="200">

From green bounded frame:
**source image** --> **initial guess** --> **joint deform** -->  **anchor deform** --> **vertex deform**

## Requirements
The project is tested on ubuntu 16.04 with python 2.7, PyTorch 1.0.  We recomend using [Anaconda](https://www.anaconda.com/download/#linux) to create a new enviroment:
```
conda create -n py27-hmd python=2.7
conda activate py27-hmd
```

Install dependecies:
```
sudo apt-get install libsuitesparse-dev
pip install -r requirements.txt
```

The installation of OpenDR is unstable now, we recommend using a old stable version:
```
pip install pip==8.1.1
pip install opendr==0.76
pip install --upgrade pip
```

Refer to the [guide](https://pytorch.org/get-started/locally/) to install the PyTorch 1.0.

## Demo
Download the pretrained model:
```
cd demo
chmod +x download_pretrained_model.sh
./download_pretrained_model.sh
```
Run the demo:
```
python demo.py --ind 2 # or 477, 2040, 2726
```
The results will be saved in the folder "demo/results/" by default.  Run "python demo.py -h" for more usages.

This repository merely contains 4 samples for demo. To run the full test data, download the test set from [Google Drive](https://drive.google.com/open?id=1ifcvLFJb1t9uS9bz0CxqhaYUfXvQNHC4) or [Baidu Cloud](https://pan.baidu.com/s/1OVfM4ETgkFiUgmGpp0Cb4A)(extracting code:0ch3).  Extract the test set and change the "dataset_path" in "conf.ini" to the extracted location.  The range of test data number is [0-4624].  You can also follow the instructions in the "Data preparation" part to generate testing data together with training data.

In the generation of the dataset, we predicted the initial mesh using [HMR](https://github.com/akanazawa/hmr) and saved it as "/para/\*.json" files.  To test on images beyond the dataset, you have to run HMR to get the initial mesh firstly.  The demo for images beyond the test set will be added in the near future.

## Data preparation
Please see the [datasets/data.md](https://github.com/zhuhao-nju/hmd/blob/master/datasets/data.md).

## Citation
If you find this project useful for your research, please consider citing:
```
@inproceedings{zhu2019detailed,
  title={Detailed human shape estimation from a single image by hierarchical mesh deformation},
  author={Zhu, Hao and Zuo, Xinxin and Wang, Sen and Cao, Xun and Yang, Ruigang},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2019}
}
```

