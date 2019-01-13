# [PsychKinectCore('GetImage')](PsychKinectCore-GetImage) 
##### [Psychtoolbox](Psychtoolbox)>[PsychKinectCore](PsychKinectCore).{mex*} subfunction


Return the color image data for the frame fetched via 'GrabFrame'.  
  
If 'returnTexturePtr' is zero (default), a uint8 3D image matrix is returned.  
The matrix is usually in RGB pixel interleaved row-major format for efficiency  
reasons, ie. to improve processing speed for realtime applications.  
If the optional 'bayerFilterMode' flag in [PsychKinect](PsychKinect)('Open') was set to 0, then  
the image is returned as a row-major 2D matrix with the raw color sensor data  
instead of post-processed RGB bayer filtered data, again for efficiency reasons.  
A 'bayerfilter' setting of 2 would return a row-major 2D matrix with infrared  
depth sensor raw data.  
If you want to use the image matrix with standard Matlab/Octave or PTB  
functions, e.g., feed it to the image processing toolbox, imwrite(), imshow(),  
or [Screen](Screen)('MakeTexture'), you need to convert it into the expected Matlab/Octave  
planar column-major format:  
  
for i = 1:channels  
   retpixels(:,:,i) = transpose(squeeze(imageOrPtr(i, :, :)));  
end  
imshow(retpixels);  
  
'imtype' if set to 1, returns a color-coded depth image instead of the RGB  
camera image.  
If 'returnTexturePtr' is one, a double-encoded memory pointer to a LUMINANCE8 or  
RGB8 rectangle texture buffer is returned, for use with  
[Screen](Screen)('SetOpenGLTextureFromMemPointer') for injection into PTB's texturing  
system. 'extType' and 'extFormat' encode the proper parameters to pass for  
external format and type to [Screen](Screen)('SetOpenGLTextureFromMemPointer').  
See for example [KinectDemo](KinectDemo).m for how this is used for fast video display.  
  


###See also:

