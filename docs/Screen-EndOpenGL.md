# [Screen('EndOpenGL')](Screen-EndOpenGL) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('EndOpenGL', windowPtr);

Finish [OpenGL](OpenGL) rendering by external [OpenGL](OpenGL) code, prepare 2D drawing into window  
'windowPtr'.  
This is the counterpart to [Screen](Screen)('BeginOpenGL'). Whenever you used  
[Screen](Screen)('BeginOpenGL') to enable external [OpenGL](OpenGL) drawing from Matlab, you \*must\*  
call [Screen](Screen)('EndOpenGL') when you're finished with a window, either because you  
want to draw into a different window, or you want to use a [Screen](Screen) command.  
Psychtoolbox will abort your script if you omit this command.   


###See also:
[BeginOpenGL](Screen-BeginOpenGL) [SetOpenGLTexture](Screen-SetOpenGLTexture) [GetOpenGLTexture](Screen-GetOpenGLTexture) moglcore
