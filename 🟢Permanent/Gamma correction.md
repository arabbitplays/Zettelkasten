# Gamma correction


## Transfer functions

- Maps the values from the frame buffer (pixel values $p$) to the possible brightness values of the screen
- Usually own transfer function per color channel
- Dependent on desired display characteristics
- Dependent on physical properties of the screen
- Limited by the maximum and minimum brightness of the display
- And ambient light reflected by the screen $k$
- <mark style="background: #FFB86CA6;">dynamic range</mark> indicates the possible contrast
$$R_d = \frac{I_{max} + k}{I_{min} + k}$$

## Transfer functions and perception

What does the ideal transfer function look like?

Colors should not produce visible brightness levels
- People only perceive a difference in brightness of 1-2% (<mark style="background: #FFB86CA6;">Just noticable difference (JND)</mark>)
- Depending on the background brightness $L$, <mark style="background: #D2B3FFA6;">absolutely smaller steps in the dark</mark>
$$\frac{L_{LND}}{L} = const = 1\%$$
The following should therefore apply for an ideal transfer function:
$$p \mapsto 1.02^{p-1}\ I_{min}$$
$$I(p) \propto p^\gamma$$
Due to the interaction of screen, software, GPU, etc. gamma is not too easy to determine
## Gamma correction

For storage and display, $I \propto p^\gamma$ is ideal, as the bits are utilized according to the perception.
However, the calculation of images should take place in linear space (the sum of two light sources should be twice the s

---

Origin: Computergrafik I
References: 
Tags: 
Created: 24.10.2024

