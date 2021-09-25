---
layout: post
title: Make wandb ignore files for a project
description: Make wandb ignore files for a project
date: 2021-09-24
comments: true
---

## What is WandB

[WandB](https://wandb.ai/) is a handy tool to visualize training process as well as cross-validate hyper-parameters. One thing wandb do is it automatically uploads all files in `wandb.run.dir`. However you only get [100GB](https://wandb.ai/subscriptions) for free, and when you save a lot of checkpoints, videos, images, it's easily become full. 

While I know we can just create another folder to save our large files, but I kind of like how wandb name each run, so I still prefer saving to `wandb.run.dir`. (and sometimes it took too long to upload all files...)

<div class='row mt-3'>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ site.baseurl }}/assets/img/wandb-run-dir.jpg" data-zoomable>
    </div>
</div>


The official doc very briefly talked about how to ignore files for your project, but there is not demo files, I did some research in their source code, and found the steps.

1. Create a file named `setting` in `wandb/`
2. Edit `setting`, both lines has to be exactly like this and for globs, each file should be comma separated, no extra space in between. e.g.
  

```
[default]
ignore_globs=*.npy,*pt 
```