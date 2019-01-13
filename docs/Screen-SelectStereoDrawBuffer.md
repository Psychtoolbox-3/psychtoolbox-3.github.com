# [Screen('SelectStereoDrawBuffer')](Screen-SelectStereoDrawBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Select the target buffer for drawing commands in stereo display mode and or  
return the current/old buffer selection in 'currentbuffer'.  
This function only applies to stereo mode, it does nothing in mono mode.  
"windowPtr" is the pointer to the onscreen stereo window.  
"bufferid" (optional) is either == 0 for selecting the left-eye buffer or == 1  
for selecting the right-eye buffer. You need to call this command after each  
[Screen](Screen)('[Flip](Flip)') command or after drawing to an offscreen window again in order to  
reestablish your selection of draw buffer, otherwise the results of drawing  
operations will be undefined and most probably not what you want.  
"param1" (optional) a parameter whose meaning depends on the active stereo mode:  
In stereoModes 1 and 11 (frame sequential stereo) it allows to select if  
stimulus onset should happen in an even video refresh interval (value 0) or in  
an odd interval (value 1). Even and odd intervals correspond to either left- or  
right-eye view, so this allows to choose if you want to have stimulus onset on  
left eye or right eye.  
If you want to use a stereo display mode, we recommend enabling the imaging  
pipeline as well. The imaging pipeline will not work with very old hardware  
(roughly pre 2007) but it allows for more reliable stereo operation especially  
when using low-level [OpenGL](OpenGL) for real 3D drawing. It also allows to parameterize  
aspects of stereo presentation, e.g., gains and other settings of anaglyph  
stereo.  
  


###See also:
[OpenWindow](Screen-OpenWindow) Flip
