# [LoadShaderFromFile](LoadShaderFromFile)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

handle = [LoadShaderFromFile](LoadShaderFromFile)(filename [, shadertype] [, debug=0])  
  
Loads a GLSL [OpenGL](OpenGL) shader definition from textfile 'filename' and  
creates an [OpenGL](OpenGL) GLSL shader of type 'shadertype'. Returns a handle to  
the new shader. If shadertype is omitted, the type of the shader is  
derived from the filename extension: .vert == GL\_VERTEX\_SHADER, .frag ==  
GL\_FRAGMENT\_SHADER, .geom == GL\_GEOMETRY\_SHADER, .tesscontrol =  
GL\_TESS\_CONTROL\_SHADER, .tesseval = GL\_TESS\_EVALUATION\_SHADER. The  
optional 'debug' flag allows to enable debugging output.  
  
The optional 'debug' flag allows to enable debugging output:  
Zero = no output, 1 = a bit of output, 2 = detailed output,  
3 = Don't compile and link anymore, but print out the shaders  
source code as [OpenGL](OpenGL) would see it.  
  
On successfull load & creation, a 'handle' to the new shader is returned.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/LoadShaderFromFile.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/LoadShaderFromFile.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/LoadShaderFromFile.m</code>
</div>

