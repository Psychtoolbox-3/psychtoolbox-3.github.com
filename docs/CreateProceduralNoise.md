# [CreateProceduralNoise](CreateProceduralNoise)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[noiseid, noiserect] = [CreateProceduralNoise](CreateProceduralNoise)(windowPtr, width, height [, noiseType='ClassicPerlin'][, backgroundColorOffset =(0,0,0,0)][, param1][, param2, ...])  
  
Creates a procedural texture that allows to draw random noise stimulus patches  
in a very fast and efficient manner on modern graphics hardware.  
  
This works on GPU's with support for the [OpenGL](OpenGL) shading language and  
vertex- and fragment shaders. See [ProceduralNoiseDemo](ProceduralNoiseDemo) for examples on how to use this function.  
  
  
### Parameters and their meaning:  
  
'windowPtr' A handle to the onscreen window.  
  
  
'width' x 'height' The maximum 2D size (in pixels) of the noise patch.  
  
  
'noiseType' Name of the noise function to use, defaults to 'ClassicPerlin'.  
The following types of noise are currently supported:  
  
- 'Perlin': Generates Perlin noise, which is approximately gaussian  
            distributed.  
  
- 'ClassicPerlin': Like Perlin, but with the classic implementation.  
  
  
'backgroundColorOffset' Optional, defaults to [0 0 0 0]. A RGBA offset  
color to add to the final RGBA colors of the drawn gabor, prior to  
drawing it.  
  
  
'param1' ... 'paramN' - Parameters specific to the noise function.  
  
  
The function returns a procedural texture handle 'noiseid' that you can  
pass to the [Screen](Screen)('DrawTexture(s)', windowPtr, noiseid, ...) functions  
like any other texture handle. The 'noiserect' is a rectangle which  
describes the size of the noise texture support.  
  
### A typical invocation to draw a single noise patch may look like this:  
  
[Screen](Screen)('DrawTexture', windowPtr, noiseid, [], dstRect, [], [], [],  
modulateColor, [], [], [contrast, seed, 0, 0]);  
  
Draws the patch 'noiseid' into window 'windowPtr', at position 'dstRect',  
or in the center if 'dstRect' is set to []. Make sure 'dstRect' has the  
size of 'noiserect' to avoid spatial distortions! You could do, e.g.,  
dstRect = [OffsetRect](OffsetRect)(noiserect, xc, yc) to place the patch centered at  
screen position (xc,yc).  
  
  
'modulateColor' is the base color of the noise patch - it defaults to  
white, ie. the noise has only luminance, but no color. If you'd set it to  
[255 0 0] you'd get a reddish noise.  
  
  
'contrast' is the amplitude of your patch in intensity units - A factor  
that is multiplied to the random number before converting the  
value into a color value. 'contrast' may be a bit of a misleading term  
here...  
  
'seed' Defines the random seed for drawing of a pseudo-random patch.  
  
Make sure to use the [Screen](Screen)('DrawTextures', ...); function properly,  
instead of the [Screen](Screen)('DrawTexture', ...); function, if you want to draw  
many different patches simultaneously - this is much faster!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralNoise.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralNoise.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateProceduralNoise.m</code>
</div>

