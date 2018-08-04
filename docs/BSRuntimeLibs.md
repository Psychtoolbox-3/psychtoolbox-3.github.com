# [BSRuntimeLibs](BSRuntimeLibs)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BrightSideDisplay](BrightSideDisplay)>[BSRuntimeLibs](BSRuntimeLibs)

Psychtoolbox:[PsychHardware](PsychHardware):[BrightSideDisplay](BrightSideDisplay):[BSRuntimeLibs](BSRuntimeLibs)  
  
This folder should contain the libraries and configuration files  
needed to build the [BrightSideCore](BrightSideCore).dll from its source and to  
actually use the DLL to interface PTB to a [BrightSide](BrightSide) High Dynamic  
Range Display device. Upon load time, the [BrightSideCore](BrightSideCore).dll will  
dynamically link against the libraries in this folder and read the  
configuration files needed for setting up the display.  
  
In a standard Psychtoolbox-3 installation, this folder won't contain  
any of the runtime and development libraries or headers, because we  
can not bundle them with PTB due to license restrictions.  
  
If you are the proud owner of such a display device, you will have  
a copy of the needed libraries and headers as part of the Software  
which is bundled with the display device. Just copy those runtime  
libraries and config files into this folder and you should be ready  
to use your display with PTB.  
  
# Dependencies on DLL libraries and other files on M$-Windows  
  
You must have the following libraries somewhere in your systems  
library search path, either by putting them into the subfolder  
outputlib/lib of this folder, or by putting them in a system default  
library folder to use the [BrightSideHDR](BrightSideHDR) with our precompiled mex file:  
  
GL\_OutputLibrary.dll -- From [BrightSide](BrightSide) software.  
[CoreLibrary](CoreLibrary)\_GL.dll   -- From [BrightSide](BrightSide) software.  
opengl32.dll         -- Part of your graphics driver installation.  
glew32.dll           -- From http://glew.sourceforge.net  
glut32.dll           -- From the source of the GLUT toolkit.  
cg.dll               -- From NVidia's Cg toolkit SDK:  
                        http://developer.nvidia.com/page/cg\_main.html  
cgGL.dll             -- From NVidia's Cg toolkit SDK.  
MSVCP71.dll          -- To be found in Psychtoolbox/[PsychContributed](PsychContributed)/[ARToolkitStuff](ARToolkitStuff)  
MSVCR71.dll  
  
Additionally in the subfolders...  
Resources/Textures  
Resources/[BlurCorrectionReference](BlurCorrectionReference)  
Resources/[DisplayConfiguration](DisplayConfiguration)  
Resources/[VertexShaders](VertexShaders)  
... you'll need the appropriate [BrightSide](BrightSide) files.  
  
You'll also need all header (includes) and .lib files from the [BrightSide](BrightSide)  
SDK if you want to rebuild the [BrightSideCore](BrightSideCore).cpp file into a MEX file,  
but this should be seldomly (if at all) needed:  
  
Subfolders:  
outputlib/include    -- For all the header files .h  
outputlib/lib        -- For all the .lib and .dll library files.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/BSRuntimeLibs/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/BSRuntimeLibs/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BrightSideDisplay/BSRuntimeLibs/Contents.m</code>
</div>

{{category}}