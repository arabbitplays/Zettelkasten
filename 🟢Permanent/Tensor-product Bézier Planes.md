# Tensor-product Bézier Planes

- given two bases to represent curves in $\mathbb{R}^d$ for example [[Bézier Curves]]
	$$F(u)=\sum_i B_i^n(u)c_i\ and\ G(v)=\sum_j B_j^m d_j$$
- The plane is then defined as
$$S(u,v) = \sum_i \sum_j B_i^n(u) B_j^m(v) b_{i,j}$$
- It can be seen as a Bézier curve of Bézier curves with $S(u,v) = \sum_i B_i^n(u) (\sum_j  B_j^m(v) b_{i,j}) = \sum_i B_i^n c_j(u)$
- The is a two dimensional version of the [[Bézier Curves#de Casteljau-Algorithmus | De Casteljau Algorithm]]

---

Origin: Computergrafik I
References: [[Bézier Curves]]
Tags: 
Created: 28.01.2025

