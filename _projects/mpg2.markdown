---
layout: page
title: MPG2
description: Multi-attribute Pizza Generator - Cross-domain Attribute Control with Conditional StyleGAN
img: /assets/img/mpg2.jpg
# redirect: http://foodai.cs.rutgers.edu:2022/
importance: 1
category: work
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid z-depth-1" autoplay loop controls muted>
            <source src="/assets/video/lerp_ingr.mp4" type="video/mp4" />
        </video>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid z-depth-1" autoplay loop controls muted>
            <source src="/assets/video/lerp_view.mp4" type="video/mp4" />
        </video>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <video class="video-fluid z-depth-1" autoplay loop controls muted>
            <source src="/assets/video/lerp_z.mp4" type="video/mp4" />
        </video>
    </div>
</div>

<h2> Abstract </h2>
<p> Multi-attribute conditional image generation is a challenging problem in computervision. We propose Multi-attribute Pizza Generator (MPG), a conditional Generative Neural Network (GAN) framework for synthesizing images from a trichotomy of attributes: content, view-geometry, and implicit visual style. We design MPG by extending the state-of-the-art StyleGAN2, using a new conditioning technique that guides the intermediate feature maps to learn multi-scale multi-attribute entangled representationsof controlling attributes. Because of the complex nature of the multi-attribute image generation problem, we regularize the image generation by predicting the explicit conditioning attributes (ingredients and view). To synthesize a pizza image with view attributesoutside the range of natural training images, we design a CGI pizza dataset PizzaView using 3D pizza models and employ it to train a view attribute regressor to regularize the generation process, bridging the real and CGI training datasets. To verify the efficacy of MPG, we test it on Pizza10, a carefully annotated multi-ingredient pizza image dataset. MPG can successfully generate photo-realistic pizza images with desired ingredients and view attributes, beyond the range of those observed in real-world training data. </p>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/mpg2.jpg' | relative_url }}" alt="model structure" title="example image"/>
    </div>
</div>
<div class="caption">
    MPG2 Framework
</div>

<h2> Links </h2>
<table class="table table-bordered text-center">
      <td><a href="https://arxiv.org/abs/2110.11830"><div>Paper</div></a></td>
      <td><a href="https://github.com/klory/MPG2"><div>Code</div></a></td>
      <td><a href="http://foodai.cs.rutgers.edu:2022"><div>Demo</div></a></td>
</table>

<h2> Citation </h2>
<pre>@misc{han2021multiattribute,
      title={Multi-attribute Pizza Generator: Cross-domain Attribute Control with Conditional StyleGAN}, 
      author={Fangda Han and Guoyao Hao and Ricardo Guerrero and Vladimir Pavlovic},
      year={2021},
      eprint={2110.11830},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
</pre>

<h2> License </h2>
<a href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank">Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)</a>