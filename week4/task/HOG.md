# HOG (Histogram of Oriented Gradients)

- HOG was first introduced in 2005 at CVPR and was initially used for detecting people in images

- Main idea: describing objects based on the distribution of edge magnitudes and directions

## Preprocessing

- Make all pictures have the same dimension (to get the same number of features for each picture)
- Increase quality of each picture (optional)

## Step 2

- Calculate gradients to find edge directions and magnitudes
- Now we have two matrices for each picture: one showing the magnitude of the gradient and one showing the direction of the gradient

## Step 3

- Now we divide the picture into cells and blocks

### Cell

- Cells are non-overlapping square or rectangles (default size is 8x8 pixels)

### Block

- Blocks are overlapping square or rectangles (default size is 2x2 cells)

## Step 4

- Here we try to find histogram of gradient angle for each cell
- To do this we must divide the interval [0, 180] (or [-180,180]) into k parts (typically 9)
- We then create a histogram with k bins for each cell
- That means for each cell we are generating k values (a vector with k values)
- To fill the bins we add the value of the magnitude to the bin that corresponds to the direction of that element
- But to increase the precision the weighted sum of the magnitude of the gradient of each pixel is added to the two nearest neighbor bins
- Weights are calculated based on the difference of gradient angle from the center of a bin (center of the interval)

## Example 1

- Consider the value of k, cell size, block sizes to be their respective default values.
- Consider an element of the Gradient Direction to have the value 80 and its corresponding element in Gradient Magnitude with the value of 2
- Since k equals 9 therefore intervals look like [0,20), ... , [160,180]
- We find the two bins that are closest to 80
- Center value for the interval [60,80) is 70 and the center of [80,100) is 90
- We first find the difference of 80 with each center so: 80 - 70 = 10, 90 - 80 = 10
- Now we divide the magnitude considering these values as the weight.
- In this case each of these bins will have their value added by 2/2 = 1

## Example 2

- Everything like the last example but this time the element in the direction matrix is equal to 36
  and the corresponding element in the magnitude matrix has the value 3
- Center value of the interval [20,40) is 30 and center of [40,60) is 50
- Now we find the weights:
- d1 = 36 - 30 = 6, d2 = 50 - 36 = 14
- d2 is actually the weight for the first interval and d1 for the second interval
- So the first bin will get 14/20 \* 3 and the second bin will get 6/20 \* 3 added to it
- As you can see the weights must be flipped because we want the closest bin to increase more

## Step 5

- We try to normalize the histograms of each block(to decrease the effect of brightness change in pictures)
- Considering default values, each block will give 9 \* 4 = 36 features
- We then put together these features to make one single feature vector
- Because there were 36 features for each block, the total number of features in a picture is number_of_blocks \* 36
- This is why in the preprocessing step, we made all the pictures have the same size. because different sizes would mean different block counts and that would mean different number of features which would cause problems.

## Final step

- The features extracted can then be used as inputs for different machine learning algorithms (e.g SVM, Random Forest) or neural networks and use them for classification problems.
