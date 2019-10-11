---
layout: post
title:  "2D Simulation of Convection in a Stratified Fluid"
permalink: /projects/convection/
youtubeId: mP6my1nAQlo
---

The objective of the project was to study the effect of convection in an stratified fluid, trying to simulate the convetion proocesses in the atmospheric boundary layer under a thermal inversion. For this, we performed a simulation using [Dedalus](http://dedalus-project.org/), which is a Python framework used for solving PDEs using spectral methods.


The simulation is based in a laboratory experiment in which convection was generated in a fluid with an stratification set using salinity gradients.

### Variables and Equations



### Boundary conditions

The boundary conditions used in the model are determined by the method by which we solve the equations. In this case, we are using spectral methods, so our basis must be Fourier series or Chebychev series. In our case, we defined a Fourier basis for the x direction and a Chebychev basis for the y direction. which implies that we had periodic boundaries in left and right sides of the domain, and fixed boundaries in the top and bottom of the domain. In particular, the boundary conditions for the top and bottom are shown in the following tables:

| Variable | Top | Bottom |
|----------|-----|--------|
| u | 0 | 0 |
| v | 0 | 0 |
| P |  |  |
| T | 20 | 28 |
| S | | |

### Initial conditions

### Results

_This work was part of my batchelor's internship done at the Laboratory of Geophysical Fluid Dynamics_.


![Temp](/../assets/projects/convection/ugm_28_T.png)

![NN](/../assets/projects/convection/ugm_28_NN.png)

### Animation
![](/../assets/projects/convection/full.gif)

You can find the video in Youtube in the following [link](https://www.youtube.com/watch?v=mP6my1nAQlo).

### References
