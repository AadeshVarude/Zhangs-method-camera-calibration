# Zhangs-method-camera-calibration

Estimating parameters of the camera like the focal length, distortion coefficients and principle point is called Camera Calibration. It is one of the most time consuming and important part of any computer vision research involving 3D geometry. An automatic way to perform efficient and robust camera calibration would be wonderful. One such method was presented Zhengyou Zhang of Microsoft in this paper and is regarded as one of the hallmark papers in camera calibration. Recall that the camera calibration matrix K is given as follows:

K=⎡⎣⎢fx000fy0cxcy1⎤⎦⎥

and radial distortion parameters are denoted by k1 and k2 respectively. Your task is to estimate fx,fy,cx,cy,k1,k2.
