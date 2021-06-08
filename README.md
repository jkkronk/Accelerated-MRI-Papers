# Awesome Accelerated-MRI-Reconstruction-Papers [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
A awesome list of a few papers on MRI reconstruction.

If your paper is not on the list, please feel free to [raise an issue](https://github.com/jkkronk/MRI-Reconstruction-Papers/issues) or drop me an [e-mail](mailto:jonatank@ee.ethz.ch?subject=[GitHub]%mri_recon%papers).

## What is Accelerated MRI-Reconstruction?
MRI is acquiring data in the Fourier domain, called kspace, and to fully sampling the data in kspace is needed to get an accurate image without artefacts. This is a time-consuming task that results in a brain scan taking up to 30 minutes. Accelerated MRI-Reconstruction seeks to reduce the acquisition time to improve efficiency, reduce motion artefacts and improve patient comfort. Accelerated MRI can be done by either introducing new hardware, such as extra receiver coils (called parallel imaging), or apply algorithms for better reconstruction. An excellent detailed introduction can found in [fastMRI dataset paper](https://arxiv.org/pdf/1811.08839.pdf). Below is an example of a fully sampled and undersampled counterpart. MRI-Reconstruction can be compared with super-resolution as the main goal is to estimate unsampled frequencies. 

<p align="center">
  <img width="600" src="/MRI_rec.png" "Example of undersampling artefacts.">
</p>

## Supervised Deep Learning Methods 
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| End-to-End Variational Networks for Accelerated MRI Reconstruction | E2E Varnet | 2020| [PDF](https://arxiv.org/pdf/2004.06688.pdf) | [CODE](https://github.com/facebookresearch/fastMRI/tree/master/fastmri_examples/varnet) |
| XPDNet for MRI Reconstruction: an Application to the fastMRI 2020 Brain Challenge | Supervised unrolled | 2020 | [PDF](https://arxiv.org/pdf/2010.07290.pdf) | |
| GrappaNet: Combining Parallel Imaging with Deep Learning for Multi-Coil MRI Reconstruction | Supervised kspace | 2020 | [PDF](https://arxiv.org/pdf/1910.12325v4.pdf) | [CODE](https://github.com/facebookresearch/fastMRI) |
| GrappaNet: Combining Parallel Imaging with Deep Learning for Multi-Coil MRI Reconstruction | Supervised kspace | 2020| [PDF](https://arxiv.org/pdf/1910.12325v4.pdf) | [CODE](https://github.com/facebookresearch/fastMRI) |
| Neumann Networks for Linear Inverse Problems in Imaging | Supervised end-to-end reconstruction | 2019 | [PDF](https://arxiv.org/pdf/1901.03707.pdf) | [CODE](https://dgilton.github.io/neumann_networks/) |
| LORAKI: Autocalibrated Recurrent Neural Networks for Autoregressive MRI Reconstruction in k-Space | Supervised CNN Kspace | 2019 | [PDF](https://arxiv.org/pdf/1904.09390.pdf) |  |
|  Image reconstruction by domain transform manifold learning | Supervised Manifold learning | 2019 | [PDF](https://arxiv.org/pdf/1704.08841.pdf) | [CODE](https://github.com/chongduan/MRI-AUTOMAP) |
| KIKI-net: cross-domain convolutional neural networ ks forreconstructing undersampled magnetic resonan ce images | Supervised CNN | 2019 |  [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.27201) | [CODE](https://github.com/zaccharieramzi/fastmri-reproducible-benchmark) |
| Learning a Variational Network for Reconstruction of Accelerated MRI Data | Supervised Variational Network | 2017 | [PDF](https://arxiv.org/pdf/1704.00447.pdf) | [CODE](https://github.com/VLOGroup/mri-variationalnetwork) |
| A Deep Cascade of Convolutional Neural Networks for MR Image Reconstruction | Supervised Cascade Network | 2017 | [PDF](https://arxiv.org/pdf/1703.00555.pdf) | [CODE](https://github.com/js3611/Deep-MRI-Reconstruction) |
| Deep ADMM-Net for Compressive Sensing MRI | Supervised and Compressed Sensing (CS) | 2016 | [PDF](https://papers.nips.cc/paper/2016/file/1679091c5a880faf6fb5e6087eb1b2dc-Paper.pdf) | [CODE](https://github.com/yangyan92/Deep-ADMM-Net) |

## Unsupervised Deep Learning Methods
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Unsupervised MRI Reconstruction with Generative Adversarial Networks | Unsupervised with GAN | 2020 | [PDF](https://arxiv.org/pdf/2008.13065.pdf) | [CODE](https://github.com/MRSRL/unsupGAN-release) |
| Unsupervised Deep Basis Pursuit: Learning inverse problems without ground-truth data | Supervised and Unsupervised end-to-end reconstruction | 2019 | [PDF](https://arxiv.org/pdf/1910.13110.pdf) | |

## Untrained Methods
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Unsupervised Deep Basis Pursuit: Learning inverse problems without ground-truth data | DIP | 2020 | [PDF](https://arxiv.org/pdf/1910.13110.pdf) | |
| Accelerated MRI with Un-trained Neural Networks | Untrained | 2020 | [PDF](https://arxiv.org/pdf/2007.02471.pdf) | |

## Low Rank Methods 
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| A General Framework for Compressed Sensing and Parallel MRI Using Annihilating Filter Based Low-Rank Hankel Matrix | Parallel imaging and Compressed Sensing (CS) | 2016 | [PDF](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7547372) | |

## Prior Based Methods
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Joint reconstruction and bias field correction for undersampled MR imaging | VAE reconstruction with Joint biasfield and reconstruction | 2020 | [PDF](https://arxiv.org/pdf/2007.13123v1.pdf) | |
| MR Image Reconstruction Using Deep Density Priors | VAE | 2019 | [PDF](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8579232) | [CODE](https://github.com/kctezcan/ddp_recon) |

## Classical Methods for Parallel Imaging and Compress Sensing 
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| ESPIRiT—an eigenvalue approach to autocalibrating parallel MRI: Where SENSE meets GRAPPA | Parallel imaging | 2014 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.24751) | [CODE](https://github.com/mikgroup/sigpy) |
| Joint image reconstruction and sensitivity estimation in SENSE (JSENSE) | Parallel imaging | 2007| [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.21245) | [CODE](https://github.com/jkkronk/jsense_mri_reconstruction) |
| Sparse MRI: The Application of Compressed Sensingfor Rapid MR Imaging | Compressed Sensing (CS) | 2007| [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.21391) | [CODE](https://github.com/peng-cao/mripy) |
| Undersampled Radial MRI with Multiple Coils. Iterative Image Reconstruction Using a Total Variation Constraint | Compressed Sensing (CS) | 2007| [PDF](https://pubmed.ncbi.nlm.nih.gov/17534903/) | |
| Robust Uncertainty Principles: Exact Signal Reconstruction from Highly Incomplete Frequency Information | Compressed Sensing (CS) | 2004| [PDF](https://arxiv.org/pdf/math/0409186.pdf) | [CODE](https://github.com/peng-cao/mripy) |
| POCSENSE: POCS-based reconstruction for sensitivity encoded magnetic resonance imaging | Parallel imaging | 2004 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.20285) | [CODE](https://mrirecon.github.io/bart/) |
| Generalized autocalibrating partially parallel acquisitions (GRAPPA) | Parallel imaging | 2002 | [PDF](https://onlinelibrary.wiley.com/doi/full/10.1002/mrm.10171?sid=nlm%3Apubmed) | [CODE](https://github.com/tetianadadakova/Tutorial-MRI-Reconstruction-Using-GRAPPA) |
| SENSE: sensitivity encoding for fast MRI | Parallel imaging | 1999 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/%28SICI%291522-2594%28199911%2942%3A5%3C952%3A%3AAID-MRM16%3E3.0.CO%3B2-S) | [CODE](https://github.com/mikgroup/sigpy) |
| Simultaneous Acquisition of Spatial Harmonics (SMASH): Fast Imaging with Radiofrequency Coil Arrays Encoded Magnetic Resonance Imaging | Parallel imaging | 1997 |  [PDF](https://pubmed.ncbi.nlm.nih.gov/9324327/) | |


## Uncertainty Estimation
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Bayesian Uncertainty Estimation of Learned Variational MRI Reconstruction | Epistemic Uncertainty Estimation | 2021 | [PDF](https://arxiv.org/pdf/2102.06665.pdf) | |
| Uncertainty Quantification in Deep MRI Reconstruction | Uncertainty | 2021 | [PDF](https://arxiv.org/pdf/1901.11228.pdf) | |
| Sampling possible reconstructions of undersampled acquisitions in MR imaging | Uncertainty Estimation | 2020 | [PDF](https://arxiv.org/pdf/2010.00042.pdf) | |

## Robustness 
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Measuring Robustness in Deep Learning Based Compressive Sensing | Robustness | 2021 | [PDF](https://arxiv.org/pdf/2102.06103.pdf) | |
| Improving Robustness of Deep-Learning-Based Image Reconstruction | Robustness | 2020 | [PDF](https://arxiv.org/pdf/2002.11821.pdf) | |
| On instabilities of deep learning in image reconstruction and the potential costs of AI | Robustness review | 2019 | [PDF](https://arxiv.org/pdf/1902.05300.pdf) | [CODE](https://github.com/vegarant/Invfool) |
| Scan-specific robust artificial-neural-networks for k-space interpolation (RAKI) reconstruction: Database-free deep learning for fast imaging | Supervised CNN Kspace | 2019 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.27420) |[CODE](https://github.com/zczam/RAKI) |

## Other
| Title | Short | Year| PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Results of the 2020 fastMRI Challenge for Machine Learning MR Image Reconstruction | Competition results | 2021 | [PDF](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9420272&tag=1) | |
| Deep Learning Methods for Parallel Magnetic Resonance Image Reconstruction | Survey | 2019 | [PDF](https://arxiv.org/pdf/1904.01112.pdf) | |
| fastMRI: An Open Dataset and Benchmarks for Accelerated MRI | Machine learning baselines and public dataset | 2019 | [PDF](https://arxiv.org/pdf/1811.08839.pdf) | [CODE](https://github.com/facebookresearch/fastMRI/) |


# Credits 
Template credits to [Few-Shot-Semantic-Segmentation-Papers](https://github.com/xiaomengyc/Few-Shot-Semantic-Segmentation-Papers) by [Xiaolin Zhang](https://github.com/xiaomengyc) and [awesome anomaly detection](https://github.com/hoya012/awesome-anomaly-detection) by [Hoseong, Lee @hoya012](https://github.com/hoya012)
