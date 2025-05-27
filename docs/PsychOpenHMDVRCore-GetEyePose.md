# [PsychOpenHMDVRCore('GetEyePose')](PsychOpenHMDVRCore-GetEyePose) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

[eyePose, eyeIndex, glModelviewMatrix] = PsychOpenHMDVRCore('GetEyePose', openhmdPtr, renderPass);

Return current predicted pose vector for an eye for [OpenHMD](OpenHMD) device 'openhmdPtr'.  
NOTE: As of August 2017, this function does not provide optimized predicted pose  
and is here just for backwards compatibility, as [OpenHMD](OpenHMD) does not provide such  
per-eye tracking info.  
  
'renderPass' is the view render pass for which to provide the data: 0 = First  
pass, 1 = Second pass.  
Return value is the vector 'eyePose' which defines the position and orientation  
for the eye corresponding to the requested renderPass ie. 'eyePose' = [posX,  
posY, posZ, rotX, rotY, rotZ, rotW].  
The second return value is the 'eyeIndex', the index of the eye whose view  
should be rendered. This would be 0 for left eye, and 1 for right eye, and could  
be used to select the target render view via, e.g.,  
[Screen](Screen)('SelectStereoDrawBuffer', window, eyeIndex);  
Which 'eyeIndex' corresponds to the first or second 'renderPass', ie., if the  
left eye should be rendered first, or if the right eye should be rendered first,  
depends on the visual scanning order of the HMD display panel - is it top to  
bottom, left to right, or right to left? This function provides that optimized  
mapping. Using this function to query the parameters for render setup of an eye  
can provide a bit more accuracy in rendering, at the expense of more complex  
usercode.  
'glModelviewMatrix' [OpenGL](OpenGL) modelview matrix, as computed by [OpenHMD](OpenHMD) from  
tracking data.  
  


###See also:

