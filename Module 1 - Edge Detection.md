## Objectives:
- introduction to edge detection, the placement of marks wherever brightness in an image changes a lot
	- [[Edge Detection - Roberts method]]
	- [[Edge Detection - Sobel method]]
- Understand and implement convolution between two arrays of numbers
- purpose of edge detection
- how ED is achieved using a derivative operation
	- differentiation of a picture involves two simultanius dimensions
	- these two simultanius derivatives constitude a vector entitiy 
- A practical differentiation operation is a subtraction, which in turn is a specific convolution, [[edge detection - convolution]]
- [[edge detection - threshholding]] as the final step in edge detection 
	- a vector's 'size' ( for thresholding puropses) is measured by magnatude calculation
- [[edge detection - smoothing]]
- understand how to use an image diplay tool to examine images, run programs on images and discuss resulting images from these programs

__I will:__
- watch set of videos
- complete mini homeworks
- do the required assignment for module 1

### Problems with edge detection
-If image has high noise, edge detector may see noise as edges. Can be fixed with [[edge detection - smoothing]] , averaging nighboring pixels

__must watch video 8 and 9__ 1/12/2022