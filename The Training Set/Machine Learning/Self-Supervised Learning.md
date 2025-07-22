**Transfer Learning** is a technique where a backbone of a network that is trained on a specific task is re-used for another but related task to enable better convergence of loss.
There is a caveat of this that once the new task is trained, the new model objectively tends to perform poorly on the original dataset, this term is called **catastrophic forgetting**. Don't know what is so catastrophic about it , as it is very intuitive that a new training on completely different dataset will rewrite the weights to fit the new dataset but hey we have a new keyword :beer: 

**Self-supervised Learning** is a similar concept but instead of labels, we ask it to generate its own labels from the data structure by using a *pretext-task*. Example: [Dino V2](https://arxiv.org/abs/2304.07193) 

![[Pasted image 20250710150352.png]]

*Pretext Tasks* for example can be masked inputs , like masked words and the network learns to predict the masked word or patches of images are masked and the network learns to fill-in-the-blanks.
