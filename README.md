# Zhangs-method-camera-calibration

Estimating parameters of the camera like the focal length, distortion coefficients and principle point is called Camera Calibration. It is one of the most time consuming and important part of any computer vision research involving 3D geometry. An automatic way to perform efficient and robust camera calibration would be wonderful. One such method was presented Zhengyou Zhang of Microsoft in this paper and is regarded as one of the hallmark papers in camera calibration. Recall that the camera calibration matrix K is given as follows:

K=⎡⎣⎢fx000fy0cxcy1⎤⎦⎥

and radial distortion parameters are denoted by k1 and k2 respectively. Your task is to estimate fx,fy,cx,cy,k1,k2.

#  Initial Parameter Estimation

We are trying to get a good initial estimate of the parameters so that we can feed it into the non-linear optimizer. We will define the parameters we are using in the code next.

x denotes the image points, X denotes the world points (points on the checkerboard), k=[k1,k2] denotes the radial distortion parameters, K denotes the camera calibration matrix, R and t represent the rotation matrix and the translation of the camera in the world frame.

# Solving for approximate K or camera intrinsic matrix and R  and t or camera extrinsics
Refer toin this [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr98-71.pdf) for a solution of parameters in K and for details on how to estimate R and t. Used cv2.findChessboardCorners function in OpenCV to find the corners of the Checker board with appropriate parameters here.

# Approximate Distortion k

Because we assumed that the camera has minimal distortion we can assume that k=[0,0]T for a good initial estimate.


# Non-linear Geometric Error Minimization

We have the initial estimates of K,R,t,k, now we want to minimize the geometric error defined as given below:

    ∑i=1N∑j=1M||xi,j−x^i,j(K,Ri,ti,Xj,k)||

Formally, the optimization problem is as follows:

    argminfx,fy,cx,cy,k1,k2∑i=1N∑j=1M||xi,j−x^i,j(K,Ri,ti,Xj,k)||

Here xi,j and x^i,j are an inhomogeneous representation

