---
layout: page
title: Retrieval System with Coherence Relations
description: Use coherence relations to improve retrieval system performance
img: /assets/img/retrieval_with_coherence.jpg
redict:
importance: 2
category: work
---

<h2> Abstract </h2>
<p> Common image-text joint understanding techniques presume that images and the associated text can universally be characterized by a single implicit model. However, co-occurring images and text can be related in qualitatively different ways, and explicitly modeling it could improve the performance of current joint understanding models. In this paper, we train a Cross-Modal Coherence Modelfor text-to-image retrieval task. Our analysis shows that models trained with image--text coherence relations can retrieve images originally paired with target text more often than coherence-agnostic models. We also show via human evaluation that images retrieved by the proposed coherence-aware model are preferred over a coherence-agnostic baseline by a huge margin. Our findings provide insights into the ways that different modalities communicate and the role of coherence relations in capturing commonsense inferences in text and imagery. </p>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" alt='model structure' src="{{ '/assets/img/retrieval_with_coherence.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Cross-Modal Coherence Model
</div>

<h2> Links </h2>
* [Arxiv](https://arxiv.org/abs/2109.11047) 
* [Code](https://github.com/Hareesh-Ravi/Mutimodal-Discourse) 

<h2> Citation </h2>
<pre>@misc{alikhani2021crossmodal,
    title={Cross-Modal Coherence for Text-to-Image Retrieval}, 
    author={Malihe Alikhani and Fangda Han and Hareesh Ravi and Mubbasir Kapadia and Vladimir Pavlovic and Matthew Stone},
    year={2021},
    eprint={2109.11047},
    archivePrefix={arXiv},
    primaryClass={cs.CV}
}
</pre>

<h2> License </h2>
[Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)