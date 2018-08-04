# [Screen('BeginOpenGL')](Screen-BeginOpenGL) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Prepare window 'windowPtr' for [OpenGL](OpenGL) rendering by external [OpenGL](OpenGL) code. This  
allows to use [OpenGL](OpenGL) drawing routines other than the ones implemented in  
[Screen](Screen)() to draw to a Psychtoolbox onscreen- or offscreen window via execution  
of [OpenGL](OpenGL) commands. Typical clients of this function are mogl (Richard F.  
Murrays [OpenGL](OpenGL) for Matlab wrapper), the new Eyelink-Toolbox and third party  
Matlab Mex-Files which contain [OpenGL](OpenGL) rendering routines. You \*have to\* call  
this command once before using any of those external drawing commands for the  
window. After drawing, you \*must\* switch back to PTB's rendering via the  
[Screen](Screen)('EndOpenGL', windowPtr); command. Normally, you won't provide the  
optional flag 'sharecontext', so PTB will automatically isolate the [OpenGL](OpenGL) state  
of your code from its internal state. However, if you provide sharecontext=1,  
then PTB will allow your code to use and affect [PTBs](PTBs) internal context. Only do  
this if you really know what you're doing! If you provide sharecontext=2 then  
PTB will give you your own private context, but it will synchronize the state of  
that context with its internal state - Seldomly needed, but here for your  
convenience. Caution: sharecontext=2 is not supported on all operating systems  
and gpu's, e.g., not on OSX, so avoid if you can! The context state isolation is  
as strict as possible without seriously affecting performance and functionality:  
All [OpenGL](OpenGL) context state is separated, with two exceptions: The framebuffer  
binding (if any) is always synchronized with PTB (and reset to zero when calling  
'EndOpenGL' or another [Screen](Screen) command) to allow external code to transparently  
render into [PTBs](PTBs) internal framebuffers - Needed for the imaging pipeline to  
work. Ressources like textures, display lists, [FBOs](FBOs), [VBOs](VBOs), [PBOs](PBOs) and GLSL shaders  
are shared between PTB and your code as well for efficiency reasons. Both types  
of ressource sharing shouldn't be a problem, because either you are a beginner  
or advanced [OpenGL](OpenGL) programmer and won't use those facilities anyway, or you are  
an expert user - in which case you'll know how to prevent any conflicts easily.  


###See also:
[EndOpenGL](Screen-EndOpenGL) [SetOpenGLTexture](Screen-SetOpenGLTexture) [GetOpenGLTexture](Screen-GetOpenGLTexture) moglcore
