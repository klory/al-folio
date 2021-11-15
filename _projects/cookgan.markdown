---
layout: page
title: CookGAN
description: Meal Image Synthesis from Ingredients
img: /assets/img/cookgan.jpg
<!-- redirect: http://foodai.cs.rutgers.edu:2019/ -->
importance: 1
category: work
---

<h1 class="title"> CookGAN: Meal Image Synthesis from Ingredients</h1>

<table class="table table-bordered text-center">
    <td><a href="https://openaccess.thecvf.com/content_WACV_2020/papers/Han_CookGAN_Meal_Image_Synthesis_from_Ingredients_WACV_2020_paper.pdf"><div>Paper</div></a></td>
    <td><a href="https://github.com/klory/CookGAN"><div>Code</div></a></td>
    <td><a href="http://foodai.cs.rutgers.edu:2019"><div>Demo</div></a></td>
</table>

<h2> Abstract </h2>
<p>In this work we propose a new computational framework, based on generative deep models, for synthesis of photo-realistic food meal images from textual list of its ingredients. Previous works on synthesis of images from text typically rely on pre-trained text models to extract text features, followed by generative neural networks (GAN) aimed to generate realistic images conditioned on the text features. These works mainly focus on generating spatially compact and well-defined categories of objects, such as birds or flowers, but meal images are significantly more complex, consisting of multiple ingredients whose appearance and spatial qualities are further modified by cooking methods. To generate real-like meal images from ingredients, we propose Cook Generative Adversarial Networks (CookGAN), CookGAN first builds an attention-based ingredients-image association model, which is then used to condition a generative neural network tasked with synthesizing meal images. Furthermore, a cycle-consistent constraint is added to further improve image quality and control appearance. Experiments show our model is able to generate meal images corresponding to the ingredients.</p>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/cookgan.jpg' | relative_url }}" alt="model structure" title="example image"/>
    </div>
</div>
<div class="caption">
    CookGAN Framework
</div>

<div class="embed-responsive embed-responsive-16by9">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/0jsteoeuZQY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<h2> Citation </h2>
<pre>@inproceedings{han2020cookgan,
    title={Cookgan: Meal image synthesis from ingredients},
    author={Han, Fangda and Guerrero, Ricardo and Pavlovic, Vladimir},
    booktitle={Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision},
    pages={1450--1458},
    year={2020}
  }  
</pre>

<h2> License </h2>
[Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)