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

StyleGANs<d-cite key="karras2019style, karras2020analyzing, karras2021alias"></d-cite> are a series of generative models that generate high-quality images from a latent space (e.g. random noise).

# Evolution

## ProgressiveGAN<d-cite key="karras2017progressive"></d-cite>
![](/assets/img/2021-10-30-evolution-of-stylegan/2021-11-12-19-23-01.png).

### Progressive Growing
> Generate better low-resolution images, then growing to high-resolution.

![](/assets/img/2021-10-30-evolution-of-stylegan/2021-11-13-14-17-38.png)

G and D are only defined once. But in each G has several `to_rgb` layers, which are used to generate images at different resolutions. After training, only the last `to_rgb` layer is used to generate the image at high resolution. The layers related to smaller resolution are trained first, and then fine-tuned together with the layers related to larger resolution.

### Minibatch Standard Deviation
> Encouraging the minibatches of generated and training images to show similar statistics.

From [official code](https://github.com/NVlabs/stylegan2-ada-pytorch/blob/6f160b3d22b8b178ebe533a50d4d5e63aedba21d/training/networks.py#L589): 

``` python
class MinibatchStdLayer(torch.nn.Module):
    def __init__(self, group_size, num_channels=1):
        super().__init__()
        self.group_size = group_size
        self.num_channels = num_channels

    def forward(self, x):
        N, C, H, W = x.shape
        with misc.suppress_tracer_warnings(): # as_tensor results are registered as constants
            G = torch.min(torch.as_tensor(self.group_size), torch.as_tensor(N)) if self.group_size is not None else N
        F = self.num_channels
        c = C // F

        y = x.reshape(G, -1, F, c, H, W)    # [GnFcHW] Split minibatch N into n groups of size G, and channels C into F groups of size c.
        y = y - y.mean(dim=0)               # [GnFcHW] Subtract mean over group.
        y = y.square().mean(dim=0)          # [nFcHW]  Calc variance over group.
        y = (y + 1e-8).sqrt()               # [nFcHW]  Calc stddev over group.
        y = y.mean(dim=[2,3,4])             # [nF]     Take average over channels and pixels.
        y = y.reshape(-1, F, 1, 1)          # [nF11]   Add missing dimensions.
        y = y.repeat(G, 1, H, W)            # [NFHW]   Replicate over group and pixels.
        x = torch.cat([x, y], dim=1)        # [NCHW]   Append to input as new channels.
        return x
``` 

Basically, it generates an additional channel with the variance of all input images of size [CHW] and append it to the input.

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

