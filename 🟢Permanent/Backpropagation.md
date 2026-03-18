---
date created: 20.11.2023 15:55
date modified: 13.08.2024 15:13
---
# Backpropagation

- part of the learning algorithm of [[Neural Networks]]

- Let $a^j$ be the activation of the jth layer, $\Theta^j$ the weights of the jth layer, and $J$ the loss function
- To update the weights, we have $\Theta^j \rightarrow \Theta^j - \alpha \frac{\partial J}{\partial \Theta^j}$, where, for example, $\frac{\partial J}{\partial \Theta^2} = \frac{\partial J}{\partial a^2} \frac{\partial a^2}{\partial \Theta^2}$ and  $\frac{\partial J}{\partial \ Theta^1} = \frac{\partial J}{\partial a^2} \frac{\partial a^2}{\partial a^1} \frac{\partial a^1}{\partial \Theta^1} = \frac{\partial J}{\partial \Theta^2} \frac{\partial a^1}{\partial \Theta^1}$
- So start at the nth level and always store $\frac{\partial J}{\partial \Theta^j}$ to calculate $\frac{\partial J}{\partial \Theta^{j-1}}$
- Use <mark style="background: #FFB86CA6;">Computational Graph</mark>
	- ![[Pasted image 20231120155842.png | 400]]
    - ![[Pasted image 20231120160055.png |400]]
	- To compute $\nabla_{w^1} L$, trace the path backward to $\nabla_{w^1} L = \frac{\partial L}{\partial L^1} \nabla_{w^1} L^1 + \frac{\partial L}{\partial L^2} \nabla_{w^1} L^2 = \dots$

---

Origin: ML I lecture
References: [[Gradient Descent]]
Tags: 
Created: 16.03.2026
