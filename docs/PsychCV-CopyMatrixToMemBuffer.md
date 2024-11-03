# [PsychCV('CopyMatrixToMemBuffer')](PsychCV-CopyMatrixToMemBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[PsychCV](PsychCV).{mex*} subfunction

PsychCV('CopyMatrixToMemBuffer', matrix, memBufferPtr);

Copies a Matlab/Octave uint8 or double matrix 'matrix' into a C memory buffer,  
whose memory (void\*) pointer is encoded as a double scalar value 'memBufferPtr'.  
The target buffer must be of sufficient size, no checking is performed! This is  
essentially a C memcpy() operation, so use with caution, or Matlab/Octave will  
crash!  


###See also:

