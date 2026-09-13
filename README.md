# <span style="color:navy"> **Seminar 01:** </span> <span style="color:green"> **Video Coding**</span>

## Overview

<img src="seminarlogo.png" class="center" style="width:100%;">

# <span style="color:navy"> **Seminar 01:** </span> <span style="color:green"> **Video Coding**</span>

### <span style = "color: navy"> **Instructions:** </span>
- Solve the tasks in the notebook, if not written differently.
- Don't create new cells or delete any cells.
- To complete the tasks you may need to use certain python packages. All common python packages are available in the system environment. Please don't install any other packages.
- Write your code between the lines **YOUR CODE HERE** and **END YOUR CODE HERE**.
- Remember to delete the line `raise NotImplementedError()` in the cell.
- Make sure to validate your assignment by pressing the **Validation** button. Once the assignment is validated with sucess, only then submit the assignmnet. Otherwise, if the validation of your final submission fails during grading it, you may get zero points.

## <span style="color:navy"> <b>Assignment:</b> Geometric Transformations of Images </span>
## <span style="color:green"> Goal: </span>
Learn to apply different geometric transformations to images, like
1. Scalling
2. Translation
3. Rotation
4. Affine transformation
5. Perspective transformation

### <span style = "color: navy"> **Import Python Packages:** </span>
<span style="color:red"> **NOTE:** Use the Python Packages below ONLY</span>

### <span style="color:navy"> **Enter your Student ID** (Matrikel Number) </span>
<span style="color:blue"> *NOTE: If you enter the wrong Matrikel Number you will fail the test.* </span>

## <span style="color:navy"><b>TASK 01:</b> Scaling </span>
- Scaling is just resizing of the image. OpenCV comes with a function `cv.resize()` for this purpose.
- The size of the image can be specified manually, or you can specify the scaling factor. Different interpolation methods are used.
- Preferable interpolation methods are `cv.INTER_AREA` for **shrinking** and `cv.INTER_CUBIC` & `cv.INTER_LINEAR` for **zooming**.
- *By default, the interpolation method `cv.INTER_LINEAR` is used for all resizing purposes in this task*.

### <span style="color:green"> Given Image </span>
Given Image is `Chess_Board.png`. You need to read the given image by using the cell below

### <span style="color:navy"> STEP 1: Down-Scale Image ( $2$ Times) </span>
In this section complete the function `def dscale():` below to down scale the image by factor $2$ (Half the Size of Original)
- Note: <span style="color:red"> You MUST use the interpolation option of opencv as `cv.INTER_LINEAR` </span>

### <span style="color:navy"> Evaluation </span>
Evaluation will be done after submission of your assignment

### <span style="color:navy"> STEP 2: Up-Scale Image ($10$ times) </span>
In this section complete the function `def upscale():` below to up scale the image by factor $10$ (10 time the original image)
- Note: <span style="color:red"> You MUST use the interpolation option of opencv as `cv.INTER_CUBIC` </span>

### <span style="color:navy"> Evaluation </span>
Evaluation will be done after submission of your assignment

## <span style="color:navy"><b>TASK 02:</b> Translation </span>
Translation is the shifting of an object's location. If you know the shift in the $(x,y)$ direction and let it be $(t_x,t_y)$, you can create the transformation matrix $M$ as follows:
<br>
<br>
$ M=\begin{bmatrix} {1} & {0} & {t_x} \\ {0} & {1}& {t_y} \end {bmatrix} $
<br>
<br>
You can make it into a Numpy array of type `np.float32`

### <span style="color:green"> Given Image </span>
Given Image is `Chess_Board.png`. You need to read the given image by using the cell below

### <span style="color:navy"> STEP 1: Shift Image </span>
In this section complete the function `def imshift():` below to shift the image by at $t_x = 300$ and $t_y = 200$

### <span style="color:navy"> Evaluation </span>
Evaluation will be done after submission of your assignment

## <span style="color:navy"><b>TASK 03:</b> Rotation </span>
Rotation of an image for an angle $\theta$ is achieved by the transformation matrix $M$ of the form:

$ M=\begin{bmatrix} {\cos(\theta)} & {-\sin(\theta)} \\ {\sin(\theta)} & {\cos(\theta)} \end {bmatrix} $

<br>
But OpenCV provides scaled rotation with adjustable center of rotation so that you can rotate at any location you prefer. The modified transformation matrix is given by:
<br>
<br>
$ M=\begin{bmatrix} {\alpha} & {\beta} & {(1-\alpha).center.x-\beta.center.y} \\ {-\beta} & {\alpha} & {\beta.center.x+(1-\alpha).center.y} \end {bmatrix} $
<br>
<br>
Where: $ \alpha = scale.\cos(\theta) $ and $ \beta = scale.\sin(\theta) $
<br>
<br>

To find this transformation matrix, <b>OpenCV</b> provides a function, `cv.getRotationMatrix2D`

### <span style="color:green"> Given Image </span>
Given Image is `Chess_Board.png`. You need to read the given image by using the cell below

### <span style="color:navy"> STEP 1: Rotates image by $45^o$: </span>
In this section complete the function `def imrotate():` below to rotate the image by $45^0$ with respect to center of image without any scaling.
- Hint: Define the rotation matric $M$ with `cv.getRotationMatrix2D`.

### <span style="color:navy"> Evaluation </span>
Evaluation will be done after submission of your assignment

## <span style="color:navy"> <b>TASK 04: </b> Affine Transformation </span>
In affine transformation, all parallel lines in the original image will still be parallel in the output image.
- To find the transformation matrix, we need three points from the input image and their corresponding locations in the output image.
- `cv.getAffineTransform` will create a $2$x$3$ matrix which is to be passed to `cv.warpAffine`.

### <span style="color:green"> Given Image </span>
Given Image is `Chess_Board.png`. You need to read the given image by using the cell below

### <span style="color:navy"> STEP 1: ransformed Image </span>
In this section complete the function `def affinetrans()` below to apply affine transform on the given image.  
  
To apply the Affine Transform you need to generate the transformation matrix.  

To find the transformation matrix, take:
- the following three points from the input image as $P_1(0,0)$;  $P_2(900,0)$;  $P_3(0,900)$
- their corresponding locations in the output image as $Q_1(0,0)$;  $Q_2(0,400)$;  $Q_3(400,400)$

### <span style="color:navy"> Evaluation </span>
Evaluation will be done after submission of your assignment

## <span style="color:navy"> <b>TASK 05: </b> Perspective Transformation </span>
For perspective transformation, you need a $3$x$3$ transformation matrix. Straight lines will remain straight even after the transformation.  
To find this transformation matrix you need 4-points on the input image and corresponding 4-points on the output image.

### <span style="color:green"> Given Image </span>
Given Image is `chessboard_perspective.png`. You need to read the given image by using the cell below

### <span style="color:navy"> STEP 1: Perspective Image </span>
In this section complete the function `def persImage():` below to apply perspective transform on the given image. To apply the Affine Transform you need to generate the transformation matrix.   
- Take the following three points from the input image as:  
$P_1(85,15),P_2(275,15), P_3(35,135)$ and $P_4(315,175)$  
- And their corresponding locations in the output image as:  
$Q_1(0,0),Q_2(350,0), Q_3(0,200)$ and $Q_4(350,200)$

- Then the transformation matrix $M$ can be found by the function `cv.getPerspectiveTransform`.
- Then apply `cv.warpPerspective` with this $3$x$3$ transformation matrix.

### <span style="color:navy"> Evaluation </span>
Evaluation will be done after submission of your assignment

## <span style="color:blue"> <b> End of Task</b> </span>

#### <span style="color:red"> DO NOT Run the notebook further </span>

## Notebook Contents

- **Markdown cells:** 30
- **Code cells:** 15

## Dependencies

The notebook contains the following import statements:

```python
import numpy as np
import cv2 as cv
import matplotlib.pyplot as plt
```

## Getting Started

1. Install Python and Jupyter Notebook or JupyterLab.
2. Install the dependencies required by the notebook.
3. Open `VC_Seminar_01.ipynb` in Jupyter.
4. Run the notebook cells in order.

## Files

- `VC_Seminar_01.ipynb` — the original Jupyter notebook.
- `README.md` — this documentation file.

## Notes

This README was generated from the notebook's stored markdown and code cells.