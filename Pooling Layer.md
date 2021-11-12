The Pooling layer follows a [[Convolution Layer]] in a [[convolutional neural networks]] . It takes a convoluted feature and reduces its spatial size, to decrease computational power needed for subsequent steps. It's useful for extracting dominant features which are rotational and [[positional invariant]]??

Two kinds: [[Max Pooling]] (returns max value of convolution slice) and [[Average Pooling]] (returns average value of convolution slice). ** For this reason, max pooling tends to perform better than average pooling**
<img src="https://miro.medium.com/max/1000/1*KQIEqhxzICU7thjaQBfPBQ.png">
