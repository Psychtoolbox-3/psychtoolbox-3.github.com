# [Screen('glPushMatrix')](Screen-glPushMatrix) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('glPushMatrix', windowPtr);

Store a backup copy of active current [OpenGL](OpenGL) matrix on the matrix stack for  
later reuse. The capacity of the matrix backup stack is limited, typically not  
more than 27 slots. For each call to glPushMatrix you need to call glPopMatrix  
at the appropriate place to avoid overflowing the stack. See  
<http://www.opengl.org/documentation/red\_book\_1.0/\> Chapter 4 for detailed  
information.  


###See also:

