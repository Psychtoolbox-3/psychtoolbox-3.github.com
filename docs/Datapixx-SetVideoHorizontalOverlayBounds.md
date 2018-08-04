# [Datapixx('SetVideoHorizontalOverlayBounds')](Datapixx-SetVideoHorizontalOverlayBounds) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Horizontal overlay causes the left and right halves of the video frame to be  
treated as two separate images which are composited, or blended. The resulting  
blended image is then stretched to fill the entire display. As an example, if  
the graphics board is generating a 2048x768 image, then the final display would  
consist principally of the left 1024x768 image, with some parts overlayed by the  
right 1024x768 image. The compositing is done within the rectangle defined by  
Datapixx('SetVideoHorizontalOverlayBounds', boundsRect).  
-"boundsRect" is a 4-element array containing the left/top/right/bottom pixel  
coordinates of the compositing rectangle. Within this bounding rectangle, the  
two images are blended according to an alpha function which is defined by  
calling Datapixx('SetVideoHorizontalOverlayAlpha', alphaTable). Because  
[SetVideoHorizontalOverlayBounds](SetVideoHorizontalOverlayBounds) can be called many times per video frame,  
horizontal overlays can be used to generate very low latency gaze-contingent  
displays, without having to wait for [OpenGL](OpenGL) to page flip.  
See [DatapixxGazeContingentDemo](DatapixxGazeContingentDemo).m for an example.  
  


###See also:
[EnableVideoHorizontalOverlay](Datapixx-EnableVideoHorizontalOverlay), [SetVideoHorizontalOverlayAlpha](Datapixx-SetVideoHorizontalOverlayAlpha)
