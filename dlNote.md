## convolutional neural networks:
The convolutional layers just include element wise multiplications and summations.

![](https://latex.codecogs.com/gif.latex?O=\frac{W-K+2P}{S}+1)

where ![](https://latex.codecogs.com/gif.latex?O) is the output height/length, ![](https://latex.codecogs.com/gif.latex?W) is the input height/length, ![](https://latex.codecogs.com/gif.latex?K) is the filter size, ![](https://latex.codecogs.com/gif.latex?P) is the padding, and ![](https://latex.codecogs.com/gif.latex?S) is the stride.

## Activation Layers
After each conv layer, it is convention to apply a activation layer immediately afterward in order to introduce nonlinearity to a system. The tanh and sigmoid are two conventionally used activation functions, but researchers found out that ReLU layers work far better thanks to its computational efficiency without the significant accuracy costwithout making a significant difference to the accuracy. The ReLU layer also helps to alleviate the vanishing gradient problem, which is the issue where the lower layers of the network train very slowly because the gradient decreases exponentially through the layers (See [here](https://en.wikipedia.org/wiki/Vanishing_gradient_problem) and here for further information).
ReLU (Rectified Linear Units) Layers

