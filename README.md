# Awesome Accelerated-MRI-Reconstruction-Papers [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> **Last updated: September 2026.** The list now covers work through mid-2026 (diffusion/score-based priors, self-supervised training, transformers and state-space models, foundation models, learned sampling, new k-space datasets and challenges). Contributions are welcome via issues or pull requests.

An awesome list of papers on MRI reconstruction.

If your paper is not on the list, please feel free to [raise an issue](https://github.com/jkkronk/Accelerated-MRI-Papers/issues) or open a pull request.

## What is Accelerated MRI-Reconstruction?
MRI is acquiring data in the Fourier domain, called kspace, and fully sampling the data in kspace is needed to get an accurate image without artefacts. This is a time-consuming task that results in a brain scan taking up to 30 minutes. Accelerated MRI-Reconstruction seeks to reduce the acquisition time to improve efficiency, reduce motion artefacts and improve patient comfort. Accelerated MRI can be done by either introducing new hardware, such as extra receiver coils (called parallel imaging), or apply algorithms for better reconstruction. An excellent detailed introduction can be found in [fastMRI dataset paper](https://arxiv.org/pdf/1811.08839.pdf). Below is an example of a fully sampled and undersampled counterpart. MRI-Reconstruction can be compared with super-resolution as the main goal is to estimate unsampled frequencies. 

<p align="center">
  <img width="600" src="/MRI_rec.png" alt="Example of undersampling artefacts.">
</p>

Yutong Chen has written a great meta review paper on accelerated MRI that can be found here: [https://arxiv.org/abs/2112.12744](https://arxiv.org/abs/2112.12744)

## Contents
- [Surveys, Reviews and Tutorials](#surveys-reviews-and-tutorials)
- [Supervised Deep Learning Methods](#supervised-deep-learning-methods)
- [Foundation Models and Universal Reconstruction](#foundation-models-and-universal-reconstruction)
- [Diffusion and Score-Based Generative Priors](#diffusion-and-score-based-generative-priors)
- [Other Learned Priors (VAE, GAN, Flows)](#other-learned-priors-vae-gan-flows)
- [Self-Supervised and Unsupervised Deep Learning Methods](#self-supervised-and-unsupervised-deep-learning-methods)
- [Untrained, Scan-Specific and Implicit Neural Representation Methods](#untrained-scan-specific-and-implicit-neural-representation-methods)
- [Dynamic and Cardiac MRI Reconstruction](#dynamic-and-cardiac-mri-reconstruction)
- [Quantitative, Multi-Contrast and Diffusion-Weighted MRI Reconstruction](#quantitative-multi-contrast-and-diffusion-weighted-mri-reconstruction)
- [Motion-Robust Reconstruction](#motion-robust-reconstruction)
- [Non-Cartesian, 3D and Low-Field Reconstruction](#non-cartesian-3d-and-low-field-reconstruction)
- [Learned Sampling and Joint Acquisition-Reconstruction Optimization](#learned-sampling-and-joint-acquisition-reconstruction-optimization)
- [Low Rank Methods](#low-rank-methods)
- [Classical Methods for Parallel Imaging and Compressed Sensing](#classical-methods-for-parallel-imaging-and-compressed-sensing)
- [Uncertainty Estimation](#uncertainty-estimation)
- [Robustness, Distribution Shift and Adversarial Attacks](#robustness-distribution-shift-and-adversarial-attacks)
- [Evaluation, Metrics and Clinical Validation](#evaluation-metrics-and-clinical-validation)
- [Datasets](#datasets)
- [Challenges and Benchmarks](#challenges-and-benchmarks)
- [Software and Toolboxes](#software-and-toolboxes)


## Surveys, Reviews and Tutorials
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Deep Learning-Based Acceleration in MRI: Current Landscape and Clinical Applications in Neuroradiology | Clinical review, neuroradiology | 2026 | [PDF](https://doi.org/10.3174/ajnr.A8943) |  |
| A Comprehensive Survey on Magnetic Resonance Image Reconstruction | Broad MRI reconstruction survey | 2025 | [PDF](https://arxiv.org/abs/2503.07097) |  |
| Advancing MRI Reconstruction: A Systematic Review of Deep Learning and Compressed Sensing Integration | Systematic review DL + CS | 2025 | [PDF](https://arxiv.org/abs/2501.14158) |  |
| Deep Learning for Accelerated and Robust MRI Reconstruction: a Review | DL MRI recon review (MAGMA) | 2024 | [PDF](https://arxiv.org/abs/2404.15692) |  |
| Diffusion models for medical image reconstruction | Diffusion recon tutorial review | 2024 | [PDF](https://doi.org/10.1093/bjrai/ubae013) |  |
| Data and Physics driven Deep Learning Models for Fast MRI Reconstruction: Fundamentals and Methodologies | Data/physics-driven DL fundamentals | 2024 | [PDF](https://arxiv.org/abs/2401.16564) |  |
| A Survey of Emerging Applications of Diffusion Probabilistic Models in MRI | Diffusion models in MRI survey | 2023 | [PDF](https://arxiv.org/abs/2311.11383) |  |
| Physics-Driven Deep Learning for Computational Magnetic Resonance Imaging | Physics-driven DL overview (SPM) | 2023 | [PDF](https://arxiv.org/abs/2203.12215) |  |
| A review and experimental evaluation of deep learning methods for MRI reconstruction | Review paper | 2021 | [PDF](https://arxiv.org/abs/2109.08618) |  |
| Plug-and-Play Methods for Magnetic Resonance Imaging | PnP denoiser-based recon (SPM) | 2020 | [PDF](https://arxiv.org/abs/1903.08616) |  |
| Deep Learning Methods for Parallel Magnetic Resonance Image Reconstruction | Survey | 2019 | [PDF](https://arxiv.org/pdf/1904.01112.pdf) |  |


## Supervised Deep Learning Methods
Unrolled / physics-driven networks, transformers, state-space models and other end-to-end supervised reconstruction.

| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| UMPIRE-Net: Unrolled Magnitude-Phase Regularization Network for Accelerated MRI | Separate magnitude/phase unrolled regularizers | 2026 | [PDF](https://arxiv.org/abs/2608.14422) | [CODE](https://github.com/MahdiSaberii/UMPIRE-Net) |
| Deep Unrolled Networks in Representation Space Applied to MRI Reconstruction | DUNE: unrolling in learned latent space | 2026 | [PDF](https://arxiv.org/abs/2606.21602) |  |
| SO-Mamba: State-Ownership Mamba for Unrolled MRI Reconstruction | Mamba regularizer inside unrolled net | 2026 | [PDF](https://arxiv.org/abs/2605.22031) |  |
| PAS-Mamba: Phase-Amplitude-Spatial State Space Model for MRI Reconstruction | Phase/amplitude dual-branch Mamba | 2026 | [PDF](https://arxiv.org/abs/2601.14530) |  |
| DH-Mamba: Exploring Dual-domain Hierarchical State Space Models for MRI Reconstruction | Dual-domain hierarchical Mamba | 2025 | [PDF](https://arxiv.org/abs/2501.08163) | [CODE](https://github.com/XiaoMengLiLiLi/DH-Mamba) |
| Rethinking Deep Unrolled Model for Accelerated MRI Reconstruction | PromptMR+; CMRxRecon 2024 winner | 2024 | [PDF](https://doi.org/10.1007/978-3-031-73226-3_10) | [CODE](https://github.com/hellopipu/PromptMR-plus) |
| Physics-Driven Autoregressive State Space Models for Medical Image Reconstruction | MambaRoll: autoregressive multi-scale SSM unrolled | 2024 | [PDF](https://arxiv.org/abs/2412.09331) | [CODE](https://github.com/icon-lab/MambaRoll) |
| MambaRecon: MRI Reconstruction with Structured State Space Models | Structured SSM reconstruction network | 2024 | [PDF](https://arxiv.org/abs/2409.12401) | [CODE](https://github.com/yilmazkorkmaz1/MambaRecon) |
| Deep Cardiac MRI Reconstruction with ADMM | vSHARP entry, CMRxRecon 2023 | 2023 | [PDF](https://arxiv.org/abs/2310.06628) | [CODE](https://github.com/NKI-AI/direct) |
| vSHARP: variable Splitting Half-quadratic Admm algorithm for Reconstruction of inverse-Problems | ADMM-unrolled network with U-Net denoiser | 2023 | [PDF](https://arxiv.org/abs/2309.09954) | [CODE](https://github.com/NKI-AI/direct) |
| CAMP-Net: Consistency-Aware Multi-Prior Network for Accelerated MRI Reconstruction | Multi-prior, multi-domain unrolled net | 2023 | [PDF](https://arxiv.org/abs/2306.11238) | [CODE](https://github.com/lpzhang/CAMP-Net) |
| Memory-efficient model-based deep learning with convergence and robustness guarantees | Deep-equilibrium MoDL (monotone operator) | 2022 | [PDF](https://arxiv.org/abs/2206.04797) |  |
| HUMUS-Net: Hybrid unrolled multi-scale network architecture for accelerated MRI reconstruction | Conv-Transformer hybrid unrolled net | 2022 | [PDF](https://arxiv.org/abs/2203.08213) | [CODE](https://github.com/z-fabian/HUMUS-Net) |
| Vision Transformers Enable Fast and Robust Accelerated MRI | Pretrained ViT for reconstruction | 2022 | [PDF](https://proceedings.mlr.press/v172/lin22a.html) | [CODE](https://github.com/MLI-lab/transformers_for_imaging) |
| ReconFormer: Accelerated MRI Reconstruction Using Recurrent Transformer | Recurrent pyramid transformer | 2022 | [PDF](https://arxiv.org/abs/2201.09376) | [CODE](https://github.com/guopengf/ReconFormer) |
| Swin Transformer for Fast MRI | SwinMR: Swin transformer reconstruction | 2022 | [PDF](https://arxiv.org/abs/2201.03230) | [CODE](https://github.com/ayanglab/SwinMR) |
| Recurrent Variational Network: A Deep Learning Inverse Problem Solver applied to the task of Accelerated MRI Reconstruction | RecurrentVarNet: k-space recurrent unrolled net | 2021 | [PDF](https://arxiv.org/abs/2111.09639) | [CODE](https://github.com/NKI-AI/direct) |
| Joint Deep Model-Based MR Image and Coil Sensitivity Reconstruction Network (Joint-ICNet) for Fast MRI | Joint image and sensitivity-map unrolled net | 2021 | [PDF](https://openaccess.thecvf.com/content/CVPR2021/html/Jun_Joint_Deep_Model-Based_MR_Image_and_Coil_Sensitivity_Reconstruction_Network_CVPR_2021_paper.html) |  |
| Deep Equilibrium Architectures for Inverse Problems in Imaging | Deep-equilibrium (infinite-depth) unrolling | 2021 | [PDF](https://arxiv.org/abs/2102.07944) | [CODE](https://github.com/dgilton/deep_equilibrium_inverse) |
| Density Compensated Unrolled Networks for Non-Cartesian MRI Reconstruction | PDNet | 2021 | [PDF](https://arxiv.org/abs/2101.01570) | [CODE](https://github.com/zaccharieramzi/fastmri-reproducible-benchmark) |
| Deep J-Sense: Accelerated MRI Reconstruction via Unrolled Alternating Optimization | pMRI reconstruction | 2021 | [PDF](https://arxiv.org/pdf/2103.02087.pdf) | [CODE](https://github.com/utcsilab/deep-jsense) |
| Multi-Modal MRI Reconstruction Assisted with Spatial Alignment Network | Combined sequences/modalities | 2021 | [PDF](https://arxiv.org/pdf/2108.05603.pdf) | [CODE](https://github.com/woxuankai/SpatialAlignmentNetwork) |
| Data augmentation for deep learning based accelerated MRI reconstruction with limited data | Data Augmentation for reconstruction | 2021 | [PDF](https://arxiv.org/abs/2106.14947) | [CODE](https://github.com/z-fabian/MRAugment) |
| Joint Frequency and Image Space Learning for MRI Reconstruction and Analysis | Do reconstruction in kspace and image space | 2020 | [PDF](https://arxiv.org/abs/2007.01441) |  |
| End-to-End Variational Networks for Accelerated MRI Reconstruction | E2E Varnet | 2020 | [PDF](https://arxiv.org/pdf/2004.06688.pdf) | [CODE](https://github.com/facebookresearch/fastMRI/tree/master/fastmri_examples/varnet) |
| XPDNet for MRI Reconstruction: an Application to the fastMRI 2020 Brain Challenge | Supervised unrolled | 2020 | [PDF](https://arxiv.org/pdf/2010.07290.pdf) |  |
| GrappaNet: Combining Parallel Imaging with Deep Learning for Multi-Coil MRI Reconstruction | Supervised kspace | 2020 | [PDF](https://arxiv.org/pdf/1910.12325v4.pdf) | [CODE](https://github.com/facebookresearch/fastMRI) |
| Ultra-Fast T2-Weighted MR Reconstruction Using Complementary T1-Weighted Information | Combined sequences | 2019 | [PDF](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6430217/) |  |
| Neumann Networks for Inverse Problems in Imaging | Supervised end-to-end reconstruction | 2019 | [PDF](https://arxiv.org/pdf/1901.03707.pdf) | [CODE](https://dgilton.github.io/neumann_networks/) |
| LORAKI: Autocalibrated Recurrent Neural Networks for Autoregressive MRI Reconstruction in k-Space | Supervised CNN Kspace | 2019 | [PDF](https://arxiv.org/pdf/1904.09390.pdf) |  |
| Image reconstruction by domain transform manifold learning | Supervised Manifold learning | 2019 | [PDF](https://arxiv.org/pdf/1704.08841.pdf) | [CODE](https://github.com/chongduan/MRI-AUTOMAP) |
| KIKI-net: Cross-domain Convolutional Neural Networks for Reconstructing Undersampled Magnetic Resonance Images | Supervised cross-domain CNN | 2018 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.27201) | [CODE](https://github.com/zaccharieramzi/fastmri-reproducible-benchmark) |
| Learning a Variational Network for Reconstruction of Accelerated MRI Data | Supervised Variational Network | 2017 | [PDF](https://arxiv.org/pdf/1704.00447.pdf) | [CODE](https://github.com/VLOGroup/mri-variationalnetwork) |
| A Deep Cascade of Convolutional Neural Networks for MR Image Reconstruction | Supervised Cascade Network | 2017 | [PDF](https://arxiv.org/pdf/1703.00555.pdf) | [CODE](https://github.com/js3611/Deep-MRI-Reconstruction) |
| Deep ADMM-Net for Compressive Sensing MRI | Supervised and Compressed Sensing (CS) | 2016 | [PDF](https://papers.nips.cc/paper/2016/file/1679091c5a880faf6fb5e6087eb1b2dc-Paper.pdf) | [CODE](https://github.com/yangyan92/Deep-ADMM-Net) |


## Foundation Models and Universal Reconstruction
Single models trained across anatomies, contrasts, sampling patterns and sites; prompt-/protocol-conditioned reconstruction.

| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Are Natural-Domain Foundation Models Effective for Accelerated Cardiac MRI Reconstruction? | Frozen CLIP/DINOv2 priors in unrolled net | 2026 | [PDF](https://arxiv.org/abs/2604.22557) |  |
| CRUNet-MR-Univ: A Foundation Model for Diverse Cardiac MRI Reconstruction | Prompt-based universal cardiac reconstruction | 2026 | [PDF](https://arxiv.org/abs/2601.04428) |  |
| UPCMR: A Universal Prompt-guided Model for Random Sampling Cardiac MRI Reconstruction | Prompt-guided universal unrolled model | 2025 | [PDF](https://arxiv.org/abs/2502.14899) | [CODE](https://github.com/dong845/UPCMR) |
| Enabling Ultra-Fast Cardiovascular Imaging Across Heterogeneous Clinical Environments with A Generalist Foundation Model and Multimodal Database | CardioMM generalist reconstruction foundation model | 2025 | [PDF](https://arxiv.org/abs/2512.21652) | [CODE](https://github.com/wangziblake/CardioMM_MMCMR-427K) |
| SDUM: A Scalable Deep Unrolled Model for Universal MRI Reconstruction | Protocol-conditioned scalable unrolled model | 2025 | [PDF](https://arxiv.org/abs/2512.17137) | [CODE](https://github.com/NVIDIA-Medtech/NV-Raw2insights-MRI) |
| On the Utility of Foundation Models for Fast MRI: Vision-Language-Guided Image Reconstruction | Vision-language semantic prior objective | 2025 | [PDF](https://arxiv.org/abs/2511.19641) |  |
| OmniMRI: A Unified Vision--Language Foundation Model for Generalist MRI Interpretation | VL foundation model incl. reconstruction task | 2025 | [PDF](https://arxiv.org/abs/2508.17524) |  |
| HierAdaptMR: Cross-Center Cardiac MRI Reconstruction with Hierarchical Feature Adapters | Adapter-based cross-center generalization | 2025 | [PDF](https://arxiv.org/abs/2508.13026) | [CODE](https://github.com/Ruru-Xu/HierAdaptMR) |
| A Unified Model for Compressed Sensing MRI Across Undersampling Patterns | Neural-operator, pattern-agnostic reconstruction | 2024 | [PDF](https://arxiv.org/abs/2410.16290) |  |
| Fill the K-Space and Refine the Image: Prompting for Dynamic and Multi-Contrast MRI Reconstruction | PromptMR all-in-one; CMRxRecon 2023 winner | 2023 | [PDF](https://arxiv.org/abs/2309.13839) | [CODE](https://github.com/hellopipu/PromptMR) |
| Universal Undersampled MRI Reconstruction | Single model across anatomies | 2021 | [PDF](https://arxiv.org/abs/2103.05214) |  |


## Diffusion and Score-Based Generative Priors
Diffusion / score-based / flow-matching models used as priors for posterior sampling or regularization.

| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Consistency Models for Fast MRI Reconstruction Using Regularization by Denoising | Consistency model prior, 4-step RED | 2026 | [PDF](https://arxiv.org/abs/2608.20561) | [CODE](https://github.com/MerveGulle/CM-RED) |
| MPFlow: Multi-modal Posterior-Guided Flow Matching for Zero-Shot MRI Reconstruction | Zero-shot multi-modal flow matching | 2026 | [PDF](https://arxiv.org/abs/2603.03710) |  |
| Fast and Robust Diffusion Posterior Sampling for MR Image Reconstruction Using the Preconditioned Unadjusted Langevin Algorithm | Preconditioned Langevin posterior sampling | 2025 | [PDF](https://arxiv.org/abs/2512.05791) | [CODE](https://gitlab.tugraz.at/ibi/mrirecon/papers/dps-pula) |
| Patch-Based Diffusion for Data-Efficient, Radiologist-Preferred MRI Reconstruction | Patch-based diffusion prior, data-efficient | 2025 | [PDF](https://arxiv.org/abs/2509.21531) | [CODE](https://github.com/voilalab/PaDIS-MRI) |
| Highly Undersampled MRI Reconstruction via a Single Posterior Sampling of Diffusion Models | One-step distilled posterior sampling | 2025 | [PDF](https://arxiv.org/abs/2505.08142) | [CODE](https://github.com/YangGaoUQ/SSDM-MRI) |
| Unsupervised Accelerated MRI Reconstruction via Ground-Truth-Free Flow Matching | Ground-truth-free flow matching | 2025 | [PDF](https://arxiv.org/abs/2502.17174) |  |
| Bigger Isn't Always Better: Towards a General Prior for Medical Image Reconstruction | Small/natural-image diffusion priors generalize | 2025 | [PDF](https://arxiv.org/abs/2501.07376) | [CODE](https://github.com/VLOGroup/bigger-isnt-always-better) |
| Ambient Diffusion Posterior Sampling: Solving Inverse Problems with Diffusion Models Trained on Corrupted Data | Diffusion prior from undersampled data only | 2024 | [PDF](https://arxiv.org/abs/2403.08728) | [CODE](https://github.com/utcsilab/ambient-diffusion-mri) |
| MRI Reconstruction with Regularized 3D Diffusion Model (R3DM) | Regularized 3D diffusion prior | 2024 | [PDF](https://arxiv.org/abs/2412.18723) | [CODE](https://jugit.fz-juelich.de/ias-8/r3dm/) |
| MRPD: Undersampled MRI reconstruction by prompting a large latent diffusion model | Prompting latent diffusion (SD) prior | 2024 | [PDF](https://arxiv.org/abs/2402.10609) | [CODE](https://github.com/Z7Gao/MRPD) |
| SMRD: SURE-based Robust MRI Reconstruction with Diffusion Models | SURE-based test-time tuning | 2023 | [PDF](https://arxiv.org/abs/2310.01799) | [CODE](https://github.com/NVlabs/SMRD) |
| Decomposed Diffusion Sampler for Accelerating Large-Scale Inverse Problems | Krylov-accelerated sampler, 3D multi-coil | 2023 | [PDF](https://arxiv.org/abs/2303.05754) | [CODE](https://github.com/HJ-harry/DDS) |
| Self-Supervised MRI Reconstruction with Unrolled Diffusion Models | Self-supervised unrolled diffusion | 2023 | [PDF](https://arxiv.org/abs/2306.16654) | [CODE](https://github.com/yilmazkorkmaz1/SSDiffRecon) |
| Learning Fourier-Constrained Diffusion Bridges for MRI Reconstruction | Fourier-constrained diffusion bridge | 2023 | [PDF](https://arxiv.org/abs/2308.01096) | [CODE](https://github.com/icon-lab/FDB) |
| Solving 3D Inverse Problems using Pre-trained 2D Diffusion Models | 2D diffusion prior for 3D volumes | 2022 | [PDF](https://arxiv.org/abs/2211.10655) | [CODE](https://github.com/HJ-harry/DiffusionMBIR) |
| Adaptive Diffusion Priors for Accelerated MRI Reconstruction | Adaptive adversarial diffusion prior | 2022 | [PDF](https://arxiv.org/abs/2207.05876) | [CODE](https://github.com/icon-lab/AdaDiff) |
| High-Frequency Space Diffusion Models for Accelerated MRI | Diffusion in high-frequency k-space | 2022 | [PDF](https://arxiv.org/abs/2208.05481) | [CODE](https://github.com/Aboriginer/HFS-SDE) |
| Towards performant and reliable undersampled MR reconstruction via diffusion model sampling | Pretrained DDPM, coarse-to-fine sampling | 2022 | [PDF](https://arxiv.org/abs/2203.04292) | [CODE](https://github.com/cpeng93/DiffuseRecon) |
| Robust Compressed Sensing MRI with Deep Generative Priors | Score-based prior, Langevin posterior sampling | 2021 | [PDF](https://arxiv.org/abs/2108.01368) | [CODE](https://github.com/utcsilab/csgm-mri-langevin) |
| Solving Inverse Problems in Medical Imaging with Score-Based Generative Models | Unconditional score prior, measurement-agnostic | 2021 | [PDF](https://arxiv.org/abs/2111.08005) | [CODE](https://github.com/yang-song/score_inverse_problems) |
| Score-based diffusion models for accelerated MRI | Score-SDE prior, predictor-corrector DC | 2021 | [PDF](https://arxiv.org/abs/2110.05243) | [CODE](https://github.com/HJ-harry/score-MRI) |
| Come-Closer-Diffuse-Faster: Accelerating Conditional Diffusion Models for Inverse Problems through Stochastic Contraction | Fast conditional diffusion, stochastic contraction | 2021 | [PDF](https://arxiv.org/abs/2112.05146) |  |


## Other Learned Priors (VAE, GAN, Flows)
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Stable Deep MRI Reconstruction using Generative Priors | Generative regularizer, variational recon | 2022 | [PDF](https://arxiv.org/abs/2210.13834) |  |
| Unsupervised MRI Reconstruction via Zero-Shot Learned Adversarial Transformers | Zero-shot adversarial transformer prior | 2021 | [PDF](https://arxiv.org/abs/2105.08059) | [CODE](https://github.com/icon-lab/SLATER) |
| Bayesian Image Reconstruction using Deep Generative Models | Unsupervised in the sense not trained end-to-end reconstruction | 2021 | [PDF](https://arxiv.org/pdf/2012.04567.pdf) |  |
| Joint reconstruction and bias field correction for undersampled MR imaging | VAE reconstruction with Joint biasfield and reconstruction | 2020 | [PDF](https://arxiv.org/pdf/2007.13123v1.pdf) |  |
| MR Image Reconstruction Using Deep Density Priors | VAE | 2019 | [PDF](https://ieeexplore.ieee.org/document/8579232) | [CODE](https://github.com/kctezcan/ddp_recon) |


## Self-Supervised and Unsupervised Deep Learning Methods
Training without fully-sampled reference data.

| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Optimized Multi-Contrast Self-Supervised MRI Reconstruction using Learned k-space Partitioning | Learned k-space split, multi-contrast | 2026 | [PDF](https://arxiv.org/abs/2606.19182) |  |
| CoilDrop-MRI: Self-supervised physics-guided MRI reconstruction with coil dropout | Self-supervision via coil dropout | 2026 | [PDF](https://arxiv.org/abs/2606.00100) |  |
| Towards a Unified Theoretical Framework for Splitting-based Self-Supervised MRI Reconstruction | Unified theory of k-space splitting SSL | 2026 | [PDF](https://arxiv.org/abs/2601.04775) |  |
| Benchmarking Self-Supervised Learning Methods for Accelerated MRI Reconstruction | Open benchmark of SSL methods | 2025 | [PDF](https://arxiv.org/abs/2502.14009) | [CODE](https://github.com/Andrewwango/ssibench) |
| Re-Visible Dual-Domain Self-Supervised Deep Unfolding Network for MRI Reconstruction | Dual-domain self-supervised unfolding | 2025 | [PDF](https://arxiv.org/abs/2501.03737) |  |
| Self-Supervised Learning for Improved Calibrationless Radial MRI with NLINV-Net | Self-supervised calibrationless radial | 2024 | [PDF](https://arxiv.org/abs/2402.06550) |  |
| Joint Supervised and Self-supervised Learning for MRI Reconstruction | Joint supervised + SSDU training | 2023 | [PDF](https://arxiv.org/abs/2311.15856) | [CODE](https://github.com/NKI-AI/direct) |
| K-band: Self-supervised MRI Reconstruction via Stochastic Gradient Descent over K-space Subsets | Train on limited-resolution k-space bands | 2023 | [PDF](https://arxiv.org/abs/2308.02958) | [CODE](https://github.com/mikgroup/K-band) |
| Clean self-supervised MRI reconstruction from noisy, sub-sampled training data with Robust SSDU | Noise-robust, weighted SSDU | 2022 | [PDF](https://arxiv.org/abs/2210.01696) | [CODE](https://github.com/charlesmillard/robust_ssdu) |
| A theoretical framework for self-supervised MR image reconstruction using sub-sampling via variable density Noisier2Noise | Noisier2Noise theory of SSDU | 2022 | [PDF](https://arxiv.org/abs/2205.10278) | [CODE](https://github.com/charlesmillard/Noisier2Noise_for_recon) |
| Dual-Domain Self-Supervised Learning for Accelerated Non-Cartesian MRI Reconstruction | Dual-domain SSL, non-Cartesian | 2022 | [PDF](https://arxiv.org/abs/2302.09244) |  |
| Robust Equivariant Imaging: a fully unsupervised framework for learning to image from noisy and partial measurements | Unsupervised via equivariance + SURE | 2021 | [PDF](https://arxiv.org/abs/2111.12855) | [CODE](https://github.com/edongdongchen/REI) |
| Noise2Recon: Enabling Joint MRI Reconstruction and Denoising with Semi-Supervised and Self-Supervised Learning | Consistency training with noise augmentation | 2021 | [PDF](https://arxiv.org/abs/2110.00075) | [CODE](https://github.com/ad12/meddlr) |
| Self-Supervised Learning for MRI Reconstruction with a Parallel Network Training Framework | Parallel-network SSL, no ground truth | 2021 | [PDF](https://arxiv.org/abs/2109.12502) | [CODE](https://github.com/chenhu96/Self-Supervised-MRI-Reconstruction) |
| Zero-Shot Self-Supervised Learning for MRI Reconstruction | Zero-shot SSDU on single scan | 2021 | [PDF](https://arxiv.org/abs/2102.07737) | [CODE](https://github.com/byaman14/ZS-SSL) |
| ENSURE: A general approach for unsupervised training of deep image reconstruction algorithms | SURE/GSURE | 2021 | [PDF](https://arxiv.org/pdf/2010.10631.pdf) |  |
| Multi-Mask Self-Supervised Learning for Physics-Guided Neural Networks in Highly Accelerated MRI | Multi-mask SSDU | 2020 | [PDF](https://arxiv.org/abs/2008.06029) |  |
| Self-Supervised Learning of Physics-Guided Reconstruction Neural Networks without Fully-Sampled Reference Data | Self-supervised via data undersampling (SSDU) | 2020 | [PDF](https://arxiv.org/abs/1912.07669) | [CODE](https://github.com/byaman14/SSDU) |
| Unsupervised MRI Reconstruction with Generative Adversarial Networks | Unsupervised with GAN | 2020 | [PDF](https://arxiv.org/pdf/2008.13065.pdf) | [CODE](https://github.com/MRSRL/unsupGAN-release) |
| Unsupervised Deep Basis Pursuit: Learning inverse problems without ground-truth data | Supervised and Unsupervised end-to-end reconstruction | 2019 | [PDF](https://arxiv.org/pdf/1910.13110.pdf) |  |


## Untrained, Scan-Specific and Implicit Neural Representation Methods
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| DD-INR: Dynamics-Driven Implicit Neural Representation for Accelerated Whole-Brain Functional MRI Reconstruction | INR for accelerated fMRI | 2026 | [PDF](https://arxiv.org/abs/2606.10756) | [CODE](https://github.com/JoosenLi/DD-INR) |
| Physics-Driven Zero-Shot MRI Reconstruction with Non-local Image Priors | Zero-shot with non-local priors | 2026 | [PDF](https://arxiv.org/abs/2606.15110) |  |
| Self-supervised Deep Unrolled Model with Implicit Neural Representation Regularization for Accelerating MRI Reconstruction | Zero-shot unrolled net + INR prior | 2025 | [PDF](https://arxiv.org/abs/2510.06611) |  |
| Three-Dimensional MRI Reconstruction with Gaussian Representations: Tackling the Undersampling Problem | 3D Gaussian splatting from k-space | 2025 | [PDF](https://arxiv.org/abs/2502.06510) |  |
| Test-time Model Adaptation for Image Reconstruction Using Self-supervised Adaptive Layers | Test-time adaptation, adaptive layers | 2024 | [PDF](https://doi.org/10.1007/978-3-031-72913-3_7) | [CODE](https://github.com/yutianzhao-00/TTT-AdaptNet) |
| Towards Architecture-Agnostic Untrained Network Priors for Image Reconstruction with Frequency Regularization | DIP with frequency regularization | 2023 | [PDF](https://arxiv.org/abs/2312.09988) | [CODE](https://github.com/YilinLiu97/Untrained-Recon) |
| IMJENSE: Scan-specific Implicit Representation for Joint Coil Sensitivity and Image Estimation in Parallel MRI | INR joint coil-sensitivity + image | 2023 | [PDF](https://arxiv.org/abs/2311.12892) | [CODE](https://github.com/AMRI-Lab/IMJENSE) |
| Unsupervised reconstruction of accelerated cardiac cine MRI using Neural Fields | Neural fields, single-subject cine | 2023 | [PDF](https://arxiv.org/abs/2307.14363) | [CODE](https://github.com/fsahli/NF-cMRI) |
| Residual RAKI: A hybrid linear and non-linear approach for scan-specific k-space deep learning | Hybrid linear + CNN scan-specific | 2022 | [PDF](https://doi.org/10.1016/j.neuroimage.2022.119248) |  |
| NeRP: Implicit Neural Representation Learning with Prior Embedding for Sparsely Sampled Image Reconstruction | INR with prior-image embedding | 2021 | [PDF](https://arxiv.org/abs/2108.10991) | [CODE](https://github.com/liyues/NeRP) |
| Accelerated MRI with Un-trained Neural Networks | Untrained ConvDecoder | 2020 | [PDF](https://arxiv.org/abs/2007.02471) | [CODE](https://github.com/MLI-lab/ConvDecoder) |
| Deep Image Prior | DIP, untrained CNN as image prior | 2018 | [PDF](https://arxiv.org/abs/1711.10925) | [CODE](https://github.com/DmitryUlyanov/deep-image-prior) |


## Dynamic and Cardiac MRI Reconstruction
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Piecewise Dynamic Diffusion Regularization for Reconstruction of Cardiac Cine MRI | Spatiotemporal diffusion prior, real-time cine | 2026 | [PDF](https://arxiv.org/abs/2607.03299) | [CODE](https://github.com/MLI-lab/pddr) |
| FlowMoDL: Model-Based Deep Learning with Conjugate-Gradient Data Consistency for Highly Accelerated 4D Flow MRI Reconstruction | Unrolled 4D flow, CG data consistency | 2026 | [PDF](https://arxiv.org/abs/2608.25828) |  |
| Motion-Robust Deep Reconstruction for Free-Breathing Cardiac Cine MRI | Free-breathing unrolled cine pipeline | 2026 | [PDF](https://arxiv.org/abs/2605.20687) |  |
| Dynamic MRI Reconstruction Via Dual Deep Priors and Low-Rank Plus Sparse Modeling | Dual deep priors + L+S dynamic | 2026 | [PDF](https://arxiv.org/abs/2605.18709) |  |
| PISCO: Self-Supervised k-Space Regularization for Improved Neural Implicit k-Space Representations of Dynamic MRI | Self-supervised regularizer for neural k-space | 2025 | [PDF](https://arxiv.org/abs/2501.09403) | [CODE](https://github.com/compai-lab/2025-pisco-spieker) |
| JotlasNet: Joint Tensor Low-Rank and Attention-based Sparse Unrolling Network for Accelerating Dynamic MRI | Tensor low-rank + sparse unrolled | 2025 | [PDF](https://arxiv.org/abs/2502.11749) | [CODE](https://github.com/yhao-z/JotlasNet) |
| A multi-dynamic low-rank deep image prior (ML-DIP) for 3D real-time cardiovascular MRI | Low-rank DIP, 3D real-time | 2025 | [PDF](https://arxiv.org/abs/2507.19404) |  |
| Multifrequency Time-Dependent Deep Image Prior for Real-Time Free-Breathing Cardiac Imaging | Zero-shot time-DIP real-time cine | 2025 | [PDF](https://doi.org/10.1002/nbm.70114) |  |
| Subspace Implicit Neural Representations for Real-Time Cardiac Cine MR Imaging | Subspace INR, real-time cine | 2024 | [PDF](https://arxiv.org/abs/2412.12742) | [CODE](https://github.com/wenqihuang/SubspaceINR-CMR) |
| FlowMRI-Net: A Generalizable Self-Supervised 4D Flow MRI Reconstruction network | Self-supervised physics-driven 4D flow | 2024 | [PDF](https://arxiv.org/abs/2410.08856) |  |
| Fully Unsupervised Dynamic MRI Reconstruction via Diffeo-Temporal Equivariance | Equivariance-based unsupervised dynamic | 2024 | [PDF](https://arxiv.org/abs/2410.08646) | [CODE](https://github.com/Andrewwango/ddei) |
| Spatiotemporal implicit neural representation for unsupervised dynamic MRI reconstruction | Unsupervised spatiotemporal INR dynamic | 2023 | [PDF](https://arxiv.org/abs/2301.00127) | [CODE](https://github.com/AMRI-Lab/INR_for_DynamicMRI) |
| Global k-Space Interpolation for Dynamic MRI Reconstruction using Masked Image Modeling | k-space transformer masked modeling (k-GIN) | 2023 | [PDF](https://arxiv.org/abs/2307.12672) | [CODE](https://github.com/JZPeterPan/k-gin) |
| Reconstruction of Cardiac Cine MRI Using Motion-Guided Deformable Alignment and Multi-Resolution Fusion | Motion-guided deformable alignment cine | 2023 | [PDF](https://arxiv.org/abs/2303.04968) |  |
| Neural Implicit k-Space for Binning-free Non-Cartesian Cardiac MR Imaging | Neural implicit k-space (NIK) | 2022 | [PDF](https://arxiv.org/abs/2212.08479) | [CODE](https://github.com/wenqihuang/NIK_MRI) |
| Data-Consistent Non-Cartesian Deep Subspace Learning for Efficient Dynamic MR Image Reconstruction | Deep subspace non-Cartesian dynamic | 2022 | [PDF](https://arxiv.org/abs/2205.01770) |  |
| Deep Low-rank plus Sparse Network for Dynamic MR Imaging | L+S-Net unrolled dynamic | 2021 | [PDF](https://arxiv.org/abs/2010.13677) | [CODE](https://github.com/wenqihuang/LS-Net-Dynamic-MRI) |


## Quantitative, Multi-Contrast and Diffusion-Weighted MRI Reconstruction
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| MRI2Qmap: multi-parametric quantitative mapping with MRI-driven denoising priors | Denoising-prior multi-parametric qMRI | 2026 | [PDF](https://arxiv.org/abs/2603.11316) |  |
| Fully 3D Unrolled Magnetic Resonance Fingerprinting Reconstruction via Staged Pretraining and Implicit Gridding | Fully 3D unrolled MRF (SPUR-iG) | 2026 | [PDF](https://arxiv.org/abs/2601.17143) |  |
| Quantitative mapping from conventional MRI using self-supervised physics-guided deep learning: applications to a large-scale, clinically heterogeneous dataset | Self-supervised physics-guided qMRI, clinical scale | 2026 | [PDF](https://arxiv.org/abs/2601.05063) |  |
| Regularized joint reconstruction and slab combination for accelerated three-dimensional multi-slab diffusion-weighted imaging using multi-scale energy models | Energy-model 3D multi-slab DWI | 2026 | [PDF](https://arxiv.org/abs/2606.01606) |  |
| Physics informed guided diffusion for accelerated multi-parametric MRI reconstruction | Physics-guided diffusion MRF (MRF-DiPh) | 2025 | [PDF](https://arxiv.org/abs/2506.23311) | [CODE](https://github.com/p-mayo/mrf-diph) |
| Accelerating multiparametric quantitative MRI using self-supervised scan-specific implicit neural representation with model reinforcement | Scan-specific INR + model reinforcement (REFINE-MORE) | 2025 | [PDF](https://arxiv.org/abs/2508.00891) | [CODE](https://github.com/I3Tlab/REFINE-MORE) |
| Low-Rank Augmented Implicit Neural Representation for Unsupervised High-Dimensional Quantitative MRI Reconstruction | Zero-shot low-rank INR 3D qMRI (LoREIN) | 2025 | [PDF](https://arxiv.org/abs/2506.09100) | [CODE](https://github.com/zhn00310/LoREIN) |
| INR meets Multi-Contrast MRI Reconstruction | INR joint multi-contrast recon | 2025 | [PDF](https://arxiv.org/abs/2509.04888) |  |
| StoDIP: Efficient 3D MRF image reconstruction with deep image priors and stochastic iterations | 3D MRF deep image prior | 2024 | [PDF](https://arxiv.org/abs/2408.02367) |  |
| Denoising Diffusion Probabilistic Models for Magnetic Resonance Fingerprinting | DDPM prior for MRF | 2024 | [PDF](https://arxiv.org/abs/2410.23318) |  |
| Fast Whole-Brain MR Multi-Parametric Mapping with Scan-Specific Self-Supervised Networks | Scan-specific T1/T2* mapping (Joint MAPLE) | 2024 | [PDF](https://arxiv.org/abs/2408.02988) | [CODE](https://github.com/AmirHeydariGit/joint_maple) |
| NLCG-Net: A Model-Based Zero-Shot Learning Framework for Undersampled Quantitative MRI Reconstruction | Model-based zero-shot T1/T2 mapping | 2024 | [PDF](https://arxiv.org/abs/2401.12004) | [CODE](https://github.com/Xinrui-Jiang/NLCG-Net) |
| DeepEMC-T2 Mapping: Deep Learning-Enabled T2 Mapping Based on Echo Modulation Curve Modeling | DL T2 mapping via EMC model | 2024 | [PDF](https://arxiv.org/abs/2402.19205) |  |
| DuDoUniNeXt: Dual-domain unified hybrid model for single and multi-contrast undersampled MRI reconstruction | Dual-domain unified multi-contrast | 2024 | [PDF](https://arxiv.org/abs/2403.05256) |  |
| Attention-Based Q-Space Deep Learning Generalized for Accelerated Diffusion Magnetic Resonance Imaging | Attention q-space DL accelerated dMRI | 2024 | [PDF](https://doi.org/10.1109/JBHI.2024.3487755) |  |
| PINQI: An End-to-End Physics-Informed Approach to Learned Quantitative MRI Reconstruction | End-to-end physics-informed qMRI | 2023 | [PDF](https://arxiv.org/abs/2306.11023) | [CODE](https://github.com/fzimmermann89/pinqi) |
| Zero-DeepSub: Zero-Shot Deep Subspace Reconstruction for Rapid Multiparametric Quantitative MRI Using 3D-QALAS | Zero-shot deep subspace 3D-QALAS | 2023 | [PDF](https://arxiv.org/abs/2307.01410) | [CODE](https://github.com/yohan-jun/Zero-DeepSub) |
| Accelerated MR Fingerprinting with Low-Rank and Generative Subspace Modeling | Low-rank + generative subspace MRF | 2023 | [PDF](https://arxiv.org/abs/2305.10651) |  |
| Magnetic Resonance Parameter Mapping using Self-supervised Deep Learning with Model Reinforcement | Self-supervised model-reinforced mapping (RELAX-MORE) | 2023 | [PDF](https://arxiv.org/abs/2307.13211) |  |
| DSFormer: A Dual-domain Self-supervised Transformer for Accelerated Multi-contrast MRI Reconstruction | Self-supervised transformer multi-contrast | 2022 | [PDF](https://arxiv.org/abs/2201.10776) |  |
| A Plug-and-Play Approach to Multiparametric Quantitative MRI: Image Reconstruction using Pre-Trained Deep Denoisers | PnP denoiser MRF reconstruction | 2022 | [PDF](https://arxiv.org/abs/2202.05269) | [CODE](https://github.com/ketanfatania/QMRI-PnP-Recon-POC) |
| A Self-Supervised Deep Learning Reconstruction for Shortening the Breathhold and Acquisition Window in Cardiac Magnetic Resonance Fingerprinting | DIP + subspace cardiac MRF (DIP-MRF) | 2022 | [PDF](https://doi.org/10.3389/fcvm.2022.928546) |  |
| Multi-Modal Transformer for Accelerated MR Imaging | Multi-modal transformer multi-contrast | 2021 | [PDF](https://arxiv.org/abs/2106.14248) | [CODE](https://github.com/chunmeifeng/MTrans) |


## Motion-Robust Reconstruction
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| MotionDPS: Motion-Compensated 3D Brain MRI Reconstruction | Diffusion posterior joint motion+image+coils | 2026 | [PDF](https://arxiv.org/abs/2605.22121) |  |
| A network-assisted joint image and motion estimation approach for robust 3D MRI motion correction across severity levels | Network-assisted joint 3D rigid MoCo | 2025 | [PDF](https://doi.org/10.1002/mrm.70052) |  |
| Non-rigid Motion Correction for MRI Reconstruction via Coarse-To-Fine Diffusion Models | Coarse-to-fine diffusion non-rigid MoCo | 2025 | [PDF](https://arxiv.org/abs/2505.15057) |  |
| Motion-Robust T2* Quantification from Gradient Echo MRI with Physics-Informed Deep Learning | Physics-informed motion-robust T2* | 2025 | [PDF](https://arxiv.org/abs/2502.17209) |  |
| End-to-End Deep Learning-Based Motion Correction and Reconstruction for Accelerated Whole-Heart Joint T1/T2 Mapping | End-to-end MoCo+recon cardiac T1/T2 | 2025 | [PDF](https://doi.org/10.1016/j.mri.2025.110396) |  |
| Reliable Evaluation of MRI Motion Correction: Dataset and Insights | Real-motion MoCo benchmark (PMoC3D) | 2025 | [PDF](https://arxiv.org/abs/2506.05975) |  |
| MotionTTT: 2D Test-Time-Training Motion Estimation for 3D Motion Corrected MRI | Test-time-training 3D rigid motion | 2024 | [PDF](https://arxiv.org/abs/2409.09370) | [CODE](https://github.com/MLI-lab/MRI_MotionTTT) |
| Moner: Motion Correction in Undersampled Radial MRI with Unsupervised Neural Representation | Unsupervised INR MoCo radial | 2024 | [PDF](https://arxiv.org/abs/2409.16921) | [CODE](https://github.com/iwuqing/Moner) |
| IM-MoCo: Self-supervised MRI Motion Correction using Motion-Guided Implicit Neural Representations | Self-supervised motion-guided INR MoCo | 2024 | [PDF](https://arxiv.org/abs/2407.02974) |  |
| Physics-Informed Deep Learning for Motion-Corrected Reconstruction of Quantitative Brain MRI | Physics-informed MoCo T2* mapping (PHIMO) | 2024 | [PDF](https://arxiv.org/abs/2403.08298) | [CODE](https://github.com/HannahEichhorn/PHIMO) |
| A Unified Deep Learning Framework for Motion Correction in Medical Imaging | Unified rigid/non-rigid MoCo (UniMo) | 2024 | [PDF](https://arxiv.org/abs/2409.14204) | [CODE](https://github.com/IntelligentImaging/UNIMO) |
| Unrolled and rapid motion-compensated reconstruction for cardiac CINE MRI | Unrolled MCMR cardiac cine, journal | 2024 | [PDF](https://doi.org/10.1016/j.media.2023.103017) |  |
| Motion-compensated MR CINE reconstruction with reconstruction-driven motion estimation | Reconstruction-driven motion estimation | 2023 | [PDF](https://arxiv.org/abs/2302.02504) | [CODE](https://github.com/JZPeterPan/MCMR-Recon-Driven-Motion) |
| Data Consistent Deep Rigid MRI Motion Correction | Data-consistent rigid MoCo, test-time opt | 2023 | [PDF](https://arxiv.org/abs/2301.10365) | [CODE](https://github.com/nalinimsingh/neuroMoCo) |
| SISMIK for brain MRI: Deep-learning-based motion estimation and model-based motion correction in k-space | k-space DL motion estimation + model MoCo | 2023 | [PDF](https://arxiv.org/abs/2312.13220) |  |
| Deep Learning for Retrospective Motion Correction in MRI: A Comprehensive Review | Review of DL retrospective MoCo | 2023 | [PDF](https://arxiv.org/abs/2305.06739) |  |
| Accelerated Motion Correction with Deep Generative Diffusion Models | Score-based joint MoCo + reconstruction | 2022 | [PDF](https://arxiv.org/abs/2211.00199) | [CODE](https://github.com/utcsilab/motion_score_mri) |
| Learning-based and unrolled motion-compensated reconstruction for cardiac MR CINE imaging | Unrolled MCMR with embedded motion net | 2022 | [PDF](https://arxiv.org/abs/2209.03671) |  |
| CoRRECT: A Deep Unfolding Framework for Motion-Corrected Quantitative R2* Mapping | Deep unfolding motion-corrected R2* | 2022 | [PDF](https://arxiv.org/abs/2210.06330) | [CODE](https://github.com/xuxiaojian/CoRRECT_QCSMRI) |
| Deep learning-based motion quantification from k-space for fast model-based magnetic resonance imaging motion correction | k-space rigid motion quantification (MoPED) | 2022 | [PDF](https://doi.org/10.1002/mp.16119) |  |


## Non-Cartesian, 3D and Low-Field Reconstruction
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Weakly Convex Ridge Regularization for 3D Non-Cartesian MRI Reconstruction | Learned weakly-convex regularizer 3D non-Cartesian | 2026 | [PDF](https://arxiv.org/abs/2603.27158) |  |
| Rapid online deep artifact suppression for real-time spiral bSSFP CMR with blipped-CAIPI simultaneous multi-slice imaging at 1.5 T | Online DL spiral SMS real-time CMR | 2026 | [PDF](https://arxiv.org/abs/2605.26127) |  |
| Physics-Guided Dual-Domain Network with Attention-Based Fusion for Portable MRI Reconstruction | Dual-domain portable low-field recon | 2026 | [PDF](https://arxiv.org/abs/2602.19829) |  |
| Interlaced R2D2 DNN Series for Scalable Non-Cartesian MRI with Sensitivity Self-calibration | Self-calibrated R2D2 non-Cartesian | 2025 | [PDF](https://arxiv.org/abs/2503.09559) |  |
| Hybrid Learning: A Novel Combination of Self-Supervised and Supervised Learning for Joint MRI Reconstruction and Denoising in Low-Field MRI | Hybrid self/supervised low-field recon | 2025 | [PDF](https://arxiv.org/abs/2505.05703) |  |
| Diffusion Probabilistic Generative Models for Accelerated, in-NICU Permanent Magnet Neonatal MRI | Diffusion prior neonatal permanent-magnet MRI | 2025 | [PDF](https://arxiv.org/abs/2505.15984) |  |
| Deep Learning Reconstruction for 7T MP2RAGE and SPACE MRI: Improving Image Quality at High Acceleration Factors | 7T DL reconstruction, high acceleration | 2025 | [PDF](https://doi.org/10.3174/ajnr.A8841) |  |
| Accelerating Low-field MRI: From Compressed Sensing to Deep Learning Reconstruction with CNNs and Transformers | Low-field reconstruction overview | 2024 | [PDF](https://arxiv.org/abs/2411.06704) |  |
| Benchmarking 3D multi-coil NC-PDNet MRI reconstruction | 3D multi-coil NC-PDNet benchmark | 2024 | [PDF](https://arxiv.org/abs/2411.05883) |  |
| Scalable Non-Cartesian Magnetic Resonance Imaging with R2D2 | R2D2 DNN series non-Cartesian | 2024 | [PDF](https://arxiv.org/abs/2403.17905) |  |
| Robust Simultaneous Multislice MRI Reconstruction Using Slice-Wise Learned Generative Diffusion Priors | Diffusion prior SMS EPI/FSE (ROGER) | 2024 | [PDF](https://arxiv.org/abs/2407.21600) | [CODE](https://github.com/Solor-pikachu/ROGER) |
| Deep-ER: Deep Learning ECCENTRIC Reconstruction for fast high-resolution neurometabolic imaging | DL non-Cartesian MRSI recon, 7T | 2024 | [PDF](https://arxiv.org/abs/2409.18303) |  |
| DARCS: Memory-Efficient Deep Compressed Sensing Reconstruction for Acceleration of 3D Whole-Heart Coronary MR Angiography | Memory-efficient 3D coronary MRA | 2024 | [PDF](https://arxiv.org/abs/2402.00320) |  |
| Whole-body magnetic resonance imaging at 0.05 Tesla | 0.05T whole-body, DL EMI + 3D recon | 2024 | [PDF](https://doi.org/10.1126/science.adm7168) |  |
| Non-Cartesian Self-Supervised Physics-Driven Deep Learning Reconstruction for Highly-Accelerated Multi-Echo Spiral fMRI | Self-supervised spiral multi-echo fMRI 10x | 2023 | [PDF](https://arxiv.org/abs/2312.05707) |  |
| Deep learning enabled fast 3D brain MRI at 0.055 tesla | 0.055T DL fast 3D brain | 2023 | [PDF](https://doi.org/10.1126/sciadv.adi9327) |  |
| Meta-Learning Enabled Score-Based Generative Model for 1.5T-Like Image Reconstruction from 0.5T MRI | Meta-learned SGM 0.5T reconstruction | 2023 | [PDF](https://arxiv.org/abs/2305.02509) |  |
| Memory Efficient Model Based Deep Learning Reconstructions for High Spatial Resolution 3D Non-Cartesian Acquisitions | Block-wise memory-efficient 3D non-Cartesian MoDL | 2022 | [PDF](https://arxiv.org/abs/2204.13862) |  |
| A Projection-Based K-space Transformer Network for Undersampled Radial MRI Reconstruction with Limited Training Subjects | Projection-domain k-space transformer radial | 2022 | [PDF](https://arxiv.org/abs/2206.07219) |  |
| Deep learning for fast low-field MRI acquisitions | Residual U-Net 0.1T undersampled | 2022 | [PDF](https://doi.org/10.1038/s41598-022-14039-7) |  |
| A low-cost and shielding-free ultra-low-field brain MRI scanner | 0.055T scanner + DL EMI cancellation | 2021 | [PDF](https://doi.org/10.1038/s41467-021-27317-1) |  |
| 20-fold Accelerated 7T fMRI Using Referenceless Self-Supervised Deep Learning Reconstruction | Self-supervised 7T fMRI 20x | 2021 | [PDF](https://arxiv.org/abs/2105.05827) |  |
| Memory-efficient Learning for High-Dimensional MRI Reconstruction | MEL for 3D / 2D+t unrolled training | 2021 | [PDF](https://arxiv.org/abs/2103.04003) | [CODE](https://github.com/mikgroup/MEL_MRI) |


## Learned Sampling and Joint Acquisition-Reconstruction Optimization
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| NexOP: Joint Optimization of NEX-Aware k-space Sampling and Image Reconstruction for Low-Field MRI | Joint sampling/recon across averages, low-field | 2026 | [PDF](https://arxiv.org/abs/2605.11583) |  |
| Flow-Based Generative Modeling for Optimizing Sampling Policies in Compressed Sensing Applications | Flow-matching prior for sampling policy | 2026 | [PDF](https://arxiv.org/abs/2606.00078) |  |
| Scan-Adaptive Dynamic MRI Undersampling Using a Dictionary of Efficiently Learned Patterns | Scan-adaptive dynamic mask dictionary | 2026 | [PDF](https://arxiv.org/abs/2602.13984) | [CODE](https://github.com/sidgautam95/rbicd-dynamic-mri-sampling) |
| On The Role of K-Space Acquisition in MRI Reconstruction Domain-Generalization | Learned trajectories with acquisition perturbation | 2025 | [PDF](https://arxiv.org/abs/2512.06530) |  |
| Learning Scan-Adaptive MRI Undersampling Patterns with Pre-Optimized Mask Supervision | CNN predicts scan-specific masks | 2025 | [PDF](https://arxiv.org/abs/2509.16846) |  |
| End-to-end Adaptive Dynamic Subsampling and Reconstruction for Cardiac MRI | Adaptive dynamic sampling policy + vSHARP | 2024 | [PDF](https://arxiv.org/abs/2403.10346) |  |
| AutoSamp: Autoencoding k-space Sampling via Variational Information Maximization for 3D MRI | Variational info-max 3D non-Cartesian sampling | 2023 | [PDF](https://arxiv.org/abs/2306.02888) | [CODE](https://github.com/alkanc/autosamp) |
| Optimizing Sampling Patterns for Compressed Sensing MRI with Diffusion Generative Models | Diffusion-prior sampling optimization | 2023 | [PDF](https://arxiv.org/abs/2306.03284) | [CODE](https://github.com/Sriram-Ravula/MRI_sampling_diffusion) |
| Constrained Probabilistic Mask Learning for Task-specific Undersampled MRI Reconstruction | Bernoulli mask learning, task-specific | 2023 | [PDF](https://arxiv.org/abs/2305.16376) | [CODE](https://github.com/saiboxx/bernoulli-mri) |
| L2SR: Learning to Sample and Reconstruct for Accelerated MRI via Reinforcement Learning | Alternating RL sampler/reconstructor | 2022 | [PDF](https://arxiv.org/abs/2212.02190) | [CODE](https://github.com/yangpuPKU/L2SR-Learning-to-Sample-and-Reconstruct) |
| Stochastic Optimization of 3D Non-Cartesian Sampling Trajectory (SNOPY) | 3D non-Cartesian trajectory learning | 2022 | [PDF](https://arxiv.org/abs/2209.11030) | [CODE](https://github.com/guanhuaw/SNOPY) |
| Learning Optimal K-space Acquisition and Reconstruction using Physics-Informed Neural Networks | Neural-ODE trajectory learning | 2022 | [PDF](https://arxiv.org/abs/2204.02480) |  |
| End-to-End Sequential Sampling and Reconstruction for MRI | SeqMRI: sequential adaptive sampling | 2021 | [PDF](https://arxiv.org/abs/2105.06460) | [CODE](https://github.com/tianweiy/SeqMRI) |
| B-spline Parameterized Joint Optimization of Reconstruction and K-space Trajectories (BJORK) for Accelerated 2D MRI | B-spline trajectory + unrolled recon | 2021 | [PDF](https://arxiv.org/abs/2101.11369) | [CODE](https://github.com/guanhuaw/Bjork) |
| Experimental design for MRI by greedy policy search | Policy-gradient adaptive sampling | 2020 | [PDF](https://arxiv.org/abs/2010.16262) | [CODE](https://github.com/Timsey/pg_mri) |
| Active MR k-space Sampling with Reinforcement Learning | RL active acquisition | 2020 | [PDF](https://arxiv.org/abs/2007.10469) | [CODE](https://github.com/facebookresearch/active-mri-acquisition) |
| Deep probabilistic subsampling for task-adaptive compressed sensing | DPS: Gumbel-softmax learned subsampling | 2020 | [PDF](https://openreview.net/forum?id=SJeq9JBFvH) | [CODE](https://github.com/IamHuijben/deep-probabilistic-subsampling) |
| J-MoDL: Joint Model-Based Deep Learning for Optimized Sampling and Reconstruction | Continuous sampling + MoDL joint training | 2019 | [PDF](https://arxiv.org/abs/1911.02945) | [CODE](https://github.com/hkaggarwal/J-MoDL) |
| PILOT: Physics-Informed Learned Optimized Trajectories for Accelerated MRI | Learned non-Cartesian trajectories | 2019 | [PDF](https://arxiv.org/abs/1909.05773) | [CODE](https://github.com/tomer196/PILOT) |
| Deep-learning-based Optimization of the Under-sampling Pattern in MRI | LOUPE journal version | 2019 | [PDF](https://arxiv.org/abs/1907.11374) | [CODE](https://github.com/cagladbahadir/LOUPE) |
| Joint learning of cartesian undersampling and reconstruction for accelerated MRI | Joint Cartesian mask + recon | 2019 | [PDF](https://arxiv.org/abs/1905.09324) |  |
| Learning-based Optimization of the Under-sampling Pattern in MRI | LOUPE: end-to-end mask + U-Net | 2019 | [PDF](https://arxiv.org/abs/1901.01960) | [CODE](https://github.com/cagladbahadir/LOUPE) |


## Low Rank Methods
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| LORAKI: Autocalibrated Recurrent Neural Networks for Autoregressive MRI Reconstruction in k-Space | Learning LORAKS | 2019 | [PDF](https://arxiv.org/abs/1904.09390) |  |
| A General Framework for Compressed Sensing and Parallel MRI Using Annihilating Filter Based Low-Rank Hankel Matrix | Parallel imaging and Compressed Sensing (CS) | 2016 | [PDF](https://ieeexplore.ieee.org/document/7547372) |  |
| Autocalibrated loraks for fast constrained MRI reconstruction | LORAKS | 2015 | [PDF](https://ieeexplore.ieee.org/abstract/document/7164018) |  |


## Classical Methods for Parallel Imaging and Compressed Sensing
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| ESPIRiT—an eigenvalue approach to autocalibrating parallel MRI: Where SENSE meets GRAPPA | Parallel imaging | 2014 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.24751) | [CODE](https://github.com/mikgroup/sigpy) |
| Joint image reconstruction and sensitivity estimation in SENSE (JSENSE) | Parallel imaging | 2007 | [PDF](https://pubmed.ncbi.nlm.nih.gov/17534910/) | [CODE](https://github.com/jkkronk/jsense_mri_reconstruction) |
| Sparse MRI: The Application of Compressed Sensing for Rapid MR Imaging | Compressed Sensing (CS) | 2007 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.21391) | [CODE](https://github.com/peng-cao/mripy) |
| Undersampled Radial MRI with Multiple Coils. Iterative Image Reconstruction Using a Total Variation Constraint | Compressed Sensing (CS) | 2007 | [PDF](https://pubmed.ncbi.nlm.nih.gov/17534903/) |  |
| Robust Uncertainty Principles: Exact Signal Reconstruction from Highly Incomplete Frequency Information | Compressed Sensing (CS) | 2004 | [PDF](https://arxiv.org/pdf/math/0409186.pdf) | [CODE](https://github.com/peng-cao/mripy) |
| POCSENSE: POCS-based reconstruction for sensitivity encoded magnetic resonance imaging | Parallel imaging | 2004 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.20285) | [CODE](https://mrirecon.github.io/bart/) |
| Generalized autocalibrating partially parallel acquisitions (GRAPPA) | Parallel imaging | 2002 | [PDF](https://onlinelibrary.wiley.com/doi/full/10.1002/mrm.10171?sid=nlm%3Apubmed) | [CODE](https://github.com/tetianadadakova/Tutorial-MRI-Reconstruction-Using-GRAPPA) |
| SENSE: sensitivity encoding for fast MRI | Parallel imaging | 1999 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/%28SICI%291522-2594%28199911%2942%3A5%3C952%3A%3AAID-MRM16%3E3.0.CO%3B2-S) | [CODE](https://github.com/mikgroup/sigpy) |
| Simultaneous Acquisition of Spatial Harmonics (SMASH): Fast Imaging with Radiofrequency Coil Arrays Encoded Magnetic Resonance Imaging | Parallel imaging | 1997 | [PDF](https://pubmed.ncbi.nlm.nih.gov/9324327/) |  |


## Uncertainty Estimation
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Pixelwise Uncertainty Quantification of Accelerated MRI Reconstruction | Conformal quantile-regression pixel UQ | 2026 | [PDF](https://arxiv.org/abs/2601.13236) |  |
| Trustworthy MRI Reconstruction via Bayesian Uncertainty Quantification with Sparsity Prior Models | Proximal-MCMC Bayesian UQ | 2026 | [PDF](https://arxiv.org/abs/2606.17343) |  |
| CUTE-MRI: Conformalized Uncertainty-based framework for Time-adaptivE MRI | Conformal UQ for adaptive scan time | 2025 | [PDF](https://arxiv.org/abs/2508.14952) |  |
| QUTCC: Quantile Uncertainty Training and Conformal Calibration for Imaging Inverse Problems | Quantile training + conformal calibration | 2025 | [PDF](https://arxiv.org/abs/2507.14760) |  |
| pcaGAN: Improving Posterior-Sampling cGANs via Principal Component Regularization | PCA-regularized posterior cGAN | 2024 | [PDF](https://arxiv.org/abs/2411.00605) | [CODE](https://github.com/matt-bendel/pcaGAN) |
| Task-Driven Uncertainty Quantification in Inverse Problems via Conformal Prediction | Task-driven conformal UQ | 2024 | [PDF](https://arxiv.org/abs/2405.18527) | [CODE](https://github.com/jwen307/TaskUQ) |
| Uncertainty Estimation and Propagation in Accelerated MRI Reconstruction | Hierarchical-VAE UQ, propagation to segmentation | 2023 | [PDF](https://arxiv.org/abs/2308.02631) | [CODE](https://github.com/paulkogni/MR-Recon-UQ) |
| A Conditional Normalizing Flow for Accelerated Multi-Coil MR Imaging | Conditional normalizing-flow posterior sampling | 2023 | [PDF](https://arxiv.org/abs/2306.01630) | [CODE](https://github.com/jwen307/mri_cnf) |
| Uncertainty Estimation and Out-of-Distribution Detection for Deep Learning-Based Image Reconstruction using the Local Lipschitz | Local-Lipschitz UQ and OOD detection | 2023 | [PDF](https://arxiv.org/abs/2305.07618) |  |
| PixCUE: Joint Uncertainty Estimation and Image Reconstruction in MRI using Deep Pixel Classification | Single-pass pixel-classification UQ | 2023 | [PDF](https://arxiv.org/abs/2303.00111) |  |
| A Regularized Conditional GAN for Posterior Sampling in Image Recovery Problems | Regularized conditional GAN posterior sampling | 2022 | [PDF](https://arxiv.org/abs/2210.13389) | [CODE](https://github.com/matt-bendel/rcGAN) |
| Bayesian MRI Reconstruction with Joint Uncertainty Estimation using Diffusion Models | Score prior, MCMC uncertainty maps | 2022 | [PDF](https://arxiv.org/abs/2202.01479) | [CODE](https://github.com/mrirecon/spreco) |
| Uncertainty Quantification for Deep Unrolling-Based Computational Imaging | Bayesian deep-unrolling UQ | 2022 | [PDF](https://arxiv.org/abs/2207.00698) |  |
| Image-to-Image Regression with Distribution-Free Uncertainty Quantification and Applications in Imaging | Conformal pixel-wise intervals | 2022 | [PDF](https://arxiv.org/abs/2202.05265) | [CODE](https://github.com/aangelopoulos/im2im-uq) |
| Bayesian Uncertainty Estimation of Learned Variational MRI Reconstruction | Epistemic Uncertainty Estimation | 2021 | [PDF](https://arxiv.org/pdf/2102.06665.pdf) |  |
| Uncertainty Quantification in Deep MRI Reconstruction | Uncertainty | 2021 | [PDF](https://arxiv.org/pdf/1901.11228.pdf) |  |
| On hallucinations in tomographic image reconstruction | Hallucination maps for learned recon | 2020 | [PDF](https://arxiv.org/abs/2012.00646) |  |
| Sampling possible reconstructions of undersampled acquisitions in MR imaging | Uncertainty Estimation | 2020 | [PDF](https://arxiv.org/pdf/2010.00042.pdf) |  |


## Robustness, Distribution Shift and Adversarial Attacks
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Triggering hallucinations in model-based MRI reconstruction via adversarial perturbations | Adversarial hallucination attacks | 2026 | [PDF](https://arxiv.org/abs/2602.18536) | [CODE](https://github.com/saeyslab/adversarial-mri) |
| Improving Deep Learning for Accelerated MRI With Data Filtering | Data curation, 48-test-set robustness | 2025 | [PDF](https://arxiv.org/abs/2508.13822) | [CODE](https://github.com/MLI-lab/data_filtering_for_accelerated_mri) |
| D2SA: Dual-Stage Distribution and Slice Adaptation for Efficient Test-Time Adaptation in MRI Reconstruction | Efficient test-time adaptation | 2025 | [PDF](https://arxiv.org/abs/2503.20815) |  |
| Training-Free Adversarial Robustness in Computational MRI | Training-free adversarial mitigation | 2025 | [PDF](https://arxiv.org/abs/2501.01908) |  |
| On Instabilities of Unsupervised Denoising Diffusion Models in Magnetic Resonance Imaging Reconstruction | Adversarial instability of diffusion recon | 2024 | [PDF](https://arxiv.org/abs/2406.16983) |  |
| Steerable Conditional Diffusion for Out-of-Distribution Adaptation in Medical Image Reconstruction | Test-time OOD adaptation of prior | 2023 | [PDF](https://arxiv.org/abs/2308.14409) | [CODE](https://github.com/alexdenker/SteerableConditionalDiffusion) |
| Robustness of Deep Learning for Accelerated MRI: Benefits of Diverse Training Data | Diverse training data for robustness | 2023 | [PDF](https://arxiv.org/abs/2312.10271) | [CODE](https://github.com/MLI-lab/mri_data_diversity) |
| Robust Physics-based Deep MRI Reconstruction Via Diffusion Purification | Diffusion purification vs adversarial noise | 2023 | [PDF](https://arxiv.org/abs/2309.05794) |  |
| Learning Provably Robust Estimators for Inverse Problems via Jittering | Jittering for worst-case robustness | 2023 | [PDF](https://arxiv.org/abs/2307.12822) | [CODE](https://github.com/MLI-lab/robust_reconstructors_via_jittering) |
| SMUG: Towards robust MRI reconstruction by smoothed unrolling | Randomized smoothing in unrolled nets | 2023 | [PDF](https://arxiv.org/abs/2303.12735) | [CODE](https://github.com/LGM70/SMUG) |
| On Retrospective k-space Subsampling schemes For Deep MRI Reconstruction | Subsampling-scheme sensitivity study | 2023 | [PDF](https://arxiv.org/abs/2301.08365) |  |
| Test-Time Training Can Close the Natural Distribution Shift Performance Gap in Deep Learning Based Compressed Sensing | Test-time training for distribution shift | 2022 | [PDF](https://arxiv.org/abs/2204.07204) | [CODE](https://github.com/MLI-lab/ttt_for_deep_learning_cs) |
| Adversarial Robustness of MR Image Reconstruction under Realistic Perturbations | Realistic k-space/rotation attacks | 2022 | [PDF](https://arxiv.org/abs/2208.03161) | [CODE](https://github.com/NikolasMorshuis/AdvRec) |
| Evaluation of the Robustness of Learned MR Image Reconstruction to Systematic Deviations Between Training and Test Data for the Models from the fastMRI Challenge | Robustness in FastMRI | 2021 | [PDF](https://link.springer.com/chapter/10.1007/978-3-030-88552-6_3) |  |
| Measuring Robustness in Deep Learning Based Compressive Sensing | Robustness | 2021 | [PDF](https://arxiv.org/pdf/2102.06103.pdf) |  |
| Adversarial Robust Training of Deep Learning MRI Reconstruction Models | Adversarial training for small lesions | 2020 | [PDF](https://arxiv.org/abs/2011.00070) | [CODE](https://github.com/fcaliva/fastMRI_BB_abnormalities_annotation) |
| Improving Robustness of Deep-Learning-Based Image Reconstruction | Robustness | 2020 | [PDF](https://arxiv.org/pdf/2002.11821.pdf) |  |
| On instabilities of deep learning in image reconstruction and the potential costs of AI | Robustness review | 2019 | [PDF](https://arxiv.org/pdf/1902.05300.pdf) | [CODE](https://github.com/vegarant/Invfool) |
| Scan-specific robust artificial-neural-networks for k-space interpolation (RAKI) reconstruction: Database-free deep learning for fast imaging | Supervised CNN Kspace | 2019 | [PDF](https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.27420) | [CODE](https://github.com/zczam/RAKI) |


## Evaluation, Metrics and Clinical Validation
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Evaluation of Machine Learning Reconstruction Techniques for Accelerated Brain MRI Scans | Neuroradiologist reader study, 4x brain | 2025 | [PDF](https://arxiv.org/abs/2509.07193) |  |
| Mind the Detail: Uncovering Clinically Relevant Image Details in Accelerated MRI with Semantically Diverse Reconstructions | Diverse recon recovers missed pathology | 2025 | [PDF](https://arxiv.org/abs/2507.00670) | [CODE](https://github.com/NikolasMorshuis/SDR) |
| Correlation of objective image quality metrics with radiologists' diagnostic confidence depends on the clinical task performed | IQMs vs task-specific radiologist confidence | 2025 | [PDF](https://doi.org/10.1117/1.JMI.12.5.051803) |  |
| Using deep feature distances for evaluating the perceptual quality of MR image reconstructions | Deep feature distances vs radiologists | 2025 | [PDF](https://doi.org/10.1002/mrm.30437) |  |
| Prospective Evaluation of Accelerated Brain MRI Using Deep Learning-Based Reconstruction: Simultaneous Application to 2D Spin-Echo and 3D Gradient-Echo Sequences | Prospective clinical brain evaluation | 2025 | [PDF](https://doi.org/10.3348/kjr.2024.0653) |  |
| Deep-learning-based reconstruction of undersampled MRI to reduce scan times: a multicentre, retrospective, cohort study | Multicentre glioma clinical validation | 2024 | [PDF](https://doi.org/10.1016/S1470-2045%2823%2900641-1) |  |
| Hallucination Index: An Image Quality Metric for Generative Reconstruction Models | Hellinger-distance hallucination metric | 2024 | [PDF](https://arxiv.org/abs/2407.12780) |  |
| A study of why we need to reassess full reference image quality assessment with medical images | PSNR/SSIM pitfalls in medical IQA | 2024 | [PDF](https://arxiv.org/abs/2405.19097) |  |
| A study on the adequacy of common IQA measures for medical images | IQA measures vs expert ratings | 2024 | [PDF](https://arxiv.org/abs/2405.19224) |  |
| Death by Retrospective Undersampling - Caveats and Solutions for Learning-Based MRI Reconstructions | Retrospective vs prospective undersampling caveat | 2024 | [PDF](https://doi.org/10.1007/978-3-031-72104-5_23) | [CODE](https://git5.cs.fau.de/rajput/death-by-retrospective-undersampling) |
| Deep Learning Reconstruction Enables Prospectively Accelerated Clinical Knee MRI | Prospective knee reader study, 2x | 2023 | [PDF](https://doi.org/10.1148/radiol.220425) |  |
| Image Quality Assessment for Magnetic Resonance Imaging | 35 IQA metrics vs 7 radiologists | 2022 | [PDF](https://arxiv.org/abs/2203.07809) |  |
| Exploring the Acceleration Limits of Deep Learning Variational Network-based Two-dimensional Brain MRI | Radiologist-rated acceleration limits | 2022 | [PDF](https://doi.org/10.1148/ryai.210313) |  |
| End-to-End AI-based MRI Reconstruction and Lesion Detection Pipeline for Evaluation of Deep Learning Image Reconstruction | Lesion-detection-based recon evaluation | 2021 | [PDF](https://arxiv.org/abs/2109.11524) |  |


## Datasets
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| MosaicMRI: A Diverse Dataset and Benchmark for Raw Musculoskeletal MRI | Raw MSK k-space, 10 anatomies | 2026 | [PDF](https://arxiv.org/abs/2604.11762) | [CODE](https://github.com/AIF4S/mosaicmri) |
| Enabling Ultra-Fast Cardiovascular Imaging Across Heterogeneous Clinical Environments with A Generalist Foundation Model and Multimodal Database | MMCMR-427K multi-center CMR k-space | 2025 | [PDF](https://arxiv.org/abs/2512.21652) | [CODE](https://github.com/wangziblake/CardioMM_MMCMR-427K) |
| Diff5T: Benchmarking Human Brain Diffusion MRI with an Extensive 5.0 Tesla K-Space and Spatial Dataset | 5T brain diffusion k-space | 2025 | [PDF](https://arxiv.org/abs/2412.06666) |  |
| CMRxRecon2024: A Multi-Modality, Multi-View K-Space Dataset Boosting Universal Machine Learning for Accelerated Cardiac MRI | Multi-modality cardiac k-space | 2024 | [PDF](https://arxiv.org/abs/2406.19043) | [CODE](https://github.com/CmrxRecon/CMRxRecon2024) |
| fastMRI Breast: A publicly available radial k-space dataset of breast dynamic contrast-enhanced MRI | Radial breast DCE k-space | 2024 | [PDF](https://arxiv.org/abs/2406.05270) |  |
| CMRxRecon: A publicly available k-space dataset and benchmark to advance deep learning for cardiac MRI | Cardiac cine/mapping k-space | 2024 | [PDF](https://www.nature.com/articles/s41597-024-03525-4) | [CODE](https://github.com/CmrxRecon/CMRxRecon-SciData) |
| FastMRI Prostate: A Publicly Available, Biparametric MRI Dataset to Advance Machine Learning for Prostate Cancer Imaging | Raw k-space prostate T2/DWI | 2023 | [PDF](https://arxiv.org/abs/2304.09254) | [CODE](https://github.com/cai2r/fastMRI_prostate) |
| M4Raw: A multi-contrast, multi-repetition, multi-channel MRI k-space dataset for low-field MRI research | Low-field 0.3T brain k-space | 2023 | [PDF](https://www.nature.com/articles/s41597-023-02181-4) | [CODE](https://github.com/mylyu/M4Raw) |
| SKM-TEA: A Dataset for Accelerated MRI Reconstruction with Dense Image Labels for Quantitative Clinical Evaluation | qMRI knee k-space + labels | 2021 | [PDF](https://arxiv.org/abs/2203.06823) | [CODE](https://github.com/StanfordMIMI/skm-tea) |
| fastMRI+: Clinical Pathology Annotations for Knee and Brain Fully Sampled Multi-Coil MRI Data | Lesion annotations for fastMRI | 2021 | [PDF](https://arxiv.org/abs/2109.03812) | [CODE](https://github.com/microsoft/fastmri-plus/) |
| OCMR (v1.0)--Open-Access Multi-Coil k-Space Dataset for Cardiovascular Magnetic Resonance Imaging | Cardiac cine multi-coil k-space | 2020 | [PDF](https://arxiv.org/abs/2008.03410) | [CODE](https://ocmr.info/) |
| fastMRI: An Open Dataset and Benchmarks for Accelerated MRI | Machine learning baselines and public dataset | 2019 | [PDF](https://arxiv.org/pdf/1811.08839.pdf) | [CODE](https://github.com/facebookresearch/fastMRI/) |


## Challenges and Benchmarks
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| Towards Modality- and Sampling-Universal Learning Strategies for Accelerating Cardiovascular Imaging: Summary of the CMRxRecon2024 Challenge | CMRxRecon2024 challenge results | 2025 | [PDF](https://arxiv.org/abs/2503.03971) | [CODE](https://github.com/CmrxRecon/CMRxRecon2024) |
| Understanding Benefits and Pitfalls of Current Methods for the Segmentation of Undersampled MRI Data | Benchmark: segmentation under undersampling | 2025 | [PDF](https://arxiv.org/abs/2508.18975) |  |
| The state-of-the-art in Cardiac MRI Reconstruction: Results of the CMRxRecon Challenge in MICCAI 2023 | CMRxRecon 2023 challenge results | 2024 | [PDF](https://arxiv.org/abs/2404.01082) | [CODE](https://github.com/CmrxRecon/CMRxRecon-SciData) |
| Multi-Coil MRI Reconstruction Challenge—Assessing Brain MRI Reconstruction Models and Their Generalizability to Varying Coil Configurations | Calgary-Campinas MC-MRRec challenge | 2022 | [PDF](https://doi.org/10.3389/fnins.2022.919186) | [CODE](https://sites.google.com/view/calgary-campinas-dataset/mr-reconstruction-challenge) |
| Results of the 2020 fastMRI Challenge for Machine Learning MR Image Reconstruction | Competition results | 2021 | [PDF](https://arxiv.org/abs/2012.06318) |  |
| Advancing machine learning for MR image reconstruction with an open competition: Overview of the 2019 fastMRI challenge | 2019 fastMRI challenge results | 2020 | [PDF](https://arxiv.org/abs/2001.02518) | [CODE](https://github.com/facebookresearch/fastMRI) |
| Benchmarking MRI Reconstruction Neural Networks on Large Public Datasets | Benchmark | 2020 | [PDF](https://doi.org/10.3390/app10051816) |  |


## Software and Toolboxes
| Title | Short | Year | PDF | CODE |
| :-----|:---:|:---:|:----:|:----:|
| BART Streams: Real-Time Reconstruction Using a Modular Framework for Pipeline Processing | BART real-time streaming pipelines | 2026 | [PDF](https://doi.org/10.1002/mrm.70455) | [CODE](https://codeberg.org/mrirecon/bart) |
| MRpro: open framework for model-based, learned, and quantitative MR imaging | PyTorch MR recon toolbox | 2025 | [PDF](https://arxiv.org/abs/2507.23129) | [CODE](https://github.com/PTB-MR/mrpro) |
| DeepInverse: A Python package for solving imaging inverse problems with deep learning | PyTorch inverse-problems library | 2025 | [PDF](https://arxiv.org/abs/2505.20160) | [CODE](https://github.com/deepinv/deepinv) |
| MRI-NUFFT: Doing non-Cartesian MRI has never been easier | Non-Cartesian NUFFT toolbox | 2025 | [PDF](https://doi.org/10.21105/joss.07743) | [CODE](https://github.com/mind-inria/mri-nufft) |
| Deep, Deep Learning with BART | Deep learning in BART | 2023 | [PDF](https://arxiv.org/abs/2202.14005) | [CODE](https://codeberg.org/mrirecon/bart) |
| DIRECT: Deep Image REConstruction Toolkit | PyTorch DL MRI recon toolkit | 2022 | [PDF](https://doi.org/10.21105/joss.04278) | [CODE](https://github.com/NKI-AI/direct) |
| MIRTorch: A PyTorch-powered Differentiable Toolbox for Fast Image Reconstruction and Scan Protocol Optimization | Differentiable PyTorch recon toolbox | 2022 | [PDF](https://archive.ismrm.org/2022/4982.html) | [CODE](https://github.com/guanhuaw/MIRTorch) |
| TensorFlow MRI | TensorFlow operators for MRI | 2022 | [PDF](https://doi.org/10.5281/zenodo.5151590) | [CODE](https://github.com/mrphys/tensorflow-mri) |
| MRIReco.jl: An MRI Reconstruction Framework written in Julia | Julia MRI recon framework | 2021 | [PDF](https://arxiv.org/abs/2101.12624) | [CODE](https://github.com/MagneticResonanceImaging/MRIReco.jl) |
| torchkbnufft: A PyTorch Library for Knitting Non-Uniform Fast Fourier Transforms | PyTorch NUFFT (Kaiser-Bessel) | 2020 | [PDF](https://mmuckley.github.io/assets/publications/2020muckleytorchkbnufft.pdf) | [CODE](https://github.com/mmuckley/torchkbnufft) |
| SigPy: A Python Package for High Performance Iterative Reconstruction | Python iterative recon package | 2019 | [PDF](https://archive.ismrm.org/2019/4819.html) | [CODE](https://github.com/mikgroup/sigpy) |
| Berkeley Advanced Reconstruction Toolbox | BART toolbox (ISMRM) | 2015 | [PDF](https://archive.ismrm.org/2015/2486.html) | [CODE](https://codeberg.org/mrirecon/bart) |


# Credits 
Template credits to [Few-Shot-Semantic-Segmentation-Papers](https://github.com/xiaomengyc/Few-Shot-Semantic-Segmentation-Papers) by [Xiaolin Zhang](https://github.com/xiaomengyc) and [awesome anomaly detection](https://github.com/hoya012/awesome-anomaly-detection) by [Hoseong, Lee @hoya012](https://github.com/hoya012)
