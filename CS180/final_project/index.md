<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
  });
</script>
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

# CS 180 Final Projects

# Gradient Domain Fusion

## Part 1 - Toy Problem

<p align="center">
  <img src="media/eq0.png" alt="Image description">
</p>


<div style="display: flex; justify-content: center; align-items: center; gap: 20px;">
    <figure>
        <img src="media/1.0.png" alt="Image description" style="width: 300px; height: auto;">
        <figcaption style="text-align: center;">Original Image</figcaption>
    </figure>
    <figure>
        <img src="media/1.1.png" alt="Reconstructed Image" style="width: 300px; height: auto;">
        <figcaption style="text-align: center;">Reconstructed Image</figcaption>
    </figure>
</div>


## Part 2 - Poisson Blending

<p align="center">
  <img src="media/eq1.jpg" alt="Image description">
</p>


<div style="display: flex; justify-content: center; align-items: center; gap: 20px;">
    <figure>
        <img src="media/2.2.jpeg" alt="Image description" style="width: 300px; height: auto;">
        <figcaption style="text-align: center;">Penguin</figcaption>
    </figure>
    <figure>
        <img src="media/2.1.JPG" alt="Penguin Chick Image" style="width: 300px; height: auto;">
        <figcaption style="text-align: center;">Background</figcaption>
    </figure>
</div>


<div style="display: flex; justify-content: center; align-items: center; gap: 0px;">
    <figure>
        <img src="media/1.3.1.jpg" alt="Image description" style="width: auto; height: auto;">
        <figcaption style="text-align: center;">Mask</figcaption>
    </figure>
    <figure>
        <img src="media/1.3.0.jpg" alt="Penguin Chick Image" style="width: auto; height: auto;">
        <figcaption style="text-align: center;">Unblended</figcaption>
    </figure>
    <figure>
        <img src="media/1.2.png" alt="Penguin Chick Image" style="width: auto; height: auto;">
        <figcaption style="text-align: center;">Poisson Blended</figcaption>
    </figure>
</div>


## Bells & Whistles - Mixed Gradients 

<p align="center">
  <img src="media/eq2.jpg" alt="Image description">
</p>

<div style="display: flex; justify-content: center; align-items: center; gap: 5px;">
    <figure>
        <img src="media/3.1.jpg" alt="Image description" style="width: 300px; height: auto;">
        <figcaption style="text-align: center;">Penguin</figcaption>
    </figure>
    <figure>
        <img src="media/3.2.jpg" alt="Penguin Chick Image" style="width: 500px; height: auto;">
        <figcaption style="text-align: center;">Background</figcaption>
    </figure>
</div>


<div style="display: flex; justify-content: center; align-items: center; gap: 0px;">
    <figure>
        <img src="media/1.6.jpg" alt="Image description" style="width: 500px; height: auto;">
        <figcaption style="text-align: center;">Mask</figcaption>
    </figure>
    <figure>
        <img src="media/1.5.jpg" alt="Penguin Chick Image" style="width: 500px; height: auto;">
        <figcaption style="text-align: center;">Unblended</figcaption>
    </figure>
    <figure>
        <img src="media/1.4.png" alt="Penguin Chick Image" style="width: 500px; height: auto;">
        <figcaption style="text-align: center;">Mixed Blended</figcaption>
    </figure>
</div>


