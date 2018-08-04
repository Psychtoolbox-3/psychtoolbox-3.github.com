# [PsychSound](PsychSound)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSound](PsychSound)

Psychtoolbox:[PsychSound](PsychSound) -- Psychtoolbox sound functions, based on [OpenAL](OpenAL)  
and [PsychPortAudio](PsychPortAudio).  
  
If you need "traditional" support for audio capture or output as most do,  
see "help [PsychPortAudio](PsychPortAudio)" and "help [InitializePsychSound](InitializePsychSound)" for info about  
our excellent [PsychPortAudio](PsychPortAudio) driver.  
  
If you need 3D spatialized sound output, read on!  
  
Psychtoolbox allows you to directly call low-level [OpenAL](OpenAL) commands from  
the Matlab environment in nearly the same way as you could do from native  
C or C++ code. This way you can code and use sound recording  
algorithms and 3D sound output algorithms in Matlab, utilizing the power of  
modern sound hardware by calling [OpenAL](OpenAL) functions.  
  
Access to [OpenAL](OpenAL) from Matlab is provided by the "Matlab [OpenAL](OpenAL) toolbox"  
(MOAL) which was derived from the MOGL toolbox for [OpenGL](OpenGL).  
  
[OpenAL](OpenAL) is a free (free software), cross-platform (Windows, Macintosh, Linux),  
highly efficient, easy to learn, flexible audio library which incorporates  
advanced features like 3D spatialized sound, multi-channel support, streaming,  
audio capture, special effects like echo, reverb, attenuation, doppler effects  
and other stuff. Its programming model and API closely resembles [OpenGL](OpenGL), so  
[OpenGL](OpenGL) programmers will find themselves immediatels at home with this library,  
and its very easy to extend 3D graphics code with corresponding 3D sound.  
  
MOAL provides one Matlab wrapper M-File for each corresponding [OpenAL](OpenAL)  
function. The wrapper file calls into a special MEX file (moalcore) which  
implements the C-language interface to [OpenAL](OpenAL). The syntax of a Matlab  
[OpenAL](OpenAL) command is mostly identical to its C counterpart with a few  
small exceptions that are imposed to us by the design of Matlab:  
  
1. Return values are returned in Matlab-style, as left-hand side  
arguments of the calls, instead of being right-hand side arguments as in  
C:  
  
E.g., the C language call alGetIntegerv[(GLenum]((GLenum) pname, [GLint](GLint)\* params);  
becomes params = alGetIntegerv(pname); in Matlab, because 'params' is a  
return argument of alGetIntegerv.  
  
2. Commands that don't take arguments don't have empty braces, because  
Matlab doesn't allow this:  
  
E.g., the C language call alEnd();  becomes alEnd; in Matlab.  
  
3. All AL, ALU and ALC constants start with prefix AL. instead of AL\_  
E.g., AL\_TRUE becomes AL.TRUE ...  
  
Each subroutine that intends to use AL constants needs to define the  
variable AL as global: Example  
  function myOpenALSubroutine()  
  global AL; % Define AL variable as global.  
  ...rest of function implementation...  
  return;  
  
If you want to use ALC constants, then 'global ALC' is also needed.  
  
4. In your main Matlab script or M-File you need to call the function  
[InitializeMatlabOpenAL](InitializeMatlabOpenAL); This command initializes the [OpenAL](OpenAL) for Matlab toolbox and  
sets up Psychtoolbox to play nicely with Matlab-[OpenAL](OpenAL) and other [OpenAL](OpenAL)  
toolboxes.  
  
  
### Support for 3rd party [OpenAL](OpenAL) MEX-Files:  
  
You can also code up [OpenAL](OpenAL) algorithms in the C programming language and  
compile them into Matlab-MEX files if you have "need for speed". Your Mex  
files will just contain the mixture of ANSI C code and [OpenAL](OpenAL) calls, but  
no code to setup the [OpenAL](OpenAL) rendering context. You just need to call the  
[InitializeMatlabOpenAL](InitializeMatlabOpenAL); function. After that call, an audio device will  
be set up and the associated [OpenAL](OpenAL) rendering context will be active. All  
commands in your MEX-File will apply to that rendering context.  
  
If you want to write [OpenAL](OpenAL) mex-files that are portable across different  
operating systems (OS-X, Windows, Linux) then have a look at:  
'Psychtoolbox/[PsychSound](PsychSound)/MOAL/source' for how to do this. This folder  
contains the source code and Makefiles for our own moalcore mex-file...  
  
### KNOWN LIMITATIONS:  
  
Depending on your specific code, rendering speed in Matlab may be  
slightly lower than when executing the same code from C or C++. This  
is the price you'll have to pay for using Matlab, but our abstraction  
layer is very thin, so most applications won't be really affected.  
  
Some [OpenAL](OpenAL) functions are not yet implemented in the toolbox, because  
these functions can't get automatically generated, so their wrappers need  
to be coded manually. Our goal is to provide full support for the  
[OpenAL](OpenAL)-API but finalizing all functions may take some time. Mostly some  
of the query-functions - functions that don't set [OpenAL](OpenAL) state or execute  
some operation, but query the current settings of [OpenAL](OpenAL), are missing.  
Also, some of the more exotic [OpenAL](OpenAL) extensions are not yet supported.  
  
Apart from these limitations that will get removed in the future, there  
are limitations imposed by your operating system and sound hardware.  
  
Support for [OpenAL](OpenAL) functions varies between different sound hardware,  
so if you want to use the latest and greatest [OpenAL](OpenAL) functions, you'll  
need to buy and install the latest and greatest sound hardware.  
  
Typical limitations of low-end versus high-end hardware:  
- Number of sound sources / channels that can be played back simultaneously.  
- Complexity of audio processing that can be performed.  
- Latency in sound processing.  
- Quality of 3D spatial audio rendering.  
  
### CONTENTS:  
  
\* All supported [OpenAL](OpenAL) low-level functions can be found in the folder  
  'Psychtoolbox/[PsychSound](PsychSound)/MOAL/wrap/'. Functions prefixed with \_ are not  
  yet implemented.  
  
\* High-level helper functions  can be found in 'Psychtoolbox/[PsychSound](PsychSound)/'  
  and its subfolders.  
  
\* Demos can be found in 'Psychtoolbox/[PsychDemos](PsychDemos)/SoundDemos'  
  
Lot's of documentation, tutorials, code samples and news about [OpenAL](OpenAL) can  
be found by following links at:  
  
http://www.openal.org  
  
Googling for [OpenAL](OpenAL) is also a option.  
  
Enjoy!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSound/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSound/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSound/Contents.m</code>
</div>

{{category}}