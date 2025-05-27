# [PsychOculusVRCore('GetUndistortionParameters')](PsychOculusVRCore-GetUndistortionParameters) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOculusVRCore](PsychOculusVRCore).{mex*} subfunction

[width, height, viewPx, viewPy, viewPw, viewPh, pptax, pptay, hmdShiftx, hmdShifty, hmdShiftz, meshVertices, meshIndices, uvScaleX, uvScaleY, uvOffsetX, uvOffsetY] = PsychOculusVRCore('GetUndistortionParameters', oculusPtr, eye [, inputWidth][, inputHeight][, fov]);

Return parameters needed for rendering and undistortion for Oculus device  
'oculusPtr'.  
'eye' which eye to provide the data: 0 = Left, 1 = Right.  
'inputWidth' = Width of the rendered input image buffer in pixels.  
'inputHeight' = Height of the rendered input image buffer in pixels.  
'fov' Optional field of view in degrees, from line of sight: [leftdeg, rightdeg,  
updeg, downdeg]. You can pass in the 'fovPort' value returned from  
[PsychOculusVR](PsychOculusVR)('GetFovTextureSize'); Defaults to whatever has been set for the  
given eye in the last call to [PsychOculusVR](PsychOculusVR)('GetFovTextureSize'); if omitted.  
  
Return values:  
[width, height] = Width and height of client renderbuffers in pixels. Same as  
the provided 'inputWidth' and 'inputHeight'.  
[viewPx, viewPy, viewPw, viewPh] Render viewport [x,y,w,h] start (x,y) position,  
width and height. Mostly useless atm., as viewPx and viewPy are always zero,  
viewPw and viewPh are identical to width and height in the current driver  
design.  
[pptax pptay] = Pixels per tangens angle at display center in x direction and y  
direction.  
[hmdShiftx, hmdShifty, hmdShiftz] = [HmdToEyeViewOffset](HmdToEyeViewOffset) 3D translation vector.  
Defines the location of the optical center of the eye relative to the origin of  
the local head reference frame, ie. the tracked head position.  
[meshVertices meshIndices] = Matrices with the definitions of the geometric  
undistortion triangle meshes. 'meshIndices' is a vector of 0-based indices into  
the vertex mesh 'meshVertices' for building a mesh out of triangles.  
'meshVertices' is a matrix with as many columns as mesh vertices, each column  
encoding one vertex. Each row encodes for one vertex property. See the Oculus  
developers manual for explanation of the format.  
[uvScaleX, uvScaleY, uvOffsetX, uvOffsetY] Scaling factors and offsets for  
texture coordinates in normalized device coordinates.  
  


###See also:
[GetFovTextureSize](PsychOculusVRCore-GetFovTextureSize)
