# **IDEA-Net: Adaptive Dual Self-Attention Network for Single Image Denoising**
By [Zheming Zuo](https://scholar.google.co.uk/citations?user=jzpjf4UAAAAJ&hl=en)<sup>1</sup>, Xinyu Chen<sup>2</sup>, Han Xu<sup>3,4</sup>, [Jie Li](https://scholar.google.co.uk/citations?user=qiP4qZMAAAAJ&hl=en)<sup>5</sup>, Wenjuan Liao<sup>6</sup>, [Zhi-Xin Yang](https://scholar.google.com/citations?user=tlgIocMAAAAJ&hl=en)<sup>2</sup>, and [Shizheng Wang](https://scholar.google.com.sg/citations?user=Flpe3S4AAAAJ&hl=en)<sup>4</sup><br/>
<sup>1</sup> Department of Computer Science, Durham University, Durham DH1 3LE, UK<br/>
<sup>2</sup> Department of Electromechanical Engineering, University of Macau, Macau 999078, China<br/>
<sup>3</sup> University of Chinese Academy of Sciences, Beijing 100049, China<br/>
<sup>4</sup> Institute of Microelectronics, Chinese Academy of Sciences, Beijing 100029, China<br/>
<sup>5</sup> School of Computing, Engineering \& Digital Technologies, Teesside University, Middlesbrough TS3 6DR, UK<br/>
<sup>6</sup> College of Engineering and Computer Science, Australian National University, Canberra ACT2600, Australia<br/>

## _Introduction_
This is an official implementation of our adapt**I**ve **D**ual s**E**lf-**A**ttention **Net**work (**IDEA-Net**).

IDEA-Net is an unsupervised single image denoiser, which performs on superiorly on AWGN and real-world image noises with a single end-to-end deep neural network, and contributes to the downstream task of face detection in low-light conditions. Our work is inspired by _[Unsupervised Attention-guided Image-to-Image Translation](https://papers.nips.cc/paper/2018/file/4e87337f366f72daa424dae11df0538c-Paper.pdf)_ and _[Self2Self With Dropout: Learning Self-Supervised Denoising From Single Image](https://openaccess.thecvf.com/content_CVPR_2020/papers/Quan_Self2Self_With_Dropout_Learning_Self-Supervised_Denoising_From_Single_Image_CVPR_2020_paper.pdf)_.

<img src = "./fig/IDEA-Net.jpg" width = "100%" alt = "Architecture of our IDEA-Net">

For more details, please refer our 
- [[paper](https://in-press.pdf)]
- [[supp](https://in-press.pdf)]

## _Contents_
1. [Preparation](#preparation)
2. [Installation](#installation)
3. [Run](#run)
4. [Performance](#performance)

### _Preparation_
Clone the github repository.
```Shell
  git https://github.com/zhemingzuo/IDEA-Net --recursive
  cd IDEA-Net
```

### _Installation_
Set up a conda environmentwith all dependencies as follows:
```Shell
  conda env create -f environment.yml
  source activate ideanet_wacv_2022
```
Please note our implementation is only tested under Ubuntu environment with Nvidia GPUs and CUDA installed.


### _Run_
Run our IDEA-Net for image denosing via
```Shell
  python main.py  --to_train=1 --log_dir=./output/exp_01 --config_filename=./configs/exp_01.json
```

### _Performance_
1. Removing AWGN Image Noise

Comparisons of AWGN denoising results in terms of PSNR on the [(C)BSD68 dataset](https://github.com/clausmichele/CBSD68-dataset) with <img src="https://latex.codecogs.com/gif.latex?\sigma"/>  valued as 25 and 50. <img src = "./fig/green_box.png" width = "1.5%"> denotes the selected image region for comparison and <img src = "./fig/blue_box.png" width = "1.5%"> indicates the dual self-attention region drawn by IDEA-Net. Best viewed in zoomed mode.
<img src = "./fig/Example_AWGN.jpg" width = "100%" alt = "">

2. Removing Real-World Image Noise

Comparisons of real-world image noise removal results with respect to PSNR on the [PolyU dataset](https://github.com/csjunxu/PolyU-Real-World-Noisy-Images-Dataset). <img src = "./fig/green_box.png" width = "1.5%"> denotes the selected image region for comparison and <img src = "./fig/blue_box.png" width = "1.5%"> indicates the dual self-attention region drawn by the proposed IDEA-Net. Best viewed in zoomed mode..
<img src = "./fig/Example_real_noise.jpg" width = "100%" alt = "">

3. Downstream task on dark face detection

Performance comparisons of real-world dark/noisy face detection on the [DARK FACE dataset](https://flyywh.github.io/CVPRW2019LowLight/). Light-Enhanced Noisy Image (LENI) is yielded by [MSRCR](https://ieeexplore.ieee.org/document/597272). Detection results are generated by a [RetinaNet](https://openaccess.thecvf.com/content_ICCV_2017/papers/Lin_Focal_Loss_for_ICCV_2017_paper.pdf) that pre-trained on the [WIDER FACE dataset](http://shuoyang1213.me/WIDERFACE/). <img src = "./fig/green_box.png" width = "1.5%"> and <img src = "./fig/red_box.png" width = "1.5%"> respectively represents the correct and erroneous detections. <img src = "./fig/blue_box.png" width = "1.5%"> indicates the dual self-attention region drawn by IDEA-Net. Best viewed in zoomed mode.
<img src = "./fig/Example_dark_face.jpg" width = "100%" alt = "">

## _Citation_
If you find IDEA-Net useful in your research, please consider citing:
```
@InProceedings{Zuo_IdeaNet_2022_WACV_Workshops,
    author = {Z. Zuo and X. Chen and H. Xu and J. Li and W. Liao and Z.-X. Yang and S. Wang},
	title = {IDEA-Net: Adaptive Dual Self-Attention Network for Single Image Denoising},
	booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV) Workshops},
	year = {2022}
}
```