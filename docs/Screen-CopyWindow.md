# [Screen('CopyWindow')](Screen-CopyWindow) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('CopyWindow',srcWindowPtr,dstWindowPtr,[srcRect],[dstRect],[copyMode])

Copy images, quickly, between two windows (on- or off- screen).  
Content from onscreen windows is copied from the onscreen windows back buffer,  
or the onscreen windows draw buffer if the imaging pipeline is enabled, but  
never from the onscreen windows front buffer.  
srcRect and dstRect are set to the size of windows srcWindowPtr and dstWindowPtr  
by default. [copyMode] is accepted as input but currently ignored.  
[CopyWindow](CopyWindow) is mostly here for compatibility to PTB-2. If you want to copy images  
really quickly, use the 'MakeTexture' and 'DrawTexture' commands. They also  
allow for rotated drawing and advanced blending operations.  
The current [CopyWindow](CopyWindow) implementation has a couple of restrictions on old  
graphics cards, which may not apply anymore on modern cards:  
One can't copy from an offscreen window into the -same- offscreen window.  
One can't copy from an onscreen window into a -different- onscreen window.  
Sizes of sourceRect and targetRect need to match for Onscreen-\>Offscreen copy.  
  


###See also:
[PutImage](Screen-PutImage), [GetImage](Screen-GetImage), [OpenOffscreenWindow](Screen-OpenOffscreenWindow), [MakeTexture](Screen-MakeTexture), [DrawTexture](Screen-DrawTexture)
