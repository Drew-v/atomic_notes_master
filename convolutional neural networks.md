## What is a convolutional neural network? 

![CNN diagram](https://miro.medium.com/max/2000/1*vkQ0hXDaQv57sALXAJquxA.jpeg)

[A comprehensive guide](https://towardsdatascience.com/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way-3bd2b1164a53) ** A convolutional neural network is used to classify images**, by assigning importance to image features (learnable weights and biases), to aspects/objects in the image and differentiate one from another. Little preprocessing is needed (filters). Conv nets with enough training, can learn filters and characteristics, instead of being manually coded. 

** Why not [[Feed Forward Networks]]? ** Because FFNs cannot identify complex relationships between image features (pixel dependencies). ** ConvNets capture spatial and temporal dependencies in an image ** through application fo filters. Better fitting through reduction of params and reusablity of weights. 

** ConvNets reduce large image resolution to a scalable level **, to process large training datasets. 

- Image input -> [[Convolution Layer]] (Kernal) -> Convolved Feature

- Convolved Feature -> [[Pooling Layer]] -> Convolved feature (reduced dimensionality, denoising)

**Cycle repeats as needed**

**The [[Convolutional Layer]] together with the [[Pooling Layer]] form the i-th layer of a convolutional neural network. ** Layers may be increased depending on complexity needs of algorithm, but this increases computational power needs. 

After these layer processing steps, the model can now understand the features, the final output is flattened and fed to a regular neural network for classification purposes.
<img src="https://miro.medium.com/max/1400/1*kToStLowjokojIQ7pY2ynQ.jpeg">
Convolution layer + pooling layer -> flattened -> [[fully connected layer]] (RelU)-> softmax layer
The [[fully connected layer]] cheaply learns Non-linear combinations of the high level features from convolutional layers.  


Somewhere between th fully connected layer and software=max, there is a feed forward neural network to distinguish features in images and classify them using softmax technique 

Here are some important ConvNets:
- [[LeNet]]
- [[AlexNet]]
- [[VGGNet]]
- [[GoogLeNet]]
- [[ResNet]]
- [[ZFNet]]