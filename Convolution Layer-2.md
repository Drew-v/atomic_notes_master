 **The objective of the convolution layer is to extract the high level features such as edges, from input image** Convolution layers are used in [[convolutional neural networks]].
- stride length regulates kernal/filter shifting (indexing) over the image
- in every shift, a matrix multiplication is performed between K and the portion P of image which kernal is overlapping

<div style="float: left; margin-right: 10px">
    <img width="150" height="200" src="https://miro.medium.com/max/652/1*NsiYxt8tPDQyjyH3C08PVA@2x.png">
</div>
In this case, image being traversed is in RGB (greyscale would be one layer), and so has a depth of 3 layers. The filter shifts to the right until reach end, moves down one level and continues right shifting.  The outer row/column of filter extends 1 past the image edges.
<br clear="Left"/>
<div style="float: right">
    <img width="300" height="200" src="https://miro.medium.com/max/1400/1*ciDgQEjViWLnCbmX-EeSrA.gif">
</div>



- For a 5x5 image and a 3x3 filter, output would be a scalar value for each shift, and an end result of a 4x4 matrix 
- If multiple layers deep, scalar value of each layer is combined to single value for output matrix
- Results of matrix mult. are summed if multiple layers, and a bias is added
- **this operation gives us a squashed one depth convoluted feature output**

Conventionally, the first conv layer detects low level features; edges, color or gradient orientation. Adding more conv layers enables higher level features to be detected. A kernal can either increase, decrease, or keep dimensionality of input image the same
- **Same Padding**: 5x5x1 image  -> 6x6x1 image and apply 3x3x1 kernal, the coonvolved matrix is 5x5x1, same as input image
- **Valid Padding:** without padding, resultant convolved matrix is 3x3x1, size of kernal itself