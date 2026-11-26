# Exploring Latent Representations for Rotational Symmetry Discovery

**Arina Kostina**  
**Accepted poster — [NewInML Workshop @ NeurIPS 2026](https://neurips.cc/virtual/2026/loc/paris/179920)**

This repository accompanies *Exploring Latent Representations for Rotational Symmetry Discovery*, accepted under the title *Geometry-Aware Oracle-Preserving Flows on Spherical Latent Spaces*. We investigate how latent geometry, dimensionality, and the representation's training objective affect the discovery of rotation-like transformations.

## Overview

Oracle-preserving latent flows (OPLF) learn transformations in a latent space while encouraging a task-specific oracle's output to remain unchanged. Here, the oracle predicts digit identity from the latent representation.

We compare four autoencoder models on rotation-augmented MNIST digits 3 and 4:

| Model | Latent geometry | Training objective |
| --- | --- | --- |
| AE | Euclidean | Reconstruction |
| VAE | Euclidean | Reconstruction + Gaussian-prior KL regularization |
| S-AE | Sphere or product of spheres | Reconstruction |
| S-VAE | Sphere or product of spheres | Reconstruction + uniform-prior KL regularization |

We compare representations with **intrinsic dimensions 2 and 4**. Euclidean models use 2 and 4 coordinates, respectively. Spherical models use 3 coordinates on the unit sphere, or 6 coordinates on a product of two spheres. These have the same intrinsic dimensions as their Euclidean counterparts.

## Evaluation

We evaluate the decoded trajectories using:

- **Rotation coverage:** absolute net angular displacement, normalized and capped at 120°.
- **Rotation fidelity:** agreement with geometric rotations of the initial decoded image.
- **Angular continuity:** the fraction of consecutive retained frames whose estimated angular change lies between 3° and 25°, inclusive. This penalizes both stationary frames and large angular jumps.
- **Digit flip rate:** the fraction of transformed latent states whose oracle prediction differs from the original digit label.

The **rotation score** combines coverage, fidelity, and continuity through their harmonic mean, scaled to 0–100. Digit flip rate is reported separately.

## Results

The following rotation scores are averaged over **200 trajectories** for each model, using seed 0:

| Intrinsic dimension | AE | VAE | S-AE | S-VAE |
| --- | ---: | ---: | ---: | ---: |
| 2 | 44.96 | **63.01** | 27.47 | 28.50 |
| 4 | 15.17 | 59.21 | 66.76 | **85.76** |

Two main patterns emerge:

- **The relative performance of Euclidean and spherical representations varies with intrinsic dimension.** At dimension 2, both Euclidean models outperform their spherical counterparts. At dimension 4, the pattern reverses, with the product-of-spheres S-VAE achieving the highest overall score.
- **Variational models outperform their deterministic counterparts in most tested settings.** This suggests that the training objective may contribute to the observed differences alongside latent geometry.

The best-performing model at each intrinsic dimension remains the same in a second training run with a different random seed. The dimension-2 spherical models achieve substantial angular coverage but low continuity; the illustrated trajectories often become nearly stationary after an initial rotation.

These scores measure rotation-like behavior, rather than success at discovering any symmetry. The training objective encourages preservation of the oracle's logit output without explicitly selecting rotation, so learned transformations can also change stroke thickness, shape, or style.

## Citation

The workshop listing retains the original accepted title. Please cite:

```bibtex
@misc{kostina2026geometry,
  author       = {Kostina, Arina},
  title        = {Geometry-Aware Oracle-Preserving Flows on Spherical Latent Spaces},
  year         = {2026},
  howpublished = {New in Machine Learning (NewInML) Workshop at NeurIPS 2026},
  note         = {Accepted poster, non-archival workshop},
  url          = {https://neurips.cc/virtual/2026/loc/paris/179920}
}
```

## Workshop

[NewInML at NeurIPS 2026](https://newinml.github.io/NewInML2026NeurIPS/)
