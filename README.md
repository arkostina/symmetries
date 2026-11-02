
# Exploring Latent Representations for Symmetry Discovery

**Arina Kostina**  
**Accepted Poster — [Paper link at NewInML Workshop @ NeurIPS 2026](https://neurips.cc/virtual/2026/loc/paris/179920)**

This repository accompanies the paper *Exploring Latent Representations for Symmetry Discovery*. It investigates how **latent dimensionality, representation learning, and geometric inductive biases** affect the discovery of continuous symmetries in data. Full paper will be uploaded soon.

## Abstract

The discovery of symmetries in data depends not only on the transformation-learning method but also on the structure of the latent representations in which these transformations are learned. In this work, we investigate how latent dimensionality, representation learning, and geometric inductive biases influence symmetry discovery through oracle-preserving latent flows. Specifically, we examine how different distributional and geometric constraints on latent representations, including Gaussian regularization and spherical geometry, affect the discovery of continuous and periodic transformations, such as rotations. We systematically compare four representation models—an autoencoder (AE), a Gaussian variational autoencoder (VAE), a spherical AE (S-AE), and a spherical VAE (S-VAE)—across different latent dimensions using rotation-augmented MNIST. We evaluate the discovered transformations in terms of rotational coverage, reconstruction fidelity, trajectory continuity, and oracle preservation. Our results show that latent-space structure substantially influences the symmetries recovered, with spherical representations often supporting broader rotational transformations, while revealing trade-offs between geometric coverage, transformation fidelity, and semantic preservation. These findings highlight the role of latent geometry as an inductive bias in symmetry discovery.

## Overview

We study **oracle-preserving latent flows (OPLF)**, which learn continuous transformations in a latent space while encouraging a task-specific oracle's output to remain stable. Our experiments examine the effect of changing the representation's geometry rather than assuming that a single latent geometry is universally optimal.

| Representation | Latent geometry | Transformation model |
| --- | --- | --- |
| AE | Euclidean | OPLF |
| VAE | Euclidean | OPLF |
| S-AE | Spherical / product of spheres | S-OPLF |
| S-VAE | Spherical / product of spheres | S-OPLF |

The evaluation uses rotation-augmented MNIST, with comparisons across latent dimensions. We investigate how geometry influences:

- **Rotation coverage:** how far the learned transformations travel in rotational terms.
- **Rotation fidelity:** how closely decoded outputs resemble rotations of the initial image.
- **Trajectory consistency and continuity:** whether the inferred rotations progress coherently and without large angular jumps.
- **Oracle preservation:** whether a digit-classification oracle remains consistent along the learned trajectory.

## Citation

If you use this work or its implementation, please cite:

```bibtex
@misc{kostina2026geometry,
  author       = {Kostina, Arina},
  title        = {Geometry-Aware Oracle-Preserving Flows on Spherical Latent Spaces},
  year         = {2026},
  howpublished = {New in Machine Learning (NewInML) Workshop at NeurIPS 2026},
  note         = {Accepted poster, non-archival workshop}
}
```

## Workshop

[NewInML at NeurIPS 2026](https://newinml.github.io/NewInML2026NeurIPS/) · Paris, France · December 2026
