# Frustum Culling

## Introduction

Frustum culling is a technique used to reduce the rendered triangle count, by removing triangles or meshes not seen by the camera.

## Extracting the Frustum Planes

- Given a matrix $M$, a point $v$ is on the inside of the frustum if these 6 inequalities are fulfilled
$$left: 0 <v \cdot (row_4 + row_1)$$
$$right: 0 <v \cdot (row_4 - row_1)$$$$bottom: 0 <v \cdot (row_4 + row_2)$$$$top: 0 <v \cdot (row_4 - row_2)$$$$near: 0 <v \cdot (row_4 + row_3)$$$$far: 0 <v \cdot (row_4 - row_3)$$
- if $M$ is equal to the projection matrix, the planes are in view space
- if $M$ is equal to the model-view-projection matrix, then the planes are in model space
- <mark style="background: #D2B3FFA6;">the point v has to be in the same space a the extracted planes</mark>

---

Origin: Fast Extraction of Viewing Frustum Planes from the WorldView-Projection Matrix by Gil Gribb ( ggribb@ravensoft.com ) Klaus Hartmann
References: [[Culling]]
Tags: 
Created: 14.05.2025

