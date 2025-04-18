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
### The histogram distribution of the real and imaginary parts of various k-space data in Fig1
<div align="center"><img src="https://github.com/yqx7150/DMSE/blob/main/Fig1.png" >  </div>
Histogram distribution of the real and imaginary parts of various k-space data. Among them, first and middle rows display the distribution of target data and measurement, respectively, while the last row illustrates the distribution of the constructed subset-k-space. Note that the red circles serve to highlight areas of pronounced disparity.

### The schematic diagram of the construction of the novel distribution in Fig2.
<div align="center"><img src="https://github.com/yqx7150/DMSE/blob/main/Fig2.png" >  </div>
Schematic diagram of the construction of the novel distribution. Stage-1: Fusion of the subset-k-space of multi-contrast data to con-struct a new distribution. Stage-2: Embedding the under-sampled target itself as the global prior operator to form a high-dimensional tensor.

### The Overview of the DMSE procedure for MC-MRI reconstruction in Fig3.
<div align="center"><img src="https://github.com/yqx7150/DMSE/blob/main/Fig3.png" >  </div>
Overview of the DMSE procedure for MC-MRI reconstruction. Training phase intuitively visualizes the dynamic process of how the data dis-tribution gradually changes as the diffusion process continues. It is evident that the data distribution is complex while the noise follows a sim-ple Gaussian distribution. Reconstruction process is refined into three modules including predictor-corrector sampler, data consistency block and low-rank constraint unit, all of which occur in each iteration of the diffusion process.

###  Convergence curves of PSNR and MSE of GLDM and the number of iterations
<div align="center"><img src="https://github.com/yqx7150/DMSE/blob/main/Fig4.png" >  </div>
The trade-off between image quality vs. iteration steps for three manners for reconstruction T2WI. Sampling scheme used for this experiment is 2D Random sampling pattern with acceleration factor R=6.

## Other Related Projects    
  * Homotopic Gradients of Generative Density Priors for MR Image Reconstruction  
[<font size=5>**[Paper]**</font>](https://ieeexplore.ieee.org/abstract/document/9435335)   [<font size=5>**[Code]**</font>](https://github.com/yqx7150/HGGDP) [<font size=5>**[Slide]**</font>](https://github.com/yqx7150/HGGDP/tree/master/Slide)  

* One-shot Generative Prior in Hankel-k-space for Parallel Imaging Reconstruction  
[<font size=5>**[Paper]**</font>](https://arxiv.org/abs/2208.07181)   [<font size=5>**[Code]**</font>](https://github.com/yqx7150/HKGM)   [<font size=5>**[PPT]**</font>](https://github.com/yqx7150/HKGM/tree/main/PPT)
