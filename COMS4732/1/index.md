<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
  });
</script>
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

# COMS 4732 Project 1: Images of the Russian Empire: Colorizing the [Prokudin-Gorskii](https://www.loc.gov/collections/prokudin-gorskii/) photo collection

## Introduction 

The Prokudin-Gorskii photo collection is a historical archive containing more than 10,000 glass plate images captured between 1908 and 1915 by Russian photographer Sergei Mikhailovich Prokudin-Gorskii. These photographs offer a rare view into the daily life, architecture, and landscapes of the Russian Empire during a time of profound political and social transformation. The Library of Congress digitized the negatives of these glass plates and made them available to the public. In this project, we use image plates selected from the Prokudin-Gorskii collection to experiment with image processing techniques.

## Method

### Simple Alignment

The naive approach iterates over all possible displacements in both x and y directions within a window of 15 pixels. Fixing one channel as a reference, we move the other channels and evaluate the alignment score at each step. There are two metrics we use: L2 Euclidean distance and normalized cross-correlation (NCC).

1. **L2 Norm (Sum of Squared Differences)** is defined as:

$$
   \text{L2 Norm} = \sum \sum \left( (\text{image1} - \text{image2})^2 \right)
$$

2. **Normalized Cross-Correlation (NCC)** is defined as:

$$
   \text{NCC} = \frac{\text{image1}}{||\text{image1}||} \cdot \frac{\text{image2}}{||\text{image2}||}
$$

For the L2 norm, we simply compute the sum of squared differences between pixels of the base image and the shifted image. A lower L2 norm indicates better matching.

For NCC, we treat each image as a vector. We take the zero-centered, normalized vectors and compute their dot product. NCC performs consistently better in my experiments.

### Multi-Resolution Pyramid Alignment
The pyramid search algorithm recursively scales down the image by half and performs naive alignment on the scaled images to improve efficiency and handle larger displacements. 

## Implementation
### Simple Alignment
In our implementation, we fix the blue image as the base plane and shift the green and red images. For simple alignment, I implemented a function named `find_displacement_naive(image_1, image_2, window_size=15, NCC=False)`  which exhaustively computes the score for all combinations of displacements. The final displacement is chosen by minimizing the L2 distance or maximizing the NCC score. NCC performs consistently better than L2 distance in my experiments. 

### Multi-Resolution Pyramid Alignment 
For pyramid alignment, I implemented the `find_displacement_pyramid` function on top of `find_displacement_naive`, which reduced runtime and enhanced performance for high-resolution images. I found that using NCC further improved the results. The challenge was determining the optimal number of pyramid layers. Setting a fixed number of layers is not ideal because different image sizes require different depths. Therefore, I ensured that the smallest image had at least 16 to 32 pixels and calculated the number of layers using a logarithmic function. We precompute the images for all pyramid levels and iteratively refine the displacement from the coarsest level to the finest.

I also experimented with dynamically adjusting the window size as the scaling factor increased, but this resulted in longer runtimes without noticeable performance improvements. To balance runtime and accuracy, I chose a constant window size (e.g., 2 pixels for refinement levels) as the optimal value.

#### Bell & Whistle
To make the image look more natural, I employed two additional techniques: gradient detection and cropping. The Sobel gradient functions as an edge detection filter. It highlights areas of the image where intensity changes significantly. This feature improves alignment accuracy by focusing on elements that are more structural significant. Also, image borders typically do not contribute to the alignment process, so cropping the outer borders helps eliminate noise that may be inconsistent with the main image content.

## Result
### Simple Alignment
#### Cathedral
![Cathedral](media/cathedral.jpg)
Displacement G: (1, -1), R: (7, -1)

#### Monastery
![Monastery](media/monastery.jpg)
Displacement G: (-3, 0), R: (3, 1)

#### Tobolsk
![Tobolsk](media/tobolsk.jpg)
Displacement G: (3, 3), R: (6, 3)


### Multi-Resolution Pyramid Alignment 
#### Church
![Church](media/Church.jpg)
Displacement G: (25, 4), R: (58, -4)

#### Emir
![Emir](media/Emir.jpg)
Displacement G: (49, 24), R: (107, 40)

#### Harvesters
![Harvesters](media/Harvesters.jpg)
Displacement G: (60, 17), R: (124, 14)

#### Icon
![Icon](media/Icon.jpg)
Displacement G: (42, 17), R: (90, 23)

#### Italil
![Italil](media/Italil.jpg)
Displacement G: (38, 22), R: (77, 36)

#### Lastochikino
![Lastochikino](media/Lastochikino.jpg)
Displacement G: (-3, -2), R: (76, -8)

#### Lugano
![Lugano](media/Lugano.jpg)
Displacement G: (41, -17), R: (92, -29)

#### Melons
![Melons](media/Melons.jpg)
Displacement G: (80, 10), R: (177, 13)

#### Self_portrait
![Self_portrait](media/Self_portrait.jpg)
Displacement G: (78, 29), R: (176, 37)

#### Siren
![Siren](media/Siren.jpg)
Displacement G: (49, -6), R: (96, -24)

#### Three_generations
![Three_generations](media/Three_generations.jpg)
Displacement G: (54, 12), R: (111, 9)


### Below are the images I selected from the collection.
#### Pole 
![Pole](media/Pole.jpg)
Displacement G: (57, -5), R: (125, -24)

#### Sitting_man 
![Sitting_man](media/Sitting_man.jpg)
Displacement G: (31, 21), R: (91, 24)

#### Mosque 
![Mosque](media/Mosque.jpg)
Displacement G: (56, 34), R: (125, 60)
