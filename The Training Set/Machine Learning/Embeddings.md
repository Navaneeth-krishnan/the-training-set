What are the difference between: Vector Embeddings, Latent Vectors and Representation

**Embeddings** encode higher dimensional data into lower dimensional vectors
![[Pasted image 20250710143045.png]]
 Sometimes we could encode sparse one-hot encoding into a dense embedding vector. 
 Every layer of a CNN can be considered an embedding vector. But lower the dimension of the embedding, better space saving i guess?
However, the second to last layer of the CNN is considered to be the embedding vector of the input image.

Embeddings can also be higher than the dimension of the input data because the main job of the embedding vector is to calculate similarity with the context of semantics.
![[Pasted image 20250710143138.png]]

To appear like a math-head:

> [!NOTE] Mathematically Embedding
> an embedding is an injective and structure-preserving map between an input space _X_ and the embedding space _Y_. This implies that similar inputs will be located at points in close proximity within the embedding space, which can be seen as the “structure-preserving” characteristic of the embedding

**Latent Space** is usually confused with embedding. But similar inputs need not necessarily have similar latent space representations.
![[Pasted image 20250710143201.png]]
The bottleneck is the latent space.

**Representation** is a term used to describe an intermediate state of the input data through a neural network. Embeddings and latent space are examples of useful representations

1-1. Suppose we’re training a convolutional network with five convolutional layers followed by three fully connected (FC) layers, similar to AlexNet ([https://en.wikipedia.org/wiki/AlexNet](https://en.wikipedia.org/wiki/AlexNet)), as illustrated in Figure

![image](https://sebastianraschka.com/images/books/ml-q-and-ai/ch01-fig04.png)

We can think of these fully connected layers as two hidden layers and an output layer in a multilayer perceptron. Which of the neural network layers can be utilized to produce useful embeddings? Interested readers can find more details about the AlexNet architecture and implementation in the original publication by Alex Krizhevsky, Ilya Sutskever, and Geoffrey Hinton.

1-2. Name some types of input representations that are not embeddings.