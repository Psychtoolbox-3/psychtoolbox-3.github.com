# [PsychKinectCore](PsychKinectCore)
##### [Psychtoolbox](Psychtoolbox)>[PsychKinectCore](PsychKinectCore)

PsychKinectCore - A Psychtoolbox driver for the Microsoft Kinect.  
  
This driver allows to control the box and grab color images and depth  
images from the Kinect depth camera.  
  
It uses and requires the free software drivers and libraries from the OpenKinect  
project (Thanks!): http://openkinect.org  
  
Libfreenect is Copyright (C) 2010 - 2014 individual OpenKinect contributors.  
Libfreenect requires libusb-1.0, which is licensed under LGPL v2 or later.  
See 'help InstallKinect' for more detailed license information.  
  
The PsychKinectCore driver is licensed to you under the terms of the MIT license.  
See 'help License.txt' in the Psychtoolbox root folder for more details.  
  
The driver also uses bits of math inspired by Nicolas Burrus Kinect work:  
http://nicolas.burrus.name/index.php/Research/KinectCalibration   
  
  
Usage:  
kinectPtr = PsychKinect('Open' [, deviceIndex=0][, numbuffers=2]][, bayerFilterMode=1]);  
PsychKinect('Close', kinectPtr);  
PsychKinect('SetAngle', kinectPtr, angle);  
[starttime, fps, cwidth, cheight, dwidth, dheight] = PsychKinect('Start', kinectPtr [, dropframes=0]);  
PsychKinect('Stop', kinectPtr);  
status = PsychKinect('GetStatus', kinectPtr);  
[...old parameter settings in order of inputs... ] = PsychKinect('SetBaseCalibration', kinectPtr, depthsIntrinsics, rgbIntrinsics, rgbRotation, rgbTranslation, depthsUndistort, rgbUndistort, depthBaseAndOffset);  
[result, cts, age] = PsychKinect('GrabFrame', kinectPtr [, waitMode=1][, mostrecent=0]);  
PsychKinect('ReleaseFrame', kinectPtr);  
[imageOrPtr, width, height, channels, extType, extFormat] = PsychKinect('GetImage', kinectPtr [, imtype=0][, returnTexturePtr=0]);  
[imageOrPtr, width, height, extType, extFormat] = PsychKinect('GetDepthImage', kinectPtr [, format=0][, returnTexturePtr=0]);  
  

ok<STOUT\>  
  


