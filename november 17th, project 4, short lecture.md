Image neural network processing

GANs, one shrinks image, other reconstructs it from compressed image. 


__[[convolutional neural networks]] are often used for image processing__
Conv nets have this idea of sharing weights, to reduce the number of params which need to be optimized in the NN

these weights are reduced through the use of the kernal, which only has as many weights as it's WxH

Each layer in convolutional NN have different weights for each filter
![[PNG image.png]]

Abstraction created in convolutional layer, examples would be one layer extracts out the horizontal lines of image, another the vertical, another edges, etc.

Pooling layers increase the rate at which an image is shrunk as input moves through CNN. This layer is not learning a specific transformation of the data like a conv layer, but instead is shrinking and denoising. Max pooling preservers variance in image. Average pooling does not. 

Pooling has fallen out of favor? Because of information loss?
Enter [[strident convolution]], which involves moving kernal more than one pixel at a time. Basically setting stride > 1. This benefits in less parameters and acts as a regularizer, reduces overfitting, improves generalization. 

Classification vs localization:
Classify object type, localization: determine where object is in image

Point being: object detection is expansion of localization

Semantic segmentation: classify every pixel in an input image as belonging to a specific class. 

Instance segmentation: segments instances of objects in classes

![[CONV_image_algorithms 1.png]]
