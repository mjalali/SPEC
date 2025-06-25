# SPEC Embedding Comparison

The Project page for ICML 2025 paper: [Towards an Explainable Comparison and Alignment of Feature Embeddings](https://arxiv.org/abs/2506.06231)

## Abstract 
Feature embedding models have been widely applied to many downstream tasks across various domains. While several standard feature embeddings have been developed in the literature, comparisons of these embeddings have largely focused on their numerical performance in classification-related downstream applications. However, an interpretable comparison of different embeddings requires identifying and analyzing mismatches between similar sample groups clustered within the embedding spaces. In this work, we propose the _Spectral Pairwise Embedding Comparison (SPEC)_ framework to compare embeddings and identify their differences in clustering a benchmark dataset. Our approach examines the kernel matrices derived from two embeddings and leverages the eigendecomposition of the differential kernel matrix to detect sample clusters that are captured differently by the two embeddings. We present a scalable implementation of this kernel-based approach, with computational complexity that grows linearly with the sample size. Furthermore, we introduce an optimization problem using this framework to align two embeddings, enhancing interpretability by correcting potential biases and mismatches, and ensuring that clusters identified in one embedding are also captured in the other. Finally, we provide numerical results showcasing the application of the SPEC framework to compare and align standard embeddings on large-scale datasets such as ImageNet and MS-COCO.

## What is SPEC?
Modern embedding models—such as CLIP and DINOv2 deliver strong downstream accuracy, yet numerical scores alone do not explain *how* the embeddings differ. SPEC fills this gap.

Given two embeddings, SPEC

1. Computes a kernel matrix for each embedding over a reference dataset.  
2. Forms their *difference* kernel.  
3. Spectrally decomposes that difference.  

Each eigenvector identifies a cluster of samples that one embedding groups but the other does not; the associated eigenvalue quantifies the strength of that mismatch.

The naïve eigen-solve scales as O(n³). SPEC avoids that cost: for bounded feature dimension *d* (or its random-Fourier proxy) the key eigenspace is recoverable in O(max{d³, n}) time—linear in sample size for practical *d* values.

## Contributions

* SPEC: kernel-difference eigendecomposition for explainable embedding comparison
* Linear-time computation via random Fourier features
* SPEC-diff: spectral distance measuring maximal cluster mismatch
* SPEC-align: gradient-based method to align embeddings (in `spec-align/`)


## Bibtex Citation
If you find SPEC useful for your work, please cite:

```bibtex
@inproceedings{
    jalali2025spec,
    title={Towards an Explainable Comparison and Alignment of Feature Embeddings},
    author={Mohammad Jalali and Bahar Dibaei Nia and Farzan Farnia},
    booktitle={Forty-second International Conference on MachineLearning},
    year={2025},
    url={https://openreview.net/forum?id=Doi0G4UNgt}
}

```
