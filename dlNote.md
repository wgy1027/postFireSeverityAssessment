### convolutional neural network:
The convolutional layers just include element wise multiplications and summations.

![](https://latex.codecogs.com/gif.latex?O=\frac{W-K+2P}{S}+1)

where ![](https://latex.codecogs.com/gif.latex?O) is the output height/length, ![](https://latex.codecogs.com/gif.latex?W) is the input height/length, ![](https://latex.codecogs.com/gif.latex?K) is the filter size, ![](https://latex.codecogs.com/gif.latex?P) is the padding, and ![](https://latex.codecogs.com/gif.latex?S) is the stride.

<span style="color:red">some *blue* text</span>

### Activation Layer
After each conv layer, it is convention to apply a activation layer immediately afterward in order to introduce nonlinearity to a system. The tanh and sigmoid are two conventionally used activation functions, but researchers found out that ReLU layers work far better thanks to its computational efficiency without the significant accuracy costwithout making a significant difference to the accuracy. The ReLU layer also helps to alleviate the vanishing gradient problem, which is the issue where the lower layers of the network train very slowly because the gradient decreases exponentially through the layers (See [here](https://en.wikipedia.org/wiki/Vanishing_gradient_problem) and [here](https://www.quora.com/What-is-the-vanishing-gradient-problem) for further information).
ReLU (Rectified Linear Units) Layers

The formulation of Noisy ReLU is as following:

![](https://latex.codecogs.com/gif.latex?f(x)=\max(0,x))

### Pooling Layer
Its function is to progressively reduce the spatial size of the representation to reduce the amount of parameters and computation in the network. Pooling layer operates on each feature map independently. The most common approach used in pooling is max pooling. Other options for pooling layers are average pooling and L2-norm pooling. The intuitive reasoning behind this layer is that once we know that a specific feature is in the original input volume, its exact location is not as important as its relative location to the other features. As you can imagine, this layer drastically reduces the spatial dimension (the length and the width change but not the depth) of the input volume. This serves two main purposes: (1) reducing the amount of parameters or weights and lessening the computation cost; (2) controlling the overfitting.

### Dropout Layer
This layer “drops out” a random set of activations in that layer by setting them to zero. It helps alleviate the overfitting problem. An important note is that this layer is only used during training, and not during test time.

### FC Layer
The FC is the fully connected layer of neurons at the end of CNN. Neurons in a fully connected layer have full connections to all activations in the previous layer.

### Shared Weight
Sharing weights in this way significantly reduces the number of weights we have to learn, making it easier to learn very deep architectures, and additionally allows us to learn features that are agnostic to what region of the input is being considered.

Consider a Convolutional Neural Network (CNN) for image classification. In order to detect local features, weight-sharing is used among units in the same convolutional layer. In such a network, the kernel weights are updated via the backpropagation algorithm.

An update for the kernel weight ![](https://latex.codecogs.com/gif.latex?h_j) in layer ![](https://latex.codecogs.com/gif.latex?l) would be as follows:

![](https://latex.codecogs.com/gif.latex?h_j^l=h_j^l-\eta\cdot\frac{\delta{R}}{\delta{h_j}^l}=h_j^l-\eta\cdot\frac{\delta{R}}{\delta{x_j}^{L}}\cdot\frac{\delta{x_j}^{L}}{\delta{x_j}^{L-1}}\cdot\dots\cdot\frac{\delta{x_j}^{l}}{\delta{h_j}^l})

## Transfer Learning
Transfer learning is the process of taking a pre-trained model (the weights and parameters of a network that has been trained on a large dataset by somebody else) and “fine-tuning” the model with your own dataset. The idea is that this pre-trained model will act as a feature extractor. You will remove the last layer of the network and replace it with your own classifier (depending on what your problem space is). You then freeze the weights of all the other layers and train the network normally (Freezing the layers means not changing the weights during gradient descent/optimization).

Let’s investigate why this works. Let’s say the pre-trained model that we’re talking about was trained on ImageNet (For those that aren’t familiar, ImageNet is a dataset that contains 14 million images with over 1,000 classes). When we think about the lower layers of the network, we know that they will detect features like edges and curves. Now, unless you have a very unique problem space and dataset, your network is going to need to detect curves and edges as well. Rather than training the whole network through a random initialization of weights, we can use the weights of the pre-trained model (and freeze them) and focus on the more important layers (ones that are higher up) for training. If your dataset is quite different than something like ImageNet, then you’d want to train more of your layers and freeze only a couple of the low layers.

## Image Processing
The task of image classification is the process of taking an input image and outputting a class number out of a set of categories.

The task of object localization is to taking an input image and produce a bounding box that describes where the object is in this image.

The task of object detection is to localize all of the objects in the image, that is, you will have multiple bounding boxes and multiple class labels.

The task of object segmentation is to output the class labels as well as an outline of every object in the input image.

## Data Augmentation Techniques
Approaches that alter the training data in ways that change the array representation while keeping the label the same are known as data augmentation techniques. They are a way to artificially expand your dataset. Some popular augmentations people use are grayscales, horizontal flips, vertical flips, random crops, color jitters, translations, rotations, and much more. By applying just a couple of these transformations to your training data, you can easily double or triple the number of training examples.
