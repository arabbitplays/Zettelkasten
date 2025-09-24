# Image Difference Metrics

## Introduction

- The goal is to measure the (visible) differences between two images
- often used to measure the difference of a rendering algorithm ([[Monte Carlo Integration]]) to a reference image

## Root Mean Square Error (RMSE)

- take the squared difference for each pixel, calculate the mean and take the root
$$\sqrt{\frac{1}{N}\sum_i^N (a_i - b_i)²}$$
- the MSE includes the (squared) bias and the variance of the images
- <mark style="background: #FF5582A6;">dominated by the big differences</mark>

## Relative RMSE (rRMSE)

- divide out the brightness of the reference pixel
	- make it not symmetric, because the reference is divided out, not the noisy pixel
- still dominated by big differences though the L2 difference

## Symmetric mean absolute percentage error (SMAPE)

$$SMAPE(x,y) = \frac{|x-y|}{|x|+|y|+\epsilon}$$
- the L1 difference tames the domination of outliers
- is symmetric again
- still doesn't tell the whole story as brightness normalisation is not the only feature of the [[Human Visual System (HVS)]]

## FLIP

- Perceptual based metric -> measure the to the [[Human Visual System (HVS) | HVS]] visible difference, not the numerical 
- uses a perceptually uniform [[Color Spaces | Color Space]] and corrects for several perception effects
	- receptive fields, contrast sensitivity, Hunt effect, ...

![[Pasted image 20250919125432.png]]
1. Linearise color from sRGB if need
2. split into a chromacity and a luminance pipeline
	- color error checks for difference in hue and saturation, corrected from the Hunt effect
	- feature error checks for points and edges
3. combine the errors to the final error map

- the color pipeline
	- spatial filtering with the contrast sensitivity functions in opponent space
		- they are low pass filter in the frequency domain, so they can be approximated with a Gauss kernel
	- compare images in perceptual uniform colorspace
	- adjust for Hunt effect by scaling the chromacity components by the luminance
- the feature pipeline
	- use difference of gaussian convolution to calculate the partial derivatives
- backed by real experimental data regarding the color space and the error metric itself
- <mark style="background: #BBFABBA6;">current state of the art</mark>

---

Origin: CG2 Lecture, FLIP: https://research.nvidia.com/publication/flip
References: [[Monte Carlo Integration]], [[Human Visual System (HVS)]]
Tags: 
Created: 03.06.2025

