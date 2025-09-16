# Denoising

## Introduction

- the [[Monte Carlo Integration]] of [[Path Tracing]] results in noisy images
- the mean energy of the image is correct 
	- but rare paths that hit a light source hold a lot of energy in one pixel, that is missing in the rest of the scene (firefly)
- goal is to not loose sharpness of the image (which would happen for simple blurs)
- noise is different for every pixel in generally in all frequencies
- denoising happens after the rendering process (a-posteriori methods)
- there are image space methods (Gaussian blur, Median filter, Bilateral filter, Wavelet denoising, Non-local means) and neural approaches ([[Machine Learning in Computer Graphics]])

## Median Filter

- fireflys do not get averaged out as they can be a factor 1000 brighter
- remove fireflys by not averaging over the neighborhood of the filter, but by taking the median
- always loses energy, even in the ideal case

## Bilateral Filter

- let the kernel shape depend on the image
$$BF(I_p) = \frac{1}{W_p}\sum_{q \in S}(G_{\sigma_s} (||p-q||))(G_{\sigma_r}|I_p-I_q|)I_q$$
- combines a positional weight with a range weight 
- but no multi-resolution analysis for different noise frequencies
- weighting depends heavily on the center pixel, which is noisy too

## Wavelet Analysis

- recursively blur the input image, take the difference (detail coefficients) and downsample the blurred input to yield coarse input to the next level
- also consider edges while blurring 
- detail coefficients mostly hold noise, so throw away
- solves multi-resolutional problems of bilateral filter but still depends on center pixel

## Neural Approaches

- <mark style="background: #FFB86CA6;">direct prediction</mark> - give the source image as input and directly get the denoised image as output
	- no control over the single pixel color
- <mark style="background: #FFB86CA6;">kernel prediction</mark> - let the network predict a kernel that can be applied to the image
	- allows for kernel normalisation to keep mean brightness and color
- both use [[Convolutional Neural Networks (CNN)]]
---

Origin: 
References: [[Path Tracing]]
Tags: 
Created: 15.09.2025

