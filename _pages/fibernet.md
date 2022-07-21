---
layout: archive
title: Physics-informed neural networks to learn cardiac fiber orientation from multiple electroanatomical maps
permalink: /research/fibernet.html
author_profile: false
---

<!-- Author: Thomas Grandits -->
Carlos Ruiz Herrera\*, Thomas Grandits\*, Gernot Plank, Paris Perdikaris, Francisco Sahli Costabal, Simone Pezzuto

{::nomarkdown}
<style type="text/css" scoped>
    /*.author-footnotes*/
    .paper-links{
        margin: auto;
        width: 35%;
        text-align:center;
        margin-bottom: 10px;
        margin-top: 10px;
    }

    .paper-links img{
        width: 15%;
        margin-left: 15px;
        margin-right: 15px;
    }

    .author-teaser-container{
        margin: auto;
        width: 70%;
        text-align:center;
        margin-bottom: 10px;
        margin-top: 10px;
    }

    .author-teaser-img{
        width: 11.5%;
        border-radius: 50%;
        margin-left: 10px;
        margin-right: 10px;
    }

    .author-footnote{
        width: 95%;
        margin: auto;
        text-align: left;
        font-style: italic;
        font-size: 10pt;
    }

    code{
        font-size: 10pt;
        white-space : pre-wrap !important;
    }
</style>

<div class="author-teaser-container">
<img class="author-teaser-img" src="https://fsahli.github.io/images/fibernet/people/carlos_herrera.jpg"/>
<a href="https://www.researchgate.net/profile/Thomas-Grandits"><img class="author-teaser-img" src="https://fsahli.github.io/images/fibernet/people/Thomas-Grandits.jpg"/> </a>
<a href="https://ccl.medunigraz.at/people.html"><img class="author-teaser-img" src="https://iheart.polimi.it/wp-content/uploads/2019/09/plank-203x200.jpg"/> </a>
<a href="https://www.amcs.upenn.edu/people/paris-perdikaris"><img class="author-teaser-img" src="https://directory.seas.upenn.edu/wp-content/uploads/2020/03/perdikaris-paris.jpg"/> </a>
<a href="https://github.com/fsahli"><img class="author-teaser-img" src="https://fsahli.github.io/images/FS.jpg" /> </a>
<a href="https://github.com/pezzus"><img class="author-teaser-img" src="https://avatars.githubusercontent.com/u/5204404?v=4"/> </a>
</div>

<div class="paper-links">
<a href="https://arxiv.org/abs/2201.12362"><img style="width: 20%" src="/images/fibernet/arxiv-logo.png"/></a>
<a href="https://github.com/fsahli/FiberNet"><img src="/images/fibernet/github_logo_small.svg"/></a>
</div>

<div class="author-footnote">
*Equal contribution
</div>

{:/}

# Motivation

In recent years, the future vision of precision cardiology through digital twinning has gained traction. 
In such scenarios, a digital replica of a patient’s heart is generated from a variety of measurements in the clinic.
The fiber distribution in the heart is a key determinant of the cardiac function and, as such, it has a prominent role in digital twinning.
We utilize the fact that the electrical stimulus activating the myocardium travels at different speeds, depending on whether the propagation occurs along or across the fibers.

We propose FiberNet, a PINN-based method to solve the inverse problem of identifying fibers in the heart from electroanatomical maps. 
This is achieved by simultaneously fitting multiple neural networks to multiple electroanatomical maps, while using a common network that predicts the conduction velocity tensor at different locations.

![Intro](/images/fibernet/FiberNet_intro.svg)

FiberNet translates a set of electroanatomical maps into a continuous estimate of the fiber field and conduction velocity. 
These estimates can be used for simulating cardiac activation in a predictive model based on the eikonal equation. 
Internally, FiberNet uses physics-informed neural networks to constrain the parameter space during the training phase.

# Method

![schematic](/images/fibernet/schematic.svg)

We use multiple neural networks to represent each of the activation times received for training. 
We use one neural network to represent the conduction velocity tensor. 
From here, we can compute the fiber orientation. 
We train all the networks simultaneously to satisfy the data from the activation time maps and the Eikonal equation, which links activation times to conduction velocities.

# Video Demo

The following video shows how FiberNet "learns" three activations and an underlying fiber field from sparse surface observations.

<video width="100%" controls>
<source src="/images/fibernet/anim_fibernet_v4.mp4" type="video/mp4">
</video>

# Reference

If you find this work helpful in your research, please consider citing our work
```bibtex
@article{herrera_physics-informed_2022,
    title = {Physics-informed neural networks to learn cardiac fiber orientation from multiple electroanatomical maps},
journal = {Engineering with Computers},
    author = {Ruiz Herrera, Carlos and Grandits, Thomas and Plank, Gernot and Perdikaris, Paris and Sahli Costabal, Francisco and Pezzuto, Simone},
    year = {2022},
    eprinttype  = {arxiv},
    eprint = {2201.12362},
doi = {10.1007/s00366-022-01709-3},
}
```

# Example Usage

The [repository](https://github.com/fsahli/FiberNet) contains several examples of how to use FiberNet:
<iframe src="/images/fibernet/3D_example.html" width="100%" height="1024" allowfullscreen="" frameborder="0">
</iframe>
