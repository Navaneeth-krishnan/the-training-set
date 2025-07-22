

### Rotating an Intrinsic Matrix [Needs Verification]

To compute the **new intrinsic matrix K′** after rotating an image:

$K' = R_{2D} \cdot K$ 

Where:
$R_{2D}$ ​: the 2D rotation matrix representing the image rotation **in pixel space**.

For example, a 90° counterclockwise image rotation (in pixel coordinates) has:

$R_{2D}^{90^\circ CCW} = \begin{bmatrix} 0 & -1 & H \\ 1 & 0 & 0 \\ 0 & 0 & 1 \end{bmatrix}$

When you rotate the **image clockwise**, it’s exactly the same idea as before—only the 2D rotation matrix changes sign. In pixel‐homogeneous coordinates (where the origin is the **top–left** corner), a **90° clockwise** rotation of a $W\times H$ image is given by the homography

$R_{2D}^{90^\circ CW} \;=\; \begin{bmatrix} 0 & 1 & 0 \\ -1 & 0 & W \\ 0 & 0 & 1 \end{bmatrix}.$


 
 So clockwise rotation would yield

$K' =\begin{bmatrix} 0 & 1 & 0 \\ -1 & 0 & W \\ 0 & 0 & 1 \end{bmatrix} \times \begin{bmatrix} f_{x}& 0 & c_{x} \\ 0 & f_{y} &c_{y}\\ 0 & 0 & 1 \end{bmatrix}$



= 
 This was what I found to be working: need to verify it with the above transformation.
 clockwise:

cx_new = unrotated_height - cy_original

cy_new = cx_original

Counterclockwise:

cx_new = cy_original

cy_new= unrotated_width - cx_original