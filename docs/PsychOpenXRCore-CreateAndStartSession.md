# [PsychOpenXRCore('CreateAndStartSession')](PsychOpenXRCore-CreateAndStartSession) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

videoRefreshDuration = PsychOpenXRCore('CreateAndStartSession', openxrPtr, deviceContext, openGLContext, openGLDrawable, openGLConfig, openGLVisualId, use3DMode, multiThreaded [, srcTexIds]);

Create, initialize and start XR session for [OpenXR](OpenXR) device 'openxrPtr'.  
The following parameters are needed to setup [OpenGL](OpenGL) <=\> [OpenXR](OpenXR) interop. They  
define the [OpenGL](OpenGL) context which will be used to share to-be-displayed image  
textures, and its configuration, either using X11/GLX/[XLib](XLib) on Linux, or Win32  
windowing on Windows:  
'deviceContext' OS specific device context: A X11 X-Server Display\* on Linux,  
the HDC used for WGL context creation on Windows.  
'openGLContext' The [OpenGL](OpenGL) context handle, a [GLXContext](GLXContext) on Linux/X11/GLX, or a  
HGLRC for Windows WGL.  
'openGLDrawable' The [GLXDrawable](GLXDrawable) on Linux/X11/GLX, the HWND window handle on  
Windows.  
'openGLConfig' The [GLXFBConfig](GLXFBConfig) on Linux/X11/GLX, and zero (unused) on Windows.  
'openGLVisualId' The X11 visual id used for creating the [GLXFBConfig](GLXFBConfig) /  
[GLXDrawable](GLXDrawable) on Linux/X11/GLX, zero (unused) on Windows.  
'use3DMode' must be 0 if pure monoscopic or stereoscopic rendering is requested,  
or 1 to request full 3D perspective correct rendering, e.g., for 3D scenes via  
[OpenGL](OpenGL).  
'multiThreaded' if provided as non-zero value, will use an asynchronous  
presenter thread to try to improve stimulus presentation scheduling. A zero  
value means to not use such a thread, 1 on demand, and 2 permanently for the  
duration of the whole session.  
'srcTexIds' Optional texture and FBO handles of the [Screen](Screen)() finalizedFBO  
backing textures and FBO's, needed for some workarounds for deficiencies of some  
MS-Windows [OpenXR](OpenXR) runtimes in multi-threaded mode. It has the format 'srcTexIds'  
= [leftTex, rightTex, leftFbo, rightFbo]. The driver tries to use an efficient  
texture based method, but falls back to a FBO based method if needed. This is a  
slower fallback path that can only handle non-MSAA content. If omitted, this  
workaround will not be used, achieving potentially higher performance, but  
likely resulting in malfunctions or hangs or crashes on some Windows [OpenXR](OpenXR)  
runtimes.  
  
Returns the following information:  
'videoRefreshDuration' Video refresh duration in seconds of the XR display  
device if available. If the info can't be queried a fallback value of 0.011 secs  
for a 90 Hz refresh rate is returned as one of the most common values for  
consumer [HMDs](HMDs).  
  


###See also:
Open Close
