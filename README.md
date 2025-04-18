# DMSE
**Paper**: Distribution Matching with Subset-k-space Embedding for Multi-contrast MRI Reconstruction 

**Authors**: Yu Guan, Yujuan Lu, Zhuoxu Cui, Shanshan Wang, Qiegen Liu* 

http://dx.doi.org/10.2139/ssrn.5144531

Date : February-25-2025  
The code and the algorithm are for non-comercial use only.  
Copyright 2022, Department of Mathematics and Computer Sciences, Nanchang University. 

To reduce the time required for multiple acquisitions in multi-contrast magnetic resonance imaging (MC-MRI), recent research has focused on collecting partial k-space data from a single contrast to reconstruct high-quality images by leveraging the redundancy among different contrasts. Further exploiting relevant information across diverse contrasts presents a more effective solution for accurate reconstruction. This work proposes a novel reconstruction method that integrates the advantages of subset-k-space distribution prior and high-dimensional global prior for MC-MRI reconstruction. Specifically, the first stage involves the individual decomposition of k-space data from different guided contrasts, which are then combined with the measurements to construct a new subset-k-space. Notably, establishing this subset-k-space minimizes the distance between the distribution of the measurements and the target examples. In addition to capitalizing on the novel distribution matching strategy for improved sampling, the second stage incorporates global prior embedding to constrain the diffusion model within the high-dimensional space, using the reconstructed contrast itself as a reference. This global prior further refines the initial reconstruction obtained in the first stage. Empirical evaluations across various datasets compellingly demonstrate the proposed method's excellent capability to preserve details and achieve accurate reconstruction.

## Requirements and Dependencies
    python==3.7.11
    Pytorch==1.7.0
    tensorflow==2.4.0
    torchvision==0.8.0
    tensorboard==2.7.0
    scipy==1.7.3
    numpy==1.19.5
    ninja==1.10.2
    matplotlib==3.5.1
    jax==0.2.26

## Training Demo
``` bash
python main.py --config=configs/ve/SIAT_kdata_ncsnpp.py --workdir=exp --mode=train --eval_folder=result
```
## Test Demo
``` bash
python PCsampling.py
```

## Graphical representation
### The whole pipeline of GLDM is illustrated in Fig1
<div align="center"><img src="https://github.com/yqx7150/GLDM/blob/main/Fig1.png" >  </div>
The schematic of the proposed GLDM algorithm. Red and blue parts represent the training stage that fully encoded full-resolution reference data is constructed through a time-interleaved acquisition scheme. Red part merges all time frames to train the global model (GM) while the blue part merges local time frames to train the local model (LM). Green part represents the reconstruction stage which the structure of the reconstruction model exists in a cascade form and the under-sampled k-space data (16 frames) are sequentially input into the network. At the same time, optimization unit (OU) containing a LR operator and a DC term is introduced to better remove aliasing and restore details

### Time-interleaved acquisition scheme is visualized in Fig2.
<div align="center"><img src="https://github.com/yqx7150/GLDM/blob/main/Fig2.png" >  </div>
The core of the approach is to construct a complete k-space dataset by merging any number of adjacent time frames. In the above example, two different under-sampled patterns (uniform and random) at 5-fold acceleration are acquired via a time-interleaved acquisition scheme.

### The time-interleaved acquisition scheme of 4 frames of dynamic MRI is visualized in Fig3.
<div align="center"><img src="https://github.com/yqx7150/GLDM/blob/main/Fig3.png" >  </div>
The ACS of each frame remains unaltered, while the remainder of the area is filled with data from adjacent frames. The distinct colors rep-resent data contributions from different frames

###  Convergence curves of PSNR and MSE of GLDM and the number of iterations
<div align="center"><img src="https://github.com/yqx7150/GLDM/blob/main/Fig4.png" >  </div>
Convergence curves of PSNR and MSE of GLDM and the number of iterations

## Other Related Projects    
  * Homotopic Gradients of Generative Density Priors for MR Image Reconstruction  
[<font size=5>**[Paper]**</font>](https://ieeexplore.ieee.org/abstract/document/9435335)   [<font size=5>**[Code]**</font>](https://github.com/yqx7150/HGGDP) [<font size=5>**[Slide]**</font>](https://github.com/yqx7150/HGGDP/tree/master/Slide)  

* One-shot Generative Prior in Hankel-k-space for Parallel Imaging Reconstruction  
[<font size=5>**[Paper]**</font>](https://arxiv.org/abs/2208.07181)   [<font size=5>**[Code]**</font>](https://github.com/yqx7150/HKGM)   [<font size=5>**[PPT]**</font>](https://github.com/yqx7150/HKGM/tree/main/PPT)
