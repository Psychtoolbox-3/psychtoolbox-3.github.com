# [CreateGLOperator](CreateGLOperator)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

gloperator = [CreateGLOperator](CreateGLOperator)(windowPtr [, imagingmode] [, shaderhandle] [, opname] [,..shader options])  
  
Creates an image processing operator for use with the [Screen](Screen)('TransformTexture')  
function (to be passed as 'transformProxy' argument) and returns  
a handle 'gloperator' to it. The operator should be destroyed via [Screen](Screen)('[Close](Close)', gloperator);  
when its not needed anymore. It gets automatically disposed when its associated onscreen window is closed.  
  
'windowPtr' is the window handle of the parent onscreen window.  
'imagingmode' (optional) to set a specifc combination of imaging flags  
that affect how this operator works. Most useful flags are:  
kPsychNeedDualPass if this operator should contain exactly two  
operations, e.g., if it defines a separable convolution which consists of  
two 1-D convolution passes, or kPsychNeedMultiPass if this operator should  
contain more than two operations. Also useful are kPsychNeed16BPCFloat or  
kPsychNeed32BPCFloat if you expect results of the operator to be signed  
or to require floating point resolution. You can use 'mor' to combine  
multiple of these flags, e.g., mor(kPsychNeedDualPass,kPsychNeed32BPCFloat)  
to create an operator suitable for high precision processing with  
possibly signed results and two processing passes.  
  
If you want to immediately assign a single image processing operation,  
you can do so by assigning an [OpenGL](OpenGL) GLSL shader 'shaderhandle'. You can  
give this shader an unique name 'opname' (for debugging purpose) and  
provide possible additional arguments for it.  
  
If you want to add multiple operations to the operator, you can use the  
[AddToGLOperator](AddToGLOperator)() command.  
  
[GLOperators](GLOperators) can also get assigned to the builtin stimulus post-processing  
pipeline if they should affect all created visual stimuli. See 'help  
PsychImaging' - the section about 'AddGLOperator'  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateGLOperator.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateGLOperator.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateGLOperator.m</code>
</div>

