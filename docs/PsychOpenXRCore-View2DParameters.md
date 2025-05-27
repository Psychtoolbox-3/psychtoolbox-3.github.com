# [PsychOpenXRCore('View2DParameters')](PsychOpenXRCore-View2DParameters) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

[oldPosition, oldSize, oldOrientation] = PsychOpenXRCore('View2DParameters', openxrPtr, eye [, position][, size][, orientation]);

Query or assign 2D quad view parameters for eye 'eye' of [OpenXR](OpenXR) device  
'openxrPtr'.  
  
Such 2D quad views are used in 'Monoscopic' (same view for both eyes), or  
'Stereoscopic' mode (one view per eye), as well as in 3D modes when a script is  
'Stop'ed and the user asked for use of these 2D quad views instead of projective  
views.  
This returns the current or previous settings for position and size in  
'oldPosition' and 'oldSize', and for orientation in 'oldOrientation' as a  
quaternion.  
'eye' Mandatory: 0 = Left eye or monoscopic view, 1 = right eye in stereo mode.  
Optionally you can specify new settings, as follows:  
'position' 3D position of the center of the virtual viewscreen, relative to the  
eye of the subject. Unit is meters, e.g., [0, 0, -0.5] would center the view at  
x,y offset zero relative to the optical axis, and 0.5 meters away from the eye.  
Iow. the center of the viewscreen aligns with the straightforward looking  
direction of the eye, but the screen floats at 0.5 meters distance. If this  
parameter is left empty [] or omitted, then the position does not change.  
Default position at session startup is centered and at a comfortable viewing  
distance away, so staring straight forward with parallel eyes, e.g., like when  
looking at an infinite point in space, would cause the center of the stimulus  
image to be located at your fixation direction.  
'size' Size of the virtual viewscreen in meters. E.g., [0.8, 1] would have the  
screen at an apparent width of 0.8 meters and an apparent height of 1 meter. If  
the parameter is omitted or left empty [], the size won't be changed. Default  
size is 1 meter high and the width adjusted to preserve the aspect ratio of the  
Psychtoolbox onscreen window into which your script draws, so a drawn circle is  
actually circular instead of elliptic.  
'orientation' A 4 component vector encoding a quaternion for orientation in  
space, ie. a [rx, ry, rz, rw] vector. Or a scalar angle in degrees for rotation  
around z-axis, e.g., 23 for a 23 degrees rotation around the optical axis / line  
of sight of the viewer.  
  


###See also:
[ViewType](PsychOpenXRCore-ViewType)
