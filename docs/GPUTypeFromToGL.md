# [GPUTypeFromToGL](GPUTypeFromToGL)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGPGPU](PsychGPGPU)

outObj = [GPUTypeFromToGL](GPUTypeFromToGL)(cmd, inObj [, glObjType][, outObj][, keepmapped][, mapflags])  
  
Note: Calling this command requires calling the following command first  
to initialize Psychtoolbox GPU computing support:  
  
[PsychImaging](PsychImaging)('AddTask', 'General', 'UseGPGPUCompute', 'GPUmat');  
  
# Supported 'cmd' commands  
  
if cmd is zero, then convert an [OpenGL](OpenGL) object of type glObjType,  
referenced by handle inObj into a GPU object and return it in outObj. If  
the optional outObj is provided as input argument, try to recycle it --  
just fill its content with [OpenGL](OpenGL) object's content. Otherwise, create an  
outObj of matching format for content. If 'keepmapped' is set to 1, the [OpenGL](OpenGL)  
object will stay mapped for the GPU compute api, otherwise it gets immediately  
unmapped after the conversion. Keeping the object mapped is more efficient, but  
requires more careful management of objects to prevent malfunctions.  
  
If cmd is == 1, then convert GPU object inObj to [OpenGL](OpenGL) object of type  
glObjType and return it in outObj. Try to recycle a passed in outObj, if  
possible, otherwise create a new one. 'keepmapped' - see explanation for cmd zero.  
  
If cmd is == 2, then unmap the [OpenGL](OpenGL) object. You must do this if you previously  
set the optional 'keepmapped' flag to 1 during a copy operation and now want to  
use the object which was the source or the target of that copy again with [OpenGL](OpenGL)  
or [Screen](Screen)(), ie., with a Psychtoolbox drawing or image processing function.  
Unmapping is neccessary for proper [OpenGL](OpenGL) operation, but costs a fraction of a  
millisecond of overhead on well working operating systems like Linux. Clever use  
of the 'keepmapped' flag and this manual unmapping method sometimes allows to  
save some redundant unmap calls.  
  
If cmd is == 3, then remove the [OpenGL](OpenGL) object from use by the GPU compute toolkit.  
This must be done before destroying/deleting the [OpenGL](OpenGL) object, e.g., before  
a call to [Screen](Screen)('[Close](Close)', x); for a window or texture handle x. This operation  
can be very expensive -- on the order of multiple milliseconds, so use sparingly.  
  
If cmd is == 4, all [OpenGL](OpenGL) objects are removed. Usually used before closing (all)  
onscreen windows, e.g., via [Screen](Screen)('CloseAll') or [sca](sca). This cache flush is very  
expensive!  
  
If cmd is == 5, then the given [OpenGL](OpenGL) object 'inObj' of type glObjType is mapped  
and a CUDA memory pointer is returned, for use with external mex files, so these  
can directly access the mapped resource. The object is mapped read-only.  
  
If cmd is == 6, the same operation as cmd == 5 happens, but the object is mapped  
write-only.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGPGPU/GPUTypeFromToGL.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGPGPU/GPUTypeFromToGL.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGPGPU/GPUTypeFromToGL.m</code>
</div>

