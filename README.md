# LRCN and Temporal CNN for Activity Recognition #

[Chih-Yao Ma](http://shallowdown.wix.com/chih-yao-ma)\*, Min-Hung Chen\* 

(\* equal contribution)

---
## Abstract 
We examine and implement several leading techniques for Activity Recognition (video classification), while proposing and investigating a novel convolution on temporally-constructed feature vectors.

#### How we tackle Activity Recognition problem? 
CNN as baseline, CNN + RNN [(LRCN)](http://jeffdonahue.com/lrcn/), Temporal CNN

<table align = "center">
<tr>
  <td align = "center"> CNN as baseline </td>
  <td align = "center"> CNN + RNN (LRCN)</td>
  <td align = "center"> Temporal CNN </td>
</tr>
<tr>
<td> <img src="/Figures/cnn.png" alt="CNN as baseline" height="120"></td>
<td> <img src="/Figures/lrcn.png" alt="CNN + RNN (LRCN)" height="120"></td>
<td> <img src="/Figures/tnn.png" alt="Temporal CNN" height="120"> </td>
</tr>
</table>

<!-- <img src="/Figures/cnn.png" alt="CNN as baseline" height="200">
##### CNN + RNN [(LRCN)](http://jeffdonahue.com/lrcn/)
<img src="/Figures/lrcn.png" alt="CNN + RNN (LRCN)" height="200">
##### Temporal CNN
<img src="/Figures/tnn.png" alt="Temporal CNN)" height="200"> -->


### Demo 
Demo video coming out soon!

---
## Dataset 
We are currently using [UCF101](http://crcv.ucf.edu/data/UCF101.php) dataset for our project. This dataset has 13320 videos from 101 action categories. 
<p align="center">
<img src="http://crcv.ucf.edu/images/slideshow/UCF101.png" alt="UCF101 Dataset" height="200" align="middle">
</p>

We will move onto [SPORTS-1M](http://cs.stanford.edu/people/karpathy/deepvideo/) dataset to see how much our performance will be changed in the near future. 
<p align="center">
<img src="http://cs.stanford.edu/people/karpathy/deepvideo/sz70h.jpg" alt="SPORTS-1M Dataset" height="200">
</p>


---
## Installation 
Our work is currently implemented in Torch, and depends on the following packages: torch/torch7, torch/nn, torch/nngraph, torch/image, cudnn ...

If you are on Ubuntu, please follow the instruction here to install Torch. For a more comprehensive installation guilde, please check [Torch installation](http://torch.ch/docs/getting-started.html). 

```bash
$ git clone https://github.com/torch/distro.git ~/torch --recursive
$ cd ~/torch; bash install-deps;
$ ./install.sh
$ source ~/.bashrc

```
You will also need to install some of the packages we used from LuaRocks. LuaRocks should already be installed with your Torch. 
```bash
$ luarocks install torch 
$ luarocks install nn 
$ luarocks install dok 
$ luarocks install gnuplot 
$ luarocks install qtlua 
$ luarocks install sys 
$ luarocks install xlua 
$ luarocks install optim
```
If you would like to use CUDA on your NVIDIA graphic card, you will need to install [CUDA toolkit](https://developer.nvidia.com/cuda-toolkit) and some additional packages. 
```bash
$ luarocks install cutorch
$ luarocks install cunn
```
---
## Usage
We provide three different methods to train the models for activity recognition: CNN, CNN with RNN, and Temporal CNN. 

#### CNN with RNN
We use the [RNN library](https://github.com/Element-Research/rnn) provided by Element-Research. Simply install it by: 
```bash
$ luarocks install rnn
```
The RNN will take the **feature vectors** generated by the first CNN as input for training. For downloading the feature vectors generated by ourselves, please refer to the Dropbox link below. Theses are the exactly training and testing list from UCF101. If you would like to compare with our results, please use the same training and testing list, as it will affect your overall performance a lot. 

* [Features for training](https://www.dropbox.com/s/b0gbo7psouxeu2c/data_UCF101_train_1.t7?dl=0)
* [Features for testing](https://www.dropbox.com/s/98fr9df1r4nl18v/data_UCF101_test_1.t7?dl=0)

After you downloaded the feature vectors, please modify the code in *./RNN/data.lua* to the director where you put your feature vector files. 

To start the training process, simple execute: 
```bash
$ th RNN_LSTM.lua
```

The training and testing performance will be plotted, and the results will be saved into log files. The learning rate and best testing accuracy will be reported each epoch if there is any update. 

---
## Acknowledgment 
This work was initialized as a class project for deep learning class in Georgia Tech 2016 Spring. We were teamed up with Hao Yan and Casey Battaglino to work on this class project, who have been a great help and provide valuable discussions as we go long this class project. 

#### This is an ongoing project. Please contact us if you have any questions. 
[Chih-Yao Ma](http://shallowdown.wix.com/chih-yao-ma) at <cyma@gatech.edu>

Min-Hung Chen at <cmhungsteve@gatech.edu>


