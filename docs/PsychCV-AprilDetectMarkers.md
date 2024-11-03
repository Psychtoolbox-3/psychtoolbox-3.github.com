# [PsychCV('AprilDetectMarkers')](PsychCV-AprilDetectMarkers) 
##### [Psychtoolbox](Psychtoolbox)>[PsychCV](PsychCV).{mex*} subfunction

[detectedMarkers] = PsychCV('AprilDetectMarkers'[, markerSubset=all][, infoType=all]);

Detect apriltags in the current video image, return information about them.  
  
Analyzes the current video image, stored in the internal input image buffer, and  
tries to detect the apriltag markers in them. For all detected tags, their 2D  
center, their 2D corners, and their 3D position and orientation is computed,  
using the provided camera calibration. The return argument 'detectedMarkers' is  
an array of structs, with one struct for each successfully detected tag. The  
struct contains info about the identity of the tag, confidence values for the  
reliability of detection, and the estimated 6-[DoF](DoF) 3D position and 3D pose of the  
marker tag in 3D space, relative to the cameras reference frame and origin.  
Please note that, in general, 3D pose estimates are not as reliable and accurate  
as the 2D detection of markers. Furthermore, the 3D orientation of the marker is  
way less well defined and accurate than the 3D position of the markers center.  
Often the estimated 3D orientation may be outright rubbish!  
You can use [PsychCV](PsychCV)('AprilSettings'); to tune various parameters related to the  
2D marker detection, including the use of multiple processing threads for higher  
performance.  
For 6-[DoF](DoF) 3D estimation, you need to provide camera intrinsic parameters and the  
size of the tags via [PsychCV](PsychCV)('April3DSettings').  
If you don't want to detect all tags, but only a subset, then pass a list of  
candidate tag id's via the list 'markerSubset', to reduce your codes complexity  
and computation time.  
To further reduce computation time, you can ask for only a subset of information  
by providing 'infoType'. By default all information is returned at highest  
quality and robustness with longest computation time:  
- 2D marker detection data is always returned.  
- A value of +1 will return 3D pose.  
Omitting the value +1 from 'infoType' will avoid 3D pose estimation.  
  
The returned structs contain the following fields:  
'Id' The decoded apriltag id. Hamming code error correction is used for  
decoding.  
'MatchQuality' A measure of the quality of the binary decoding process. This is  
what the apriltag library calls decision\_margin. Higher numbers roughly indicate  
better decodes. It is a reasonable measure of detection quality only for small  
tags, mostly meaningless for bigger tags.  
'HammingErrorBits' Number of error bits corrected. Smaller numbers are better.  
'Corners2D' A 2-by-4 matrix with the 2D pixel coordinates of the detected  
corners of the tag in the input image, each column representing one corner [x ;  
y]. These always wrap counter-clock wise around the tag.  
'Center2D' A vector with the 2D pixel coordinates of the estimated center of the  
tag in the input image.  
'PoseError' If 3D pose estimation was used, the object space error of the  
returned pose.  
'T' A 3-component [x ; y; z] translation vector which encodes the estimated 3D  
location of the center of the tag in space, in units of meters, relative to the  
origin of the camera.  
'R' A 3x3 rotation matrix, encoding the estimated pose of the tag, relative to  
the cameras reference frame. Convention is that the tag itself lies in the x-y  
plane of its local reference frame, and the positive z-axis sticks out of the  
tags surface like a surface normal vector.  
'TransformMatrix' A 4x4 transformation matrix representing position and  
orientation all in one, for convenience. Simply the product [TransformMatrix](TransformMatrix) = T  
\* R, extended to a 4x4 format. This represents pose relative to the cameras  
origin, x-axis to the right, y-axis down, z-axis along the looking direction aka  
optical axis.  
'ModelViewMatrix' A 4x4 RHS transformation matrix, directly usable for 3D [OpenGL](OpenGL)  
rendering of objects in the tags local reference frame. It can be used directly  
as GL\_MODELVIEW\_MATRIX for rendering 3D content on top of the tag in the video  
image, or right-multiplied to the active GL\_MODELVIEW\_MATRIX to represent the  
tags 6 [DoF](DoF) pose relative to the 3D [OpenGL](OpenGL) cameras origin. You need to use the  
GL\_PROJECTION\_MATRIX returned by matrix = [PsychCV](PsychCV)('April3DSettings'); for  
rendering superimposed to images from the camera that captured the april tags.  
This matrix is a rotated version of 'TransformMatrix', rotated 180 degrees  
around the x-axis for [OpenGL](OpenGL) compatibility, as apriltag has x-axis to the right,  
y-axis down, z-axis along optical looking direction axis, whereas [OpenGL](OpenGL) has its  
x-axis to the right, y-axis up, and the negative z-axis along optical looking  
direction axis / viewing direction, ie. 180 degrees rotated.  
  


###See also:
[AprilInitialize](PsychCV-AprilInitialize) [AprilSettings](PsychCV-AprilSettings) [April3DSettings](PsychCV-April3DSettings)
