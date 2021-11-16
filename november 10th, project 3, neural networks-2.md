## Project 3 notes
Use min max scaler to train, save it, then unscale predictions before submission
May have to write custom loss function with this method. This has gotten performance of .15 score

No feature engineering or dimensional reduction 
Prof wants scores below .2 for good grade

This is extra step, not expected byb prof but may improve score:
	Book 3rd party libraries to automate hyperparameter tuning? Tensorflow also has  automated param tuning. 

Note to self: batch normalization may prove highly effective on this project, may replace min max scaler.

Kaggle has time limit on notebook runtime. Tensorflow has a thing called checkpointing 

## Lecture notes: neural networks
Neural networkS: network of nodes connected by edges, dense neural network is where every node is connected to every node in next layer. __this is called a dense layer__. 

Basic process is information propagates from input layer, through hidden layers,to the output layer. 

Activation functions are: sigmoid, Tanh, RelU, elu, sleu, linear, leaky RelU. Each has its particular use, and some networks have combinations of activation functions. 

Networks are trained with [[backpropagation]].  Backpropigation assigns the portrion of error made by each node, starting with total error at output, and working backwards over each node calculating the exact portion of error at each node to find individual error values over whole network for every node. These error calculations are called gradient values, which are calculated Usonian partial derivatives. 

Training pitfall: with sigmoid and tanh, gradients can cluster around extreme gradients. This is known as the [[exploding gradient problem]], resulting in failing to converge. This can happen if neural network is too small. This problem is similar to the [[vanishing gradient problem]].

![[232AEFB6-9F08-47C3-A603-77C7FADEADB3.jpeg]]


Neural networks without activation functions behave very similarly to linear regression. Remember the simple perceptron? Yeah.


## Batch normalization: 
Done as a layer inside a network, sandwiched in between hidden layers. This attempts to stabilize the gradients, by constraining the gradients. Network performs better if gradient towards end of network are similar towards Starting layers. This effectively replaces standardizing the input data. This is a very highly effective technique in improving performance. Can occur before or after activation function. It is easier to do after the activation function. This is how tf/Karas does it. This is an option which depending on the problem, may work better one way or the other. This also helps with overfitting and the vanishing/exploding gradient problems. 

## what to do if limited on labeled data??
[[transfer learning]] and [[unsupervised pre training]].



Concept of [[momentum, machine learning]]