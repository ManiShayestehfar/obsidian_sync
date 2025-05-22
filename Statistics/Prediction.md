Suppose $X,Y$ are jointly distributed RVs (two measurements from the same experiment) and suppose we know $X=x$.
$$\textit{How can we use this to predict the value of Y?}$$

- Formally, given $X$, our predictor of $Y$ is $g(X)$, where $g:\mathbb{R}\to \mathbb{R}$ (measurable).  How to measure the quality of prediction? MSE is reasonable: $E[Y-g(x)]^2$ 