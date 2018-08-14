# [Datapixx('SetVideoPixelSyncLine')](Datapixx-SetVideoPixelSyncLine) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Configure pixel sync raster line operation.  
Register cache writes to the Datapixx can be delayed until a user-specified  
pixel sequence occurs. This allows signal input or output to be synchronized to  
video with microsecond precision. Datapixx reset behaviour is to recognize the  
pixel sequence anywhere within a video frame. [SetVideoPixelSyncLine](SetVideoPixelSyncLine) configures  
whether the pixel sequence should only be recognized on a single raster line.  
-"rasterLine" specifies the raster line.  
-"singleLine" default value of 1 means that pixel sync will only be recognized  
on rasterLine. Passing a value of 0 to singleLine will allow the pixel sequences  
to be recognized on any raster line.  
-"blankLine" default value of 1 means that rasterLine will always be displayed  
black. This effectively hides the presence of the pixel sequence from the  
display viewer. Passing a value of 0 to blankLine will display rasterLine as  
normal video.  
  


###See also:
[RegWrPixelSync](Datapixx-RegWrPixelSync), [GetVideoStatus](Datapixx-GetVideoStatus)
