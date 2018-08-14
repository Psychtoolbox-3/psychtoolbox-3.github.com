# [Screen('DrawDots')](Screen-DrawDots) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Quickly draw an array of dots.  "xy" is a two-row vector containing the x and y  
coordinates of the dot centers, relative to "center" (default center is [0 0]).  
"size" is the diameter of each dot in pixels (default is 1). Instead of a common  
size for all dots you can also provide a vector which defines a different dot  
size for each dot. Different graphics cards do have different limits on the  
maximum size of dots, 10 or 63 are typical limits.  
"color" is the the clut index (scalar or [r g b a] vector) that you want to poke  
into each dot pixel (default is black).  Instead of a single "color" you can  
also provide a 3 or 4 row vector,which specifies an individual RGB or RGBA color  
for each corresponding point.  
"dot\_type" is a flag that determines what type of dot is drawn: 0 (default) and  
4 draw square dots, whereas 1, 2 and 3 draw round dots (circles) with  
anti-aliasing: 1 favors performance, 2 tries to use high-quality anti-aliasing,  
if supported by your hardware. 3 Uses a builtin shader-based implementation.  
dot\_type 1 and 2 may not be supported by all graphics cards and drivers. On some  
systems [Screen](Screen)() will then automatically switch to dot\_type 3 - our own  
implementation - in such a case. If you use round dot\_type 1, 2 or 3 you'll also  
need to set a proper blending mode with the [Screen](Screen)('BlendFunction') command,  
e.g., GL\_SRC\_ALPHA + GL\_ONE\_MINUS\_SRC\_ALPHA. A dot\_type of 4 will draw square  
dots like dot\_type 0, but may be faster when drawing lots of dots of different  
sizes by use of an efficient shader based path.  
"lenient" If set to 1, will not check the sizes of dots for validity, so you can  
try requesting sizes bigger than what the hardware claims to support.  
  
The optional return arguments [minSmoothPointSize, maxSmoothPointSize,  
minAliasedPointSize, maxAliasedPointSize] allow you to query the minimum and  
maximum allowed 'size' for smooth anti-aliased dots (dot\_type 1,2,3) and for non  
anti-aliased square dots (dot\_type 0 and 4). Calling [...] = [Screen](Screen)('DrawDots',  
windowPtr) will only query these point size limits without drawing any dots.  
  


###See also:
[BlendFunction](Screen-BlendFunction)
