## convolutional neural network:
The convolutional layers just include element wise multiplications and summations.

![](https://latex.codecogs.com/gif.latex?O=\frac{W-K+2P}{S}+1)

where ![](https://latex.codecogs.com/gif.latex?O) is the output height/length, ![](https://latex.codecogs.com/gif.latex?W) is the input height/length, ![](https://latex.codecogs.com/gif.latex?K) is the filter size, ![](https://latex.codecogs.com/gif.latex?P) is the padding, and ![](https://latex.codecogs.com/gif.latex?S) is the stride.

## Activation Layer
After each conv layer, it is convention to apply a activation layer immediately afterward in order to introduce nonlinearity to a system. The tanh and sigmoid are two conventionally used activation functions, but researchers found out that ReLU layers work far better thanks to its computational efficiency without the significant accuracy costwithout making a significant difference to the accuracy. The ReLU layer also helps to alleviate the vanishing gradient problem, which is the issue where the lower layers of the network train very slowly because the gradient decreases exponentially through the layers (See [here](https://en.wikipedia.org/wiki/Vanishing_gradient_problem) and [here](https://www.quora.com/What-is-the-vanishing-gradient-problem) for further information).
ReLU (Rectified Linear Units) Layers

The formulation of Noisy ReLU is as following:

![](https://latex.codecogs.com/gif.latex?f(x)=\max(0,x))

## Pooling Layer
Its function is to progressively reduce the spatial size of the representation to reduce the amount of parameters and computation in the network. Pooling layer operates on each feature map independently. The most common approach used in pooling is max pooling.

