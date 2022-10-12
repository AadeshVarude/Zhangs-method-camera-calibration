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

# Results
![image](https://user-images.githubusercontent.com/50541542/195444507-562b1aa3-e012-4431-b410-dd4f26d523c6.png)

![image](https://user-images.githubusercontent.com/50541542/195444580-24381289-44b8-47d0-8ef0-e0e8bd0fd408.png)

![image](https://user-images.githubusercontent.com/50541542/195444665-46e0a766-a789-4dc6-8a5f-f4650351a5bb.png)

![image](https://user-images.githubusercontent.com/50541542/195444819-87595f87-3c81-465d-adb6-c7c83ab63207.png)

![image](https://user-images.githubusercontent.com/50541542/195444876-91c1a1ef-dc08-4c36-b7b9-4db2042e24b8.png)

![image](https://user-images.githubusercontent.com/50541542/195444974-fd36ec12-d585-476d-b72b-8961e5621f1a.png)




