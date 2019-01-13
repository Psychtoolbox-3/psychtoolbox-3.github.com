# [Datapixx('RegWrRdPixelSync')](Datapixx-RegWrRdPixelSync) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

isTimeout = Datapixx('RegWrRdPixelSync', pixelSequence [, timeout=255]);

Write local register cache modifications to Datapixx when the specified pixel  
sequence appears on the video display, then read back Datapixx register snapshot  
to local cache. This is a good way to write Datapixx registers with microsecond  
synchronization to a specific location in a video frame, then pause program  
execution until after the pixel has passed. All Datapixx Set\* functions do fast  
writes to a local register cache on the host, and all Datapixx Get\* functions do  
fast reads from this local register cache. [RegWrRdPixelSync](RegWrRdPixelSync) writes these cached  
register modifications back to the Datapixx over USB, then waits for a fresh  
snapshot of the Datapixx registers to be returned over USB. The cache writeback  
USB message is sent immediately, but the Datapixx itself waits until the  
specified pixel sequence is presented before writing the registers.  
-pixelSequence is a two dimensional array of 8-bit pixel values. Each column  
contains the RGB values for one pixel in the sequence. The sequence can contain  
from 1 to 8 pixels. The array must contain 3 rows; one row for each of the red,  
green, and blue pixel components. For example, passing [255 0; 0 255; 0 0] would  
wait until a red-green pixel pair is displayed.  
Note that a display's gamma setting can transform pixel values between the frame  
buffer and the display. Use the [GetVideoLine](GetVideoLine) function to read back which pixel  
values are really sent to the display when a pixel sequence is drawn in the  
frame buffer. The pixel values returned by [GetVideoLine](GetVideoLine) are the values which  
should be used in pixelSequence.  
-timeout is the maximum number of video frames (0-65535) which the Datapixx  
should wait before continuing to process USB traffic. If the timeout is reached  
without the specified pixel sequence having been displayed, then the isTimeout  
return value will be true, and the pixelSyncTimeout field returned by  
[GetVideoStatus](GetVideoStatus) will be true.  
[RegWrRdPixelSync](RegWrRdPixelSync) returns when registers are read back after the target pixel  
sequence has passed, or a timeout occurs.  
  


###See also:
[RegWrRd](Datapixx-RegWrRd), [RegWrRdVideoSync](Datapixx-RegWrRdVideoSync), [RegWrPixelSync](Datapixx-RegWrPixelSync), [GetVideoStatus](Datapixx-GetVideoStatus)
