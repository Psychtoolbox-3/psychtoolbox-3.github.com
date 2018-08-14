# [Screen('GetCapturedImage')](Screen-GetCapturedImage) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Try to fetch a new image from video capture device 'capturePtr' for visual  
playback/display in window 'windowPtr' and return a texture-handle 'texturePtr'  
on successfull completion. 'waitForImage' If set to 1 (default), the function  
will wait until the image becomes available. If set to zero, the function will  
just poll for a new image. If none is ready, it will return a texturePtr of  
zero, or -1 if none will become ready because capture has been stopped. Set  
'waitForImage' = 2 if you just want to get the summed intensity or timestamp of  
the image. 'waitForImage' = 3 will behave as a setting of 2, but it will only  
poll, not block. Note: Settings 2 and 3 will not return textures, therefore the  
returned 'texturePtr' will always be zero, irrespective of availabilty of new  
frames. You'll have to check the other return arguments for indication that a  
frame has arrived, e.g., non-zero summed\_intensity.  
The setting 'waitForImage' = 4 is special: It will not block, nor will it return  
any information, but will make sure the capture engine keeps running. This is  
useful if you want PTB to perform harddisk recording of video footage in the  
background without any need to access information about the capture process or  
the actual video data from within Matlab. This is the least ressource consuming  
way of doing this.  
'oldTexture' (if provided) allows you to pass the texture handle of an already  
existing texture. Psychtoolbox will reuse that texture by overwriting its  
previous image content with the new image, instead of creating a completely new  
texture for the new image. Use of this ''recycling facility'' may allow for  
higher capture framerates and lower latencies on low-end graphics hardware in  
some cases. Providing a value of 'oldTexture'=0 is the same as leaving it out.  
The optional argument 'specialmode' allows to request special treatment of  
textures. Currently, specialmode = 1 will ask PTB to use GL\_TEXTURE\_2D textures  
instead of other formats. This is sometimes less efficient, unless you want to  
do realtime blurring of images. If you set specialmode = 2, then the optional  
return value 'average\_intensityOrRawImageMatrix' will not return the summed  
pixel intensity, but a Matlab uint8 or uint16 matrix with the captured raw image  
data for direct use within Matlab, e.g., via the image processing toolbox. uint8  
matrices return intensities in the range 0 - 255. uint16 matrices for high  
bitdepth video capture return 16 bit intensity values in which the most  
significant bit (the 16th bit) contains the most significant bit of the cameras  
sensor data. This means that if a camera has a sensor that returns less than 16  
bit precision, then the least significant bits in the uint16 return values will  
be all-zero, e.g., a 12 bit sensor would return uint16 values with the 4 least  
significant bits all zero.  
If you set 'specialmode' = 4 and provide a double-encoded memory pointer in  
'targetmemptr', then PTB will copy the raw image data into that buffer instead  
of returning it as a matrix in the fourth return argument. The buffer is  
expected to be of sufficient size, otherwise a crash of Matlab or Octave will  
occur (Experts only!).  
A 'specialmode' == 8 will require high-precision drawing, see the specialFlag ==  
2 setting in [Screen](Screen)('MakeTexture') for a description of its meaning. A  
'specialMode' == 16 will prevent automatic mipmap-generation for GL\_TEXTURE\_2D  
textures. A 'specialMode' == 32 will prevent closing of the texture by a call to  
[Screen](Screen)('[Close](Close)');  
'capturetimestamp' contains the system time when the returned image was  
captured. This timestamp has been verified to be very precise on Linux with  
suitable professional IIDC 1394 firewire cameras when the dc1394 capture engine  
is used. The same may be true for OS/X, although this hasn't been extensively  
tested. If other operating systems, capture engines or cameras are used, the  
timestamp may become just a rough approximation of unknown precision.  
The (optional) return value 'droppedcount' contains the number of captured  
frames that had to be dropped to keep in sync with realtime or due to internal  
shortage of buffer memory. If you didn't specify the 'dropFrames' flag in  
[Screen](Screen)('StartVideoCapture') then it will report the number of pending buffers  
which can be fetched, i.e., how many more buffers are queued up for delivery.  
The (optional) return value 'average\_intensityOrRawImageMatrix' contains the  
average of all pixel intensity values of all channels of the image - some  
measure of overall brightness. The value is normalized to the 0.0 - 1.0 range,  
where an all-black image would return 0.0 and an all-white saturated image would  
return 1.0. Only query this value if you need it, as its computation requires  
extra time.  


###See also:
[CloseVideoCapture](Screen-CloseVideoCapture) [StartVideoCapture](Screen-StartVideoCapture) [StopVideoCapture](Screen-StopVideoCapture) [GetCapturedImage](Screen-GetCapturedImage)
