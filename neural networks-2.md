Who what when where and why

The quality of an ML model depends on the quality of the dataset, but also how well features encode the patterns in the data. Feature engineering extremely important for traditional machine learning methods, not so much with deep learning. Deep learning algorithms take in dataset, Learn its patterns, learn to represent the data, with features they extract on their own. Then combine different representations of the dataset each one identifying a specific pattern or characteristic of the dataset, into a more abstract high level representation of the dataset. This hands off process allows algorithms to adapt faster to dataset. 

Neural networks as they are today do not model the structure of the brain, but are inspired by it. Deep learning is not intended to replicate how the brain works, but instead enables systems that learn multiple levels of pattern composition. 
Before deep learnings' complex structures and widespread applications used today, there was the humble basic structure, the neuron, invented in the 1940s. 
<figure>
	<img src="https://miro.medium.com/max/1400/1*KAJBM4Fq-f96pibxNjusbA.png" height="150" width="600" >
	<figcaption>McCulloch and Pitts neuron Model, 1940s.</figcaption>
</figure>
Look familiar?

A decade later, the neuron model was extended creating an algorithm called the **[[Multilayer perceptron|perceptron]]**, able to _learn_ the weights in order to generate an output. **A single perceptron can only be applied to linear data. **. Originally used the sigmoid activation function but today RelU is more commonly used. 
<figure>
	<img src="https://miro.medium.com/max/1400/1*s2_hVuUCvV7-yWGTTpiM3A.png" height="150" width="600">
	<figcaption>Perceptron neuron model(left) activation function (right)</figcaption>
</figure>

Different kinds of modern neural networks
	- [[convolutional neural networks]]
	- [[multilayer perceptron]]