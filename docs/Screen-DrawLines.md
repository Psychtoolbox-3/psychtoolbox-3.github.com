# [Screen('DrawLines')](Screen-DrawLines) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Quickly draw an array of lines into the specified window "windowPtr".  
"xy" is a two-row vector containing the x and y coordinates of the line  
segments: Pairs of consecutive columns define (x,y) positions of the starts and  
ends of line segments. All positions are relative to "center" (default center is  
[0 0]). "width" is either a scalar with the global width for all lines in pixels  
(default is 1), or a vector with one separate width value for each separate  
line. "colors" is either a single global color argument for all lines, or an  
array of rgb or rgba color values for each line, where each column corresponds  
to the color of the corresponding line start or endpoint in the xy position  
argument. If you specify different colors for the start- and endpoint of a line  
segment, PTB will generate a smooth transition of colors along the line via  
linear interpolation. The default color is white if colors is omitted. "smooth"  
is a flag that determines whether lines should be smoothed: 0 (default) no  
smoothing, 1 smoothing (with anti-aliasing), 2 = high quality smoothing. If you  
use smoothing, you'll also need to set a proper blending mode with  
[Screen](Screen)('BlendFunction').  
"lenient" If set to 1, will not check the widths of lines for validity, so you  
can try requesting widths bigger than what the hardware claims to support.  
  
The optional return arguments [minSmoothLineWidth, maxSmoothLineWidth,  
minAliasedLineWidth, maxAliasedLineWidth] allow you to query the minimum and  
maximum allowed 'width' for smooth anti-aliased lines and for non anti-aliased  
lines. Calling [...] = [Screen](Screen)('DrawLines', windowPtr) will only query these  
width limits without drawing any lines.  
  


###See also:
[BlendFunction](Screen-BlendFunction)
