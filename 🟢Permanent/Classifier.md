# Classifier 


- Classify data into multiple classes.
- Data of the form $D=\{(x_i,c_i)\}$, where $c$ is the label for the correct class.
- Train a function $f$ that minimizes the number of misclassified points
- This can also be achieved using [[Neural Networks]] with a softmax function in the final layer

## Linear Classification

- Find a line $f(x) = w^\top x + b$ that divides the data
    - ![[Pasted image 20231106172741.png | 300]]

- Possible loss functions:
	- A step function as the loss function is NP-hard
    - A loss function like the one used in [[Bachelor/5th Semester/GKI/Machine Learning/Supervised Learning/Regression|Regression]] is susceptible to outliers, since labels are discrete but the function output is continuous
	- Use the sigmoid function $\sigma(a) = \frac{1}{1+e^{-a}}$ in the loss function
        - ![[Pasted image 20231106170543.png |300]]
$$L(w)=\sum (\sigma ( f(x_i))-c_i)^2$$

- Consider $\sigma(f(x))$ as a probability function with
    - $p(c=1|x) = \sigma(w^\top x +b)$
	- $p(c=0|x) = 1-\sigma(w^\top x +b)$
    - Combine using the exponent trick to
$$p(c | x) = p(c=1|x)^cp(c=0|x)^{1-c}$$

- Optimize the likelihood function using the [[Estimator#Maximum-Likelihood-Estimator]]:
$$argmax_w\ log\ lik(w, D) = \sum_i log\ p(c_i|x_i)$$
$$= argmax_w\ \sum_i(c_i\ log\ p(c=1|x) + (1-c_i)\ log\ p(c=0|x_i)$$
$$= argmax_w\ \sum_i(c_i\ log\ \sigma(w^\top x_i) + (1-c_i)\ log\ (1-\sigma(w^\top x_i))$$
- Function no longer has an analytical solution -> use [[Gradient Descent]]
## Generalized Classification
- Use functions on the features to make the input space linearly separable
    - ![[Pasted image 20231106171419.png | 400]]
	- For example, instead of the features themselves, use $\Phi(x_1, x_2) = x_1^2 + x_2^2$ as the distance from the center
$$argmax_w\ \sum_i(c_i\ log\ \sigma(w^\top \Phi(x_i)) + (1-c_i)\ log\ (1-\sigma(w^\top \Phi(x_i)))$$

---

Origin: ML I lecture
References: [[Machine Learning Index]]
Tags: 
Created: 06.11.2023
