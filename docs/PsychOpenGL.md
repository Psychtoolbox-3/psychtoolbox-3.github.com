# [PsychOpenGL](PsychOpenGL)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

[PsychOpenGL](PsychOpenGL) -- [OpenGL](OpenGL) support for Matlab.  
  
Psychtoolbox allows you to directly call low-level [OpenGL](OpenGL) commands from  
the Matlab environment in nearly the same way as you could do from native  
C or C++ code. This way you can code and use image manipulation  
algorithms and 3D graphics algorithms in Matlab, utilizing the power of  
modern graphics hardware by calling [OpenGL](OpenGL) functions.  
  
Access to [OpenGL](OpenGL) from Matlab is provided by the "Matlab [OpenGL](OpenGL) toolbox"  
(MOGL), whose original OS/X version was developed, implemented and  
contributed to Psychtoolbox under the MIT license by Prof. Richard F.  
Murray, University of York, Canada. (The code was under GPL license until  
2010, but has been relicensed to the more permissive MIT license in 2011).  
  
MOGL provides one Matlab wrapper M-File for each corresponding [OpenGL](OpenGL)  
function. The wrapper file calls into a special MEX file (moglcore) which  
implements the C-language interface to [OpenGL](OpenGL). The syntax of a Matlab  
[OpenGL](OpenGL) command is mostly identical to its C counterpart with a few  
small exceptions that are imposed to us by the design of Matlab:  
  
1. Return values are returned in Matlab-style, as left-hand side  
arguments of the calls, instead of being right-hand side arguments as in  
C:  
  
E.g., the C language call glGetIntegerv[(GLenum]((GLenum) pname, [GLint](GLint)\* params);  
becomes params = glGetIntegerv(pname); in Matlab, because 'params' is a  
return argument of glGetIntegerv.  
  
2. Commands that don't take arguments don't have empty braces, because  
Matlab doesn't allow this:  
  
E.g., the C language call glEnd();  becomes glEnd; in Matlab.  
  
3. All GL, GLU and AGL constants start with prefix GL. instead of GL\_  
E.g., GL\_RGB becomes GL.RGB, GL\_DEPTH\_TEST becomes GL.DEPTH\_TEST, ...  
  
Each subroutine that intends to use GL constants needs to define the  
variable GL as global: Example  
  function myOpenGLSubroutine()  
  global GL; % Define GL variable as global.  
  ...rest of function implementation...  
  return;  
  
If you want to use GLU constants, then 'global GLU' is also needed.  
  
4. In your main Matlab script or M-File you need to call the function  
[InitializeMatlabOpenGL](InitializeMatlabOpenGL);  \*before\* calling [Screen](Screen)('OpenWindow', ...) the  
first time. This command initializes the [OpenGL](OpenGL) for Matlab toolbox and  
sets up Psychtoolbox to play nicely with Matlab-[OpenGL](OpenGL) and other [OpenGL](OpenGL)  
toolboxes. Psychtoolbox will then attach a 24-bit depth buffer (z-buffer)  
and a 8-bit stencil buffer to each onscreen window, so occlusion handling  
works properly when rendering 3D-Stimuli.  
  
Please note that [InitializeMatlabOpenGL](InitializeMatlabOpenGL)() allows to optionally set the  
'debuglevel', the amount of error checking automatically performed during  
execution of your scripts. By default, the debug level is set so that  
MOGL checks for [OpenGL](OpenGL) errors after execution of each single [OpenGL](OpenGL) call!  
This is nice for debugging code, but can significantly impact performance  
for complex rendering code! Make sure to explicitely set the debuglevel  
to '0' once your experiment code is performing as expected, so you can  
get higher rendering performance.  
  
  
Each time after calling a Psychtoolbox [Screen](Screen)() command for 2D drawing,  
you need to call [Screen](Screen)('BeginOpenGL', window); to tell PTB that you want  
to use [OpenGL](OpenGL) code to draw into onscreen- or offscreen-window 'window',  
so PTB can set up the window properly for your [OpenGL](OpenGL) code. Each time  
after you've finished drawing with [OpenGL](OpenGL) commands and you want to draw  
with PTB again, you'll need to call [Screen](Screen)('EndOpenGL', window), so PTB  
can switch back to its own drawing engine.  
  
Psychtoolbox provides two [Screen](Screen) subfunctions that allow you to either  
use Psychtoolbox textures in your own [OpenGL](OpenGL) code or to inject your own  
self-made [OpenGL](OpenGL) textures into Psychtoolbox for use with  
[Screen](Screen) Drawingcommands. See the [Screen](Screen) online help with...  
  
[Screen](Screen) [SetOpenGLTexture](SetOpenGLTexture)?  
[Screen](Screen) [GetOpenGLTexture](GetOpenGLTexture)?  
  
... for how to use these functions.  
This allows you to conveniently upload images into PTB with the usual  
img=imread(filename); tex=[Screen](Screen)('MakeTexture', win, img) methods and  
then use the texture in your [OpenGL](OpenGL) drawing code. It also allows you to  
access the images of Quicktime movies and images captured by the video  
capture functions in your [OpenGL](OpenGL) code.  
  
We also provide a couple of higher-level functions, implemented as M-Files  
to solve common tasks:  
  
\* [LoadOBJFile](LoadOBJFile)()  -- This implements a simple loader for Alias/Wavefront  
OBJ geometry files. Most common 3D graphics applications (e.g, Blender,  
Maya, 3D-Studio-Max, ...) allow you to export 3D objects and scenes as files  
in ASCII-OBJ format. [LoadOBJFile](LoadOBJFile)() allows you to load such files into  
Matlab. See 'help LoadOBJFile' for usage info. The loader is pretty  
limited at the moment, so read the file carefully to understand its  
limitations!  
  
\* moglDrawDots3D() -- High speed drawing of 3D dots or points, similar to  
[Screen](Screen)('DrawDots') for the 2D case.  
  
\* [moglmorpher](moglmorpher)()  -- A high-speed shape rendering and morphing function.  
[moglmorpher](moglmorpher) allows to quickly draw (=render) single 3D objects loaded by  
[LoadOBJFile](LoadOBJFile)(). It also allows you to load a collection of shapes and  
quickly morph them into each other by linear combination of their shape-  
and surface-normal vectors. This is mostly useful for 3D facial animation  
and face morphing (face perception studies) and for high-level 3D object  
recognition tasks. Have a look at [MorphDemo](MorphDemo) for a nice example of how to  
use [LoadOBJFile](LoadOBJFile) and [moglmorpher](moglmorpher). This demo was contributed by Quoc, C.  
Vuong, MPI for Biological Cybernetics Tuebingen, Germany.  
  
\* [LoadShaderFromFile](LoadShaderFromFile)() and [LoadGLSLProgramFromFiles](LoadGLSLProgramFromFiles)() -- These functions  
allow to load [OpenGL](OpenGL) GL Shading language (GLSL) shader definition files  
from the filesystem and to create GLSL shaders from them. When used  
properly, one can implement very complex lighting models and a host of  
image processing operations directly on the graphics hardware. This can  
provide speed gains anywhere from 10 to 1000 times faster than when  
executing such algorithms on the CPU. Have a look at [GLSLDemo](GLSLDemo) for some  
example of how to use GLSL shaders. Use of GLSL shaders requires state of  
the art graphics hardware, so if you don't have a recent graphics adapter  
installed in your machine, these demos and functions may fail.  
  
\* moglFDF() -- A high-speed renderer for "formless dot fields", random  
dot field motion stimuli for the creation of "structure from motion"  
stimuli from 3D objects.  
  
More high-level functions will follow...  
  
For demos on how to code [OpenGL](OpenGL) in Matlab, have a look at the demos in  
'Psychtoolbox/[PsychDemos](PsychDemos)/[OpenGL4MatlabDemos](OpenGL4MatlabDemos)/'  
  
### Support for 3rd party [OpenGL](OpenGL) MEX-Files:  
  
You can also code up [OpenGL](OpenGL) algorithms in the C programming language and  
compile them into Matlab-MEX files if you have "need for speed". Your Mex  
files will just contain the mixture of ANSI C code and [OpenGL](OpenGL) calls, but  
no code to setup the window, [OpenGL](OpenGL) rendering context, or to flip the  
front- and backbuffers. Psychtoolbox takes care of setting up [OpenGL](OpenGL) and  
windows for you. You just need to call the [InitializeMatlabOpenGL](InitializeMatlabOpenGL);  
function at the beginning of your script and wrap each invocation of your  
mex-file into [Screen](Screen)('BeginOpenGL', win) and [Screen](Screen)('EndOpenGL',win)  
calls. Use the [Screen](Screen)('[Flip](Flip)', win) command as usual to take care of  
stimlulus onset.  
  
If you want to write [OpenGL](OpenGL) mex-files that are portable across different  
operating systems (OS-X, Windows, Linux) then have a look at:  
'Psychtoolbox/[PsychOpenGL](PsychOpenGL)/MOGL/source' for how to do this. This folder  
contains the source code and Makefiles for our own moglcore mex-file...  
  
### KNOWN LIMITATIONS:  
  
If you use many immediate mode [OpenGL](OpenGL) rendering calls, rendering speed in  
Matlab may be significantly lower than when executing the same code from  
C or C++. This is the price you'll have to pay for using Matlab. However,  
immediate mode rendering is discouraged even in C for anything but the  
most trivial tasks, it's just that you pay a slightly higher "time  
penalty" for doing the wrong thing in Matlab than in C. Well written code  
will not cause any significant performance difference to C.  
  
Some [OpenGL](OpenGL) functions are not yet implemented in the toolbox, because  
these functions can't get automatically generated, so their wrappers need  
to be coded manually. Our goal is to provide full support for the  
[OpenGL](OpenGL)-API but finalizing all functions may take some time. Mostly some  
of the query-functions - functions that don't set [OpenGL](OpenGL) state or execute  
some operation, but query the current settings of [OpenGL](OpenGL), are missing.  
  
Also, some of the more exotic [OpenGL](OpenGL) extensions are not yet supported,  
especially there is no support for old-style Vertexprograms and  
Fragmentprograms, but GLSL vertexshaders and fragmentshaders are a  
complete - and easier to use - replacement for these.  
  
Apart from these limitations that will get removed in the future, there  
are limitations imposed by your operating system and graphics hardware.  
Support for [OpenGL](OpenGL) functions varies between different graphics hardware,  
so if you want to use the latest and greatest [OpenGL](OpenGL) functions, you'll  
need to buy and install the latest and greatest graphics hardware.  
  
### CONTENTS:  
  
\* All supported [OpenGL](OpenGL) low-level functions can be found in the folder  
'Psychtoolbox/[PsychOpenGL](PsychOpenGL)/MOGL/wrap/'. Functions prefixed with \_ are not  
yet implemented.  
  
\* A number of interesting GLSL shaders for realtime image processing can  
be found in 'Psychtoolbox/[PsychOpenGL](PsychOpenGL)/[PsychGLSLShaders](PsychGLSLShaders)/'. These may only work on  
state of the art graphics hardware.  
  
\* High-level helper functions (e.g., OBJ file loading, morphing, ...) can  
be found in 'Psychtoolbox/[PsychOpenGL](PsychOpenGL)/' and its subfolders.  
  
\* Demos can be found in 'Psychtoolbox/[PsychDemos](PsychDemos)/OpenGL4MatlabDemos'  
  
Lot's of documentation, tutorials, code samples and news about [OpenGL](OpenGL) can  
be found at:  
  
http://www.opengl.org  
  
Enjoy!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/Contents.m</code>
</div>

{{category}}