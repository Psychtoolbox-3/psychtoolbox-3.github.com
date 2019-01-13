# [PsychKinectCore('Open')](PsychKinectCore-Open) 
##### [Psychtoolbox](Psychtoolbox)>[PsychKinectCore](PsychKinectCore).{mex*} subfunction

kinectPtr = PsychKinect('Open' [, deviceIndex=0][, numbuffers=2][, bayerFilterMode=1]);

Open connection to Microsoft Kinect box, return a 'kinectPtr' handle to it.  
  
The call tries to open the Kinect box with index 'deviceIndex', or the first  
detected box, if 'deviceIndex' is omitted. It configures the box for video and  
depth capture, using a n-buffered pool for internal storage of up to  
'numbuffers' frames. 'numbuffers' defaults to 2 for double-buffering if omitted.  
'bayerFilterMode' is optional and selects mode of color reconstruction from the  
visual cameras sensor data: A setting of 1 (default) will use a slow and  
unoptimized bayer filter algorithm built into the libfreenect driver to return  
RGB images via the 'GetImage' function. A setting of 0 will disable filtering  
and return a 2D only image with sensor raw data, which you'll need to  
post-process and filter yourself.  
A setting of 2 will return infrared image data from the depth camera instead of  
RGB data.  
A setting of \> 2 would select other filtering methods, but these are not yet  
implemented. You would want to use the default value if you need convenient  
access to RGB images without any effort on your side. Unfiltered raw data has  
the advantage that cpu load of kinect operation is much lower, so you may get  
higher framerates. Also, raw data only requires a third of the storage memory if  
this is of concern, e.g., for high settings of 'numbuffers'.  
The returned handle can be passed to the other subfunctions to operate the  
device.  
  


###See also:

