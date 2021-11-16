[written in relation to multilayer perceptron, how does this generalize to other algorithms?]
A learning mechanism for neural networks, to iteratively **adjust weights in network with goal of minimizing the cost function. **
The requirement for backpropagation is that the weighted sum and the threshold function ( for example the RelU function) must be differentiable, having a bounded derivative, because **gradient descent is typically the optimization function in multilayer perceptron**.
<img src="https://miro.medium.com/max/1400/1*tYQrcNF2rPAETvzpqGX0PA.png" height="400" width="500">
With each iteration, **after the feedforward step** (weighted sums forwarded through layers) **the gradient of the Mean Squared Error is computed **across all input and output pairs. 
**Next, to propagate it back, the weights of the first hidden layer are updated with the value of the gradient.** This is how weights are propagated back the the starting point of the neural network!
<img src="https://miro.medium.com/max/1400/1*-ojxaaPB17oBrr9ICDPdmg.png" height="200" width="600">
This process **continues until gradient for each input-output pair has converged**, meaning the newly computed gradient hasn't changed more than a specified _convergence threshold_, compared to previous iteration. 

