

# Bayesian Adaptive Superpixel Segmentation

This is the official code for our ICCV 2019 paper, ["Bayesian Adaptive Superpixel Segmentation"](https://www.cs.bgu.ac.il/~orenfr/BASS/Uziel_ICCV_2019.pdf) , co-authored by Roy Uziel, Meitar Ronen, and Oren Freifeld.

#### Important update (12/3/2022): The code is now much faster than it used to be. 
The original PyTorch-based GPU code (released in 2019) has been deprecated. The current CUDA-based GPU implementation (of the same algorithm from the paper) is much faster, translating usually to a x50 speedup. For example, using an NVIDIA GeForce GTX 1070 graphics card, a typical running time on a 512x512 image is 0.042 seconds.

# Prerequisites
GPU<br />
CUDA driver (Tested on 11.3+) <br />
OpenCV <br />

# Installation

### Cloning The GitHub Repository

```bash
$ git clone https://github.com/BGU-CS-VIL/BASS.git
``` 
```bash
$ cd BASS
$ mkdir build
$ cd build
$ cmake .. && make
``` 

# Usage
```bash
$./Sp_demo_for_direc -d ../images
``` 
Mean and contour images will be saved at ../result alongside the segmentation map (csv)

### Args and Kwargs:
-n the desired number of pixels on the side of a superpixel<br />
-i_std std dev for color Gaussians, should be 0.01<= value <=0.05. A smaller value leads to more irregular superpixels<br />
--im_size resizing input images (single number)<br />
--beta beta (Potts) 0 < value < 10<br />
--alpha alpha (Hasting ratio) 0.01< value <100<br />

### Usage Examples:

#### Changing the initial number of Superpixels:
```bash
./Sp_demo_for_direc -d ../images -n 25
```
![alt-text-1](./gif/border_25.png "-n 25") 


```bash
./Sp_demo_for_direc -d ../images -n 15
```

![alt-text-2](./gif/border_20.png "-n 15")

#### Larger Values of alpha will result in more superpixels due to splits:
```bash
./Sp_demo_for_direc -d ../images/ --im_size 512 -n 20 --alpha 0.1
```
![alt-text-2](./gif/border_2.png "--alpha 2")



```bash
./Sp_demo_for_direc -d ../images/ --im_size 512 -n 20 --alpha 20
```
![alt-text-2](./gif/border_alpha20.png "--alpha 20")


#### Increasing i_std will result in more compact Superpixels:

```bash
./Sp_demo_for_direc -d ../images/ --i_std 0.03
```
![alt-text-1](./gif/border_302003.png "-n 25")![alt-text-2](./gif/mean_302003.png "-n 25")  

```bash
./Sp_demo_for_direc -d ../images/ --i_std 0.018
```

![alt-text-1](./gif/border_18.png "-n 25")![alt-text-2](./gif/mean_18.png "-n 25")  




This software is released under the MIT License (included with the software). Note, however, that if you are using this code (and/or the results of running it) to support any form of publication (e.g., a book, a journal paper, a conference paper, a patent application, etc.) then we request you will cite our paper:

```
@inproceedings{Uziel:ICCV:2019:BASS,
  title = {Bayesian Adaptive Superpixel Segmentation},
  author = {Roy Uziel and Meitar Ronen and Oren Freifeld},
  booktitle = {ICCV},
  year={2019}
 } 
