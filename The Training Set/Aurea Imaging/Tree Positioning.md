Commit before July 15th of the [Detection Pipeline](https://github.com/aureaimaging/tms-detection-pipeline-service)  uses depth of a bounding box and angle relative to heading for object positioning

# Goal
Projected points should lie within 10 cm of the ground truth 



# Requirements
We need to understand every part of it before we can decide on what to work on:

## Input Image 
Speed and Quality affect Detections. It also seems to change the behavior of Depth
![[Pasted image 20250715150628.png]]
Number frames an id was seen at different speeds in seen here. We can see a higher number of frames for ids 0 and 10 because they were set at the end

## Depth
Depth plays an important role in positioning 

![[Pasted image 20250715131459.png]] ![[Pasted image 20250715131545.png]]![[Pasted image 20250715133221.png]]

The above graphs are driven at 5 m/h , 8 m/h and 2 m/h respectively

| Speed (mph) | y intercept | slope | R squared |
| ----------- | ----------- | ----- | --------- |
| 2           | 0.366       | 0.665 | 0.875     |
| 5           | 0.575       | 0.55  | 0.8       |
| 8           | 0.532       | 0.597 | 0.95      |

So we see the trend changes over speed which is not ideal.

![[Pasted image 20250715154634.png]]

![[Pasted image 20250715160450.png]]

Here we see how different depth sources behave . I would expect depth to behave more like the aruco plot (pnp) because in my mind depth would ideally follow a parabola when an object passes by . 
Simulating a point moving past another point at 2m the distance plot looks like this 
![[Pasted image 20250715162335.png]]
The distance function is quadratic and the function should be differentiable at minimum so it makes sense that the aruco distance plateaus at the end

## Timing
When we pushback the timestamp by 130ms things weirdly start looking better.
![[Pasted image 20250721100225.png]] 
The orange points are Aruco markers with ZED depth, green are arucos with[ Perspective N-Point Algorithm](https://medium.com/@rashik.shrestha/perspective-n-point-pnp-f2c7dd4ef1ed) and Red Star is the ground truth

Evaluating the resulting cluster centers with the ground truth:
Zed:
![[Pasted image 20250721110248.png]]
PNP:
![[Pasted image 20250721110313.png]]

This shows that ZED depth is actually reliable 