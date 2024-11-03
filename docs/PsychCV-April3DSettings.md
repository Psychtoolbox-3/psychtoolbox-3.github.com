# [PsychCV('April3DSettings')](PsychCV-April3DSettings) 
##### [Psychtoolbox](Psychtoolbox)>[PsychCV](PsychCV).{mex*} subfunction

[glProjectionMatrix, camCalib, tagSize, minD, maxD] = PsychCV('April3DSettings' [, camCalib][, tagSize][, minD][, maxD]);

Return current 3D marker pose reconstruction and 3D rendering parameters,  
optionally change them.  
For 6-[DoF](DoF) 3D marker tag pose computation, and for return of [OpenGL](OpenGL) compliant  
rendering matrices, information about the physical size of april tag markers,  
[OpenGL](OpenGL) near and far clipping planes, andthe intrinsic optical parameters of the  
camera that captures the marker images are needed.  
These parameters can be changed anytime with this subfunction. Following  
settings are available:  
'camCalib' Intrinsic camera parameters vector: [cx, cy, fx, fy]. (cx,cy) is  
sensor center in pixels, (fx,fy) is focal length in pixels.  
'tagSize' Size of an April tag in meters, ie. length of one side of the square  
tag.  
'minD' Near clipping distance for [OpenGL](OpenGL) frustum computation - Affects  
'glProjectionMatrix' matrix only.  
'maxD' Far clipping distance for [OpenGL](OpenGL) frustum computation - Affects  
'glProjectionMatrix' matrix only.  
  
The optionally returned 'glProjectionMatrix', based on these parameters, can be  
used as [OpenGL](OpenGL) GL\_PROJECTION\_MATRIX to render 3D objects superimposed and  
aligned with the markers in the video input image from the camera, for  
debugging, diagnostics, or AR / mixed reality applications.  
  


###See also:
[AprilDetectMarkers](PsychCV-AprilDetectMarkers)
