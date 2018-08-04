# [LoadGLSLProgramFromFiles](LoadGLSLProgramFromFiles)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

handle = [LoadGLSLProgramFromFiles](LoadGLSLProgramFromFiles)(filenames [, debug=0] [, extraShaders])  
Loads a GLSL [OpenGL](OpenGL) shading language program. All shader definition files in  
'filenames' are read, shaders are built for each definition and all  
shaders are linked together into a new GLSL program. Returns a handle to  
the new program, if successfull. The optional 'debug' flag allows to enable  
debugging output: Zero = no output, 1 = a bit of output, 2 = detailed  
output, 3 = Don't compile and link anymore, but print out the shaders  
source code as [OpenGL](OpenGL) would see it.  
  
The program can then be used at any time by calling glUseProgram(handle). One  
can switch back to the standard [OpenGL](OpenGL) fixed-function pipeline by calling  
glUseProgram(0). The same handles can be passed to the  
[Screen](Screen)('MakeTexture', ...), [Screen](Screen)('DrawTexture', ...); et al. routines  
to define procedural textures - or some processing operations on them  
via the  'textureShader' argument -- See 'help ProceduralShadingAPI' for  
more info about procedural texturing. The handle is also used to build  
[GLOperators](GLOperators) for [Screen](Screen)('TransformTexture') or as plugins for the imaging  
pipeline: See 'help CreateGLOperator' or 'help AddToGLOperator' for info.  
  
'filenames' can have one of two formats: If filenames is a array of  
strings that define the names of the shaders to use, then all shader  
files are loaded, compiled and linked into a single program. E.g.,  
shaderfiles={ 'myshader.vert' , 'myothershader.frag'}; will try to load  
the two shaderfiles myshader.vert and myothershader.frag and link them  
into a valid program.  
  
If only a single filename is given, then all shaders beginning with that  
name are linked into a program. E.g., shaderfiles = 'Phonglighting' will  
try to link all files starting with Phonglighting.  
  
The optional argument 'extraShaders' if present, should be a vector of  
additinal shader handles - Handles returned by the [LoadShaderFromFile](LoadShaderFromFile)()  
or by your self-compiled shaders via glCompileShader(). All precompiled  
shaders referenced by those handles get also linked into the final GLSL  
program.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/LoadGLSLProgramFromFiles.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/LoadGLSLProgramFromFiles.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/LoadGLSLProgramFromFiles.m</code>
</div>

