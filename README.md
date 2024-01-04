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

## Aumenti di accuracy
Rete normale senza early stopping: 26,7%
Rete normale con early stopping basata su GL: 25,7%
Rete normale con data augmentation (random horizontal flip): 30% (verifica)
Rete con batch normalization e data augmentation (rhf): 52%
Rete con batch normalization e data augmentation (rhf) early stopping: 59%
