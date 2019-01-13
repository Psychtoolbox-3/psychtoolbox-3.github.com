# [Screen('BlendFunction')](Screen-BlendFunction) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[sourceFactorOld, destinationFactorOld, colorMaskOld]=Screen('BlendFunction', windowIndex, [sourceFactorNew], [destinationFactorNew], [colorMaskNew]);

Return or set the current alpha-blending mode and the color buffer writemask for  
window 'windowIndex'.  
Alpha blending is a way to combine color values of pixels already in the window  
with new color values from drawing commands. Alpha blending is disabled by  
default: If you overdraw some pixel location (x,y) in your window with a new  
source color value [Rs Gs Bs As], then the window location gets that color value  
assigned: I(x,y) = [Rs Gs Bs As]. However, [OpenGL](OpenGL) also allows you to combine  
such new color values with color values previously stored in that location. The  
old values are called destination colors [Rd Gd Bd Ad]. The way old and new  
destination and source colors are combined into new destination colors is called  
alpha-blending. Formally:  
New color at location (x,y) is [Rn Gn Bn An] = blendequation([Rs Gs Bs As], [Rd  
Gd Bd Ad]);  
 where blendequation is a function that describes how the new [Rs Gs Bs As]  
color values and previous old values [Rd Gd Bd Ad] should be combined. You can  
choose the 'blendequation' from a set of defined blend equations via choice of  
the 'sourceFactorNew' and 'destinationFactorNew' arguments. See help  
[PsychAlphaBlending](PsychAlphaBlending) and the help texts for the functions in that folder for  
possible choices of blend factors. The default setting of GL\_ONE, GL\_ZERO  
disables blending.  
The most common alpha-blending factors are sourceFactorNew = GL\_SRC\_ALPHA and  
destinationFactorNew = GL\_ONE\_MINUS\_SRC\_ALPHA They are needed for proper  
anti-aliasing (smoothing) by [Screen](Screen)('DrawLines'), [Screen](Screen)('DrawDots') and for  
drawing masked stimuli with the [Screen](Screen)('DrawTexture') command. See [DotDemo](DotDemo),  
[LinesDemo](LinesDemo), [AlphaImageDemo](AlphaImageDemo), [GazeContingentDemo](GazeContingentDemo) for a few applications of  
alpha-blending.  
  
This function also allows to return and set the color write mask for a window:  
You can prevent Psychtoolbox from drawing into and changing the content of one  
or more color channels by disabling the color channel for writing. This allows  
to perform drawing commands that only affect, e.g., the red chahnnel, but not  
the blue, green or alpha channel. You choose the channels by specification of  
the 'colorMaskNew' vector: The first element selects if writing to the red color  
channel are allowed (value greater than zero) or disallowed (value equal zero).  
The 2nd element selects the green channels state, the 3rd element selects the  
blue channels state and the 4th element selects the alpha channels state. E.g.,  
setting colorMaskNew equal to [1 1 0 0] would allow updates of the red and green  
channel, but not of the blue and alpha channel. A setting of [0 1 0 1] would  
allow updates to the green- and alpha channel, but not the red- and blue channel  
etc. The default writemask is 'all enabled' ie. [1 1 1 1].  
  
Settings for alpha-blending and color write mask are per window: They can be set  
individually for each onscreen window, offscreen window or texture.   


###See also:
[DrawDots](Screen-DrawDots), [DrawLines](Screen-DrawLines), [DrawTexture](Screen-DrawTexture)
