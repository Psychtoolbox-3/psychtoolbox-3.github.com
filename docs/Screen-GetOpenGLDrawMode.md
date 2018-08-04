# [Screen('GetOpenGLDrawMode')](Screen-GetOpenGLDrawMode) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Return information about current [OpenGL](OpenGL) rendering state.  
'targetwindow' is the window handle of the window that is currently enabled for  
drawing. That is, the last window a [Screen](Screen) drawing command was drawing to, or  
the window which is the current target for [OpenGL](OpenGL) rendering commands.  
'IsOpenGLRendering' if equal to zero, then normal 2D [Screen](Screen) drawing is active.  
If greater than zero, then Matlab [OpenGL](OpenGL) drawing is active, ie. a  
[Screen](Screen)('BeginOpenGL'); command was executed and [OpenGL](OpenGL) code can draw into  
'targetwindow'.   


###See also:
[BeginOpenGL](Screen-BeginOpenGL) [EndOpenGL](Screen-EndOpenGL) [SetOpenGLTexture](Screen-SetOpenGLTexture) [GetOpenGLTexture](Screen-GetOpenGLTexture) moglcore
