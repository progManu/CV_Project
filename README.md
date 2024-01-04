# Important Observations
## Kernel size considerations
Early layers with smaller kernel sizes (e.g., 3x3) capture local information such as edges and textures. As you move deeper into the network, larger kernel sizes (e.g., 5x5, 7x7) can help capture more global patterns and relationships. Hierarchical Feature Extraction:

The idea is to create a hierarchical representation of the input, where shallow layers focus on fine details, and deeper layers capture more abstract and global features. Reduction in Spatial Dimensions:

Larger kernels might be used in deeper layers where spatial dimensions have been significantly reduced through pooling or strides, allowing the network to still capture larger patterns effectively. Parameter Efficiency:

Using larger kernels in deeper layers allows the network to have a broader receptive field without an excessive increase in the number of parameters. Computational Efficiency:

Larger kernels can help reduce the spatial dimensions more quickly, which can be computationally efficient.

## Stopping criterion considerations
Abbiamo usato il paper Random stopping but when

Usato primo criterio perché vogliamo trovare una soluzione molto buona

Alpha troppo grande (7) => overfitting, accuracy non troppo elevata ma loss diminuisce, meglio tenere 2

## Optimizer considerations
Adam converge a risultati migliori (38%) in meno epochs (7) rispetto a sgd (20%, 18 epochs)

## Data augmentation considerations
Just flipping does not affect much the result.

Using the strong data aug, we obtain worst results because the network is not very expressive

## Initialization considerations

### Xavier Initialization
Xavier initialization, also known as Glorot initialization, is a widely used method for initializing the weights of neural network layers. It is named after Xavier Glorot, one of the researchers who proposed this initialization technique. Xavier initialization is designed to address the challenges of training deep neural networks by carefully selecting the initial values of weights to ensure a good balance between the input and output of each layer.

The initialization strategy for Xavier initialization is as follows:

For a layer with $$n^{in}$$ input units and $$n^{out}$$ output units, the weights are initialized by drawing random values from a distribution with mean 0 and variance $$\frac{2}{n_{in}+n_{out}}$$
This initialization is particularly effective when used with activation functions that have outputs in the range of -1 to 1, such as tanh. It helps prevent the vanishing or exploding gradient problems during training, which can be common in deep networks.

### He Initialization

 initialization technique designed to address the challenges of training deep neural networks with rectified linear units (ReLU) activations. This initialization method is also known as Kaiming initialization. ReLU is a popular activation function in deep neural networks

 The He initialization strategy for a layer with $$n_{in}$$ input units is to initialize the weights by drawing random values from a distribution with mean 0 and variance $$\frac{2}{n_in}$$

## Aumenti di accuracy

### SGD
- Rete normale senza early stopping: 26,7%
- Rete normale con early stopping basata su GL: 25,7%
- Rete normale con data augmentation (random horizontal flip): 30% (verifica)
- Rete con batch normalization e data augmentation (rhf): 52%
- Rete con batch normalization e data augmentation (rhf), early stopping (GL + momentum a 0.98): 59%
- Rete con batch normalization e dropout, data augmentation (rhf): 44,8%
- Rete con batch normalization e dropout, data augmentation (rhf), early stopping (GL + momentum a 0.92): 44,4%
- Rete con batch normalization e 2 dropout, data augmentation (rhf): 34,7%
- Rete con batch normalization e 2 dropout, data augmentation (rhf), early stopping (GL + momentum a 0.92): 37,8%
