# [Datapixx('SetVideoHorizontalOverlayAlpha')](Datapixx-SetVideoHorizontalOverlayAlpha) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetVideoHorizontalOverlayAlpha', alphaTable);

Horizontal overlay causes the left and right halves of the video frame to be  
treated as two separate images which are composited, or blended. The resulting  
blended image is then stretched to fill the entire display. As an example, if  
the graphics board is generating a 2048x768 image, then the final display would  
consist principally of the left 1024x768 image, with some parts overlayed by the  
right 1024x768 image. The compositing is done within the rectangle defined by  
Datapixx('SetVideoHorizontalOverlayBounds', boundsRect). Within this bounding  
rectangle, the two images are blended according to an alpha function which is  
defined by calling Datapixx('SetVideoHorizontalOverlayAlpha', alphaTable).  
Because [SetVideoHorizontalOverlayBounds](SetVideoHorizontalOverlayBounds) can be called many times per video  
frame, horizontal overlays can be used to generate very low latency  
gaze-contingent displays, without having to wait for [OpenGL](OpenGL) to page flip.  
-"alphaTable" is a 1024-element array containing a 512-entry XALPHA function,  
followed by a 512-entry YALPHA function. For each pixel within the boundsRect,  
its distance from the left edge of boundsRect is used as an index into the  
XALPHA function, and its distance from the top edge of boundsRect is used as an  
index into the YALPHA function. The XALPHA and YALPHA values are multiplied  
together to calculate the final ALPHA value to be used for that pixel. This  
strategy can generate any separable 2D alpha function, such as rectangles and  
gaussians. An ALPHA value of 0 means that the final pixel will be taken entirely  
from the left half video image. An ALPHA value of 1 means that the final pixel  
will be taken entirely from the right half video image. Intermediate ALPHA  
values result in a blended composite of the left/right half video images. The  
[DATAPixx](DATAPixx) powers up with all ALPHA values initialized to 1, so by default the  
boundsRect will just show a solid overlay consisting of the right half image.  
See [DatapixxGazeContingentDemo](DatapixxGazeContingentDemo).m for an example.  
  


###See also:
[EnableVideoHorizontalOverlay](Datapixx-EnableVideoHorizontalOverlay), [SetVideoHorizontalOverlayBounds](Datapixx-SetVideoHorizontalOverlayBounds)
