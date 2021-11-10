---
layout: distill
title: Evolution of StyleGAN
description: How StyleGAN is gradually evolving up to the current version.
date: 2021-10-30

authors:
  - name: Fangda Han
    url: "https://klory.github.io/"
    # affiliations:
    #   name: Myself

bibliography: distill.bib

output:
  distill::distill_article:
    toc: true
    toc_depth: 2
---

# Still Working on it

StyleGANs<d-cite key="karras2019style, karras2020analyzing, karras2021alias"></d-cite> are a series of generative models that generate high-quality images from a latent space.

# Evolution

## ProgressiveGAN<d-cite key="karras2017progressive"></d-cite>


## StyleGAN<d-cite key="karras2019style"></d-cite>


## StyleGAN2<d-cite key="karras2020analyzing"></d-cite>


## StyleGAN2-ada<d-cite key="karras2020training"></d-cite>

## StyleGAN3<d-cite key="karras2021alias"></d-cite>

# Project to latent space
It involves project a real images to the latent space of StyleGAN, which is a preliminary to [munipulate image](#munipulate-image).

## StyleGAN2 projector<d-cite key="karras2020analyzing"></d-cite>

## e2e projector<d-cite key="tov2021designing"></d-cite>

# Control Image
It involves control certain attribute of an image by first map the image into the latent space of StyleGAN, then move the latent space towards the targeting direction.

## GANSpace<d-cite key="harkonen2020ganspace"></d-cite>

## GANControl<d-cite key="shoshan2021gan"></d-cite>

## MPG2<d-cite key="han2021multi"></d-cite>

## SeFa<d-cite key="shen2021closed"></d-cite>

## InterFaceGAN<d-cite key="shen2020interfacegan"></d-cite>

## StyleSpace<d-cite key="wu2021stylespace"></d-cite>

## StyleClip<d-cite key="patashnik2021styleclip"></d-cite>
![](/assets/img//2021-10-30-evolution-of-stylegan/2021-11-10-08-45-13.png)

### Latent Optimization
![](/assets/img/2021-10-30-evolution-of-stylegan/2021-11-10-00-20-09.png)

### Latent Mapper

