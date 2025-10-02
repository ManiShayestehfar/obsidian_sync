
# Activation Function

>[!def] Activation function
>a one-variable non-linear function $f:\mathbb{C} \to \mathbb{C}$ differentiable except in a set of measure zero.
- Generally non-linear


# Neural Network

![[Basic-1759401890071.png]]


# Activation Output

![[Basic-1759402497994.png]]
![[Basic-1759402514653.png]]

# Network Function

![[Basic-1759402640913.png]]


# Group Change of Basis for NN

![[Neural Networks-1759403076941.png]]
![[Neural Networks-1759403087093.png]]
- $(\tau\cdot W, \tau \cdot f)$ is a neural network such that $\tau: (W,f) \to (\tau\cdot W,\tau\cdot f)$ is an isomorphism of neural networks.



# THEOREM

![[Neural Networks-1759403166918.png]]

*proof:* page 13. We essentially need to verify the behaviour of the activation output $\mathbf{a}$ on input->hidden, hidden->hidden, and hidden->output layers, as well as max-pooling.

**Implications:**
1. There are infinitely many neural networks with the same network function, independently of the architecture and the activation functions.
2. ReLU networks are positive scale invariant

![[Neural Networks-1759403729600.png]]



