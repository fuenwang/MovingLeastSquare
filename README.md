# MovingLeastSquare
## Introduction
This is the implementation for [Moving Least Square](http://faculty.cs.tamu.edu/schaefer/research/mls.pdf), it is used for 
wapring image into other shape with several control points. So far, I have implemented two kind of moving least sqare:
1. Affine Deformation
2. Rigid Deformation
3. Similarity Deformation

## Usage
```python
import numpy as np
import MovingLSQ as MLSQ

if __name__ == '__main__':
#
#   First, you need to label Control Points.
#   In my example, control points start from "controlSrcPts" to "controlDstPts"
#
    controlSrcPts = np.array([
                    [0, 0],
                    [1, 1],
                    [3, 4]
                ])
    controlDstPts = np.array([
                    [50, 50],
                    [60, 60],
                    [70, 80]
                ])
    solver = MLSQ.MovingLSQ(controlSrcPts, controlDstPts)  # initialize
#
#   Then according to control points, all the points you want to transform need to be 
#   parsed to "solver". In my example, I only want to find the destination of two points.
#
    srcPts = np.array([
                    [3, 4],
                    [5, 6]
                ])
    dstPts = solver.Run_Affine(srcPts) # For Affine Deformation
    dstPts = solver.Run_Rigid(srcPts)  # For Rigid Deformation
    dstPts = solver.Run_Similarity(srcPts) # For Similarity Deformation
#
#   "dstPts" is the final position of "srcPts"
#
```
