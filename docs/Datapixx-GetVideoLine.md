# [Datapixx('GetVideoLine')](Datapixx-GetVideoLine) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

pixels = Datapixx('GetVideoLine' [, nPixels=HORIZONTAL_RESOLUTION]);

Upload pixels from Datapixx internal video receiver line buffer to local host.  
The pixels uploaded are from the start of the top raster line of the most recent  
video frame.  
-"nPixels" specifies the number of pixels to be uploaded. The default value is  
the horizontal resolution of the display. If nPixels is greater than the  
horizontal resolution of the display, then the returned pixels will include the  
digital video data received during the horizontal blanking interval, and  
possibly into the next raster line. The maximum number of pixels which can be  
requested is 2048.  
-"pixels" is returned as a 2D array with one column for each pixel, and one row  
for each of the red/green/blue components. Each datum is an 8-bit unsigned pixel  
component value.  
Note that [GetVideoLine](GetVideoLine) is asynchronous w.r.t. internal line buffer writes. If  
the top raster line is modified between two video frames, and [GetVideoLine](GetVideoLine)  
executes while the new top raster line is being received, then the returned data  
could be a combination of the old and new data.  
  


###See also:

