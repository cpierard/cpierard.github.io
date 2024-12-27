---
layout: post
title: "Bayesian inference of river plastics in the South Atlantic Ocean"
permalink: /projects/bayesian-plastic/
---

This work was published in Frontiers in Marine Science with a ["Attribution of Plastic Sources Using Bayesian Inference: Application to River-Sourced Floating Plastic in the South Atlantic Ocean (2022)"](https://doi.org/10.3389/fmars.2022.925437) by C.M. Pierard, D. Bassotto, F. Meirer and E. van Sebille. 

## Description

We developed a Bayesian inference framework to determine the probability that a piece of floating plastic found at sea came from a particular river by combining river emission data with Lagrangian simulations. The framework was tested in the South Atlantic Ocean, showcasing that particle age and location define the source probabilities.

### Plastic emitted from principal rivers (clustered)

<div style="display: flex; justify-content: space-between; align-items: center; margin: 20px 0;">
    <img src="/../assets/projects/bayesian/clusters.jpg" alt="First image description" style="width: 68%;">
    <img src="/../assets/projects/bayesian/priors.png" alt="Second image description" style="width: 28%;">
</div>

### Lagrangian Simulations of plastic from river deltas

<p align="center"><iframe width="90%" height="515" src="/../assets/projects/bayesian/realtime_sa-s06_3.mp4" frameborder="0" allowfullscreen></iframe></p>

###  Posterior probability that a piece of floating plastic found at sea came from a particular river
Click on the image to zoom in.

<style>
.image-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 16px;
    padding: 16px;
}

.grid-item {
    position: relative;
    width: 100%;
    padding-bottom: 100%;
    cursor: pointer;
}

.grid-item img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.modal {
    display: none;
    position: fixed;
    z-index: 1000;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.9);
}

.modal-content {
    margin: auto;
    display: block;
    width: 80%;
    max-width: 900px;
    max-height: 80vh;
    margin-top: 50px;
}

.close {
    position: absolute;
    right: 32px;
    top: 32px;
    color: white;
    font-size: 32px;
    font-weight: bold;
    cursor: pointer;
}
</style>

<div class="image-grid">
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Recife.png" alt="Recife" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Salvador.png" alt="Salvador" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Paraiba.png" alt="Paraiba" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Rio-de-Janeiro.png" alt="Rio de Janeiro" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Santos.png" alt="Santos" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Itajai.png" alt="Itajai" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Porto-Alegre.png" alt="Porto Alegre" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Rio-de-la-Plata.png" alt="Rio de la Plata" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Unclustered-America.png" alt="Unclustered America" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Cape-Town.png" alt="Cape Town" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Congo.png" alt="Congo" onclick="openModal(this.src)">
    </div>
    <div class="grid-item">
        <img src="/assets/projects/bayesian/posterior_contour_Unclustered-Africa.png" alt="Unclustered Africa" onclick="openModal(this.src)">
    </div>
</div>

<div id="imageModal" class="modal">
    <span class="close" onclick="closeModal()">&times;</span>
    <img class="modal-content" id="modalImage">
</div>

<script>
function openModal(imgSrc) {
    const modal = document.getElementById('imageModal');
    const modalImg = document.getElementById('modalImage');
    modal.style.display = "block";
    modalImg.src = imgSrc;
}

function closeModal() {
    document.getElementById('imageModal').style.display = "none";
}

window.onclick = function(event) {
    const modal = document.getElementById('imageModal');
    if (event.target == modal) {
        modal.style.display = "none";
    }
}
</script>