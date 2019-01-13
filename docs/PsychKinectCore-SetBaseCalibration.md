# [PsychKinectCore('SetBaseCalibration')](PsychKinectCore-SetBaseCalibration) 
##### [Psychtoolbox](Psychtoolbox)>[PsychKinectCore](PsychKinectCore).{mex*} subfunction

[...old parameter settings in order of inputs... ] = PsychKinect('SetBaseCalibration', kinectPtr, depthsIntrinsics, rgbIntrinsics, rgbRotation, rgbTranslation, depthsUndistort, rgbUndistort, depthBaseAndOffset);

Set and/or Get camera calibration matrices of box 'kinectPtr'.  
  
This function assigns various parameters needed for 3D reconstruction of the 3D  
scene from Kinect raw sensor data.  
You will need to use an external 3rd party camera calibration tool to determine  
the specific parameters of your Kinect. The driver uses some builtin defaults of  
a reference Kinect box if you don't provide updated parameters via this  
function. This allows to get at least ok results for quick testing and  
experimenting.  
The optical undistortion parameters (arguments 6 and 7) may not get used by  
early versions of the driver, or in fast 3D preview modes. They are accepted but  
silently ignored on such configurations.  
'depthsIntrinsics' vector with intrinsic parameters of depth cam:  
 [fx, fy, cx, cy].  
'rgbIntrinsics' vector with intrinsic parameters of the RGB video camera:  
[fx, fy, cx, cy].  
'rgbRotation' a 3x3 rotation matrix which encodes rotation of the color camera  
with respect to the depths camera.  
'rgbTranslation' a 3 component translation vector which encodes translation of  
the color camera with respect to the depths camera.  
'depthsUndistort' undistoration parameters for depths camera.  
[k1,k2,p1,p2,k3].  
'rgbUndistort' undistoration parameters for RGB video camera.  
[k1,k2,p1,p2,k3].  
'depthBaseAndOffset' a 2 element vector [kinectDepthBase, kinectDephOffset].  
  


###See also:

