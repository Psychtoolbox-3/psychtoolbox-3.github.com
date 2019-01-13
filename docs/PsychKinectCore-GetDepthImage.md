# [PsychKinectCore('GetDepthImage')](PsychKinectCore-GetDepthImage) 
##### [Psychtoolbox](Psychtoolbox)>[PsychKinectCore](PsychKinectCore).{mex*} subfunction


Return the depth image data for the frame fetched via 'GrabFrame'.  
  
If 'returnTexturePtr' is zero (default), a matrix is returned for processing in  
Matlab/Octave.  
  
If 'returnTexturePtr' is one, a memory pointer to a buffer is returned.  
  
'format' defines the type of returned data:  
0 = Return raw disparity image as 2D double matrix with integral values.  
1 = Return depths z-image as 2D double matrix with z-distance in meters.  
2 = Return a vertex buffer with (x,y,z) vertices that define a 3D surface mesh  
    and (R,G,B) color values for each vertex. -\> [x,y,z,r,g,b] per element.  
3 = Return a vertex buffer with (x,y,z) vertices that define a 3D surface mesh.  
    and (tx,ty) texture coordinates for vertices -\> [x,y,z,tx,ty] per element.  
4/5 = Return a vertex buffer with (xi,yi,z) vertices that define sensor pixel  
      position (xi,yi) of depths sensor and reconstructed z value. This needs  
      to be post-processed in a vertex shader for speedups.  
6/7 = Return a vertex buffer with vertex id's uniquely identifying each sensor   
      position of depths sensor and raw sensor value at that location. The whole  
      3D reconstructin is done on the GPU in a vertex shader for maximum speed.  
8   = Return a uint16 buffer with a transposed copy of the raw depth buffer.  
      This is the most compact and efficient way to return raw data to you. The  
      transposed format is again for efficiency reasons. You need to transpose()  
      the returned 2D data matrix yourself.  
      Alternatively return a memory pointer to the 16 bit unsigned integer raw  
      depth buffer. CAUTION: The pointer becomes invalid as soon as the  
      current buffer is released via 'ReleaseFrame'! This is the fast-path.  
        
  
  


###See also:

