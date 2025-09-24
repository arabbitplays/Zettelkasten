# Animation

## Introduction

- how to move 3D geometry over time -> Keyframes
	- draw most important poses, and fill in the rest through interpolation
	- everything can be keyframed: position, rotation (use [[Quaternions]]), scale, ...
	- see [[Bézier Curves#Use in animation]] for more

## Facial animation

- define a set of target shapes 
![[Pasted image 20250916101515.png]]
- interpolate the targets by weights $w$
	- shapes define a high dimensional hypercube with the neutral face as the origin
- problems:
	- result regresses to the mean if multiple weights are active
	- the blendshapes must be sculpted somehow -> matching to footage of live actors
	- scattered data interpolation would be better the the hypercube structure, so new data points could be added where needed
- define a set of markers on the face -> solve for the rest of the face given the marker positions

---

Origin: 
References: [[Bézier Curves]], [[Rendering Index]]
Tags: 
Created: 15.09.2025

