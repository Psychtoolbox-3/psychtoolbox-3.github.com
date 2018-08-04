# [PsychColorCorrection](PsychColorCorrection)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

varargout = [PsychColorCorrection](PsychColorCorrection)(cmd, varargin)  
  
This function is used to setup and control the built-in color correction   
and transformation mechanisms of PTB's imaging pipeline. It allows to choose  
among different methods of color correction (for calibrated output of  
stimuli) and to change parameters of the chosen method. This only works  
when the imaging pipeline is enabled and with certain output devices.  
  
This functions are mostly meant to provide fast color correction, e.g.,  
gamma correction, when PTB is used with special high precision / HDR  
output devices, e.g., CRS Bits++ in Mono++ or Color++ mode, or video  
attenuators. When operating such devices, the standard gamma correction  
mechanisms of your graphics card can't be used, so PTB must do it itself.  
  
With a standard 8bpc framebuffer, you won't need this function for simple  
gamma correction or color correction.  
Instead you'd use the [Screen](Screen)('LoadNormalizedGammaTable') command to  
perform gamma correction with the graphics cards built-in gamma tables.  
Same applies to Bits++ box in Bits++ mode, using the built-in tables of  
the Bits++ device, also controlled via [Screen](Screen)('LoadNormalizedGammaTable').  
  
For more complex correction schemes than a lookup table transform you can  
still use this function, even with a normal 8 bit framebuffer, as long as  
the imaging pipeline is enabled. It's just important to note that you  
don't need to use it for a standard framebuffer in the simple case -- the  
gfx cards gamma tables are more efficient for the simple case.  
  
### How to use:  
  
1. Before opening an onscreen window, you use the following  
[PsychImaging](PsychImaging)() setup call to specify the method of display color correction  
to apply, and the view channel to apply it to (in case there are multiple  
like in many stereo display setups):  
  
[PsychImaging](PsychImaging)('AddTask', whichChannel, 'DisplayColorCorrection', methodname);  
- where whichChannel can be 'LeftView' or 'RightView' for the left- or  
right display output channel/device of a stereo setup, or  
'FinalFormatting' if you have a single display monoscopic setup or want  
to apply the same color correction to both channels of a stereo setup.  
The parameter 'methodname' is a name string with the name of one of the  
supported methods - See overview below for supported methods.  
  
CAUTION: The order of specifications matters! If you use multiple color  
correction methods or other image processing operations simultaneously,  
make sure to specify them in the order in which they should be executed.  
The system tries to order operations in a reasonable way, but it is not  
fool-proof!  
  
2. Then, after you've specified all other window parameters via the  
[PsychImaging](PsychImaging)() subcommands, you open the onscreen window via the usual  
win = [PsychImaging](PsychImaging)('OpenWindow', ....); call, as always when you use the  
imaging pipeline. This will open the window and apply the chosen color  
correction method, choosing reasonable default parameters for the method  
at hand.  
  
3. At any time in your script you can change the operating parameters of  
the chosen color correction method via the [PsychColorCorrection](PsychColorCorrection)()  
subfunctions mentioned below. You'll have to specify the window handle  
for the onscreen window whose parameters should be changed, and - in a  
stereo display setup with separate color correction parameters for each  
of the display channels - the name 'whichChannel' of the display channel  
to change, e.g., 'LeftView'. Changes take effect at next [Screen](Screen)('[Flip](Flip)').  
  
  
  
Supported display color correction methods:  
===========================================  
  
These are the method names that can be passed as 'methodname' parameter to  
[PsychImaging](PsychImaging)('DisplayColorCorrection', ....., methodname):  
  
### 'methodname' is the name string of one of the supported methods:  
  
\* 'None': Don't do anything. Fastest, but not safest.   
  
  If your stimulus contains (by accident) color or luminance values outside  
  the displayable range, the corresponding pixels may show undefined output  
  color -- Likely not what you want. This mode is about 10% faster than  
  'ClampOnly'. This mode is the default if no method is selected, unless  
  you use Bits++ in Mono++ or Color++ mode, where 'ClampOnly' is the  
  default.  
  
  
\* 'ClampOnly': Do not apply any color transformation. Default for Bits++  
  in Mono++ or Color++ mode:  
  
  In this mode, values are clamped against the limits set via  
  'SetColorClampingRange' (see below) to always keep them in the  
  requested range set via [PsychColorCorrection](PsychColorCorrection)('SetColorClampingRange'),  
  nothing else.  
  
  
\* 'CheckOnly': Do not apply any color transformation.  
  
  In this mode, values are checked against the limits set via  
  [PsychColorCorrection](PsychColorCorrection)('SetColorClampingRange'). Values outside that  
  range are visually coded, so you should be able to see troublesome  
  areas via visual inspection: All values are first clamped, then  
  inverted, in the hope that this creates clearly detectable artifacts in  
  your stimulus. We may change the "marker" method in the future if we  
  happen to find a better visual marker. This mode is meant for debugging  
  your stimulation scripts, not for running them on your subjects!  
  
  
### \* 'SimpleGamma' : Apply some power-law based gamma correction:  
  
  Simple gamma correction means: Apply a power-law to incoming  
  values: outcolor = incolor ^ [EncodingGamma](EncodingGamma). incolor is the uncorrected  
  input color or intensity, outcolor the corrected one, [EncodingGamma](EncodingGamma) is  
  encoding gamma value to apply. See [PsychColorCorrection](PsychColorCorrection)('SetEncodingGamma')  
  for how to set the gamma values. After gamma correction, output values  
  are clamped against the range set via [PsychColorCorrection](PsychColorCorrection)('SetColorClampingRange').  
  
  See [PsychColorCorrection](PsychColorCorrection)('SetExtendedGammaParameters') on how to supply  
  additional parameters for use of a more complex gamma correction function.  
  
  
### \* 'MatrixMultiply4' : Multiply with 4x4 color transformation matrix:  
  
  Extend RGB component of color by a fourth "constant 1" component,  
  multiply by specified 4-by-4 matrix, normalize by dividing result by  
  4'th component, return transformed rgb components as output color. Pass  
  through alpha-channel unmodified.  
  
  rgbw' = M \* [r,g,b,1]'  
  out.rgb = [r', g', b'] / w'  
  out.a = a  
  
\* 'SensorToPrimary' : Implement the same conversion as [SensorToPrimary](SensorToPrimary).m  
  
  This can convert from XYZ sensor tristimulus values to standard RGB  
  primary color values. This is the right thing to do if your display  
  device is linearized via use of a proper gamma correction method.  
  
  Use the function [PsychColorCorrection](PsychColorCorrection)('SetSensorToPrimary') below to  
  assign the 'cal'ibration struct to use for actual conversion from XYZ  
  color values to RGB primaries.  
  
  
\* '[xyYToXYZ](xyYToXYZ)' : Implement the same conversion as [xyYToXYZ](xyYToXYZ).m  
  
  This can convert to tristimulus XYZ color coordinates from  
  chromaticity (x,y) and luminance (Y) color coordinates xyY. It performs  
  the same color space conversion as the M-Function XYZ = [xyYToXYZ](xyYToXYZ)(xyY).  
  
  
\* 'LookupTable' : Apply color correction by color table lookup, ie. a CLUT.  
  
  This will allow to pass in a color lookup table of selectable  
  granularity (ie., number of slots) and range, which is later on used to  
  lookup corresponding corrected color values for given framebuffer input  
  values.  
  
  
\* 'LookupTable3D' : Apply color correction by a 3D color table lookup.  
  
  This will allow to pass in a 3D color lookup table of selectable  
  granularity (ie., number of slots per dimension) and range, which is  
  later on used to lookup corresponding corrected color values for given  
  framebuffer input values.  
  
  
\* 'GainMatrix' : Apply color gain correction by 2D gain matrix lookup.  
  
  This allows to apply a 2D matrix G which stores luminance- or color gain  
  correction factors for each single output pixel of the display. For  
  each 2D display pixel location (x,y), the stimulus image I(x,y) will be  
  multiplied with the corresponding gain factor G(x,y) of the gain matrix  
  and the result O(x,y) used for further processing and display. G(x,y)  
  can be a single scalar for luminance correction, or - if G is a 3-layer  
  matrix - a RGB vector with individual gains for each color channel and  
  pixel location.  
  
  O(x,y) = I(x,y) \* G(x,y).  
  
  If you want to combine this with one of the other correction methods,  
  e.g., gamma correction, you should issue this command first, because  
  the non-linear gamma correction should apply to the output of this  
  method for correct results.  
  
  After you've opened your onscreen 'window', you'll need to define the 2D  
  gain 'matrix' via a call to ...  
  
  [PsychColorCorrection](PsychColorCorrection)('SetGainMatrix', ...);  
  
  See below for description of 'SetGainMatrix'.  
  
\* 'AnaglyphStereo' : Apply anaglyph stereo algorithm.  
  
  This loads a similar anaglyph shader as the one used in stereoModes 6  
  to 9 when the function [SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)('ColorAnaglyphMode')  
  or its siblings was used. This is useful if you want to employ anaglyph  
  stereo presentation, but not by rendering a full anaglyph image into  
  one single framebuffer for output to a single display or projector, but  
  if you want to direct the "left-eye" anaglyph image to a different  
  display or projector than the "right-eye" anaglyph image. An example  
  would be having two video projectors attached to two video outputs of a  
  graphics card. One projector shall project the left-eye image, the  
  other one the right-eye image. In this case you'd choose a stereoMode  
  of 4 or 5 (typically on Linux or Windows) for desktop spanning stereo  
  output, or 10 (on OSX) for dual-window stereo output. Then you'd use ...  
  [PsychImaging](PsychImaging)('AddTask', 'LeftView', 'DisplayColorCorrection', 'AnaglyphStereo')  
  ... and ...  
  [PsychImaging](PsychImaging)('AddTask', 'RightView', 'DisplayColorCorrection', 'AnaglyphStereo')  
  ... to add an anaglyph shader to the end of each view channel.  
  
  After adding individual shaders for each image processing channel and opening  
  the onscreen window(s), you can use [SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)() to  
  parameterize the anaglyph stereo presentation as if it were created via  
  regular anaglyph stereo setup in stereomoded 6-9.  
  
  
Supported runtime Subfunctions:  
===============================  
  
oldlevel = [PsychColorCorrection](PsychColorCorrection)('Verbosity' [, newlevel]);  
Return current level of verbosity in optional 'oldlevel', optionally set  
new level of verbosity via 'newlevel'. The level of verbosity affects how  
much status output is printed in some routines: 0 = Nothing, 1 = Only  
errors, 2 = Errors and warnings, 3 = Errors + Warnings + Some info.  
  
  
The following routines must be called \*after\* opening a window for which color  
correction is enabled. They can be called anytime and changed settings  
will apply at the next [Screen](Screen)('[Flip](Flip)'). If your 'window' is actually a  
stereo display window, you may want or need to provide the optional  
'viewId' parameter to tell PTB which of the two stereo view channels  
shall be changed in its settings. If both stereo views are displayed on  
the same physical display device, this is not needed. If the separate  
views go to separate physical displays, you may need to calibrate them  
separately. Allowable values for viewId are 'AllViews', 'LeftView' and  
'RightView', corresponding to the 'whichChannel' setting that you used  
when setting up the window with [PsychImaging](PsychImaging)().  
  
  
[PsychColorCorrection](PsychColorCorrection)('SetColorClampingRange', window, min, max [,viewId]);  
- Set the range of allowable output color or luminance intensity values  
to the interval [min; max] for onscreen window 'window'. Values outside  
that range get either clamped to the 'min'imum or 'max'imum value, or -  
in 'CheckOnly' mode - will be visually marked as out of range. The default  
range is [0.0 ; 1.0] -- The range that your display device can really  
display.  
  
  
[PsychColorCorrection](PsychColorCorrection)('SetEncodingGamma', window, gamma [,viewId]);  
- Set the gamma value to use for gamma correction on window 'window'.  
'gamma' can be either a single scalar if the same gamma should apply to  
all color channels (or single luminance channel), or it can be a  
three-component [gammaRed, gammaGreen, gammaBlue] vector, if each color  
channel should be gamma corrected with an individual gamma value.  
  
How the value gets applied depends on the chosen method of color  
correction (see above). The simplest method ('SimpleGamma') performs a  
simple power-law mapping of input values to output values: out = in ^ gamma.  
'in' must be greater than zero, and 'gamma' must be greater than zero,  
otherwise results may be undefined, depending on your graphics hardware.  
However, usually only encoding 'gamma' values in the range of about  
0.33 - 1.0 are meaningful.  
  
Example: If your monitor has a "decoding gamma" of 1.8, the proper  
setting for 'gamma' would be gamma = 1/1.8. For a decoding gamma of 2.2,  
you'd choose gamma = 1/2.2 ...  
  
  
[PsychColorCorrection](PsychColorCorrection)('SetExtendedGammaParameters', window, minL, maxL, gain, bias [,viewId]);  
- Set the additional (optional) parameters to fine-tune gamma correction on  
window 'window'. All these parameters have reasonable defaults. All  
parameters can be supplied as a scalar value if the same setting shall  
apply to all color channels (or a single luminance channel), or you can  
provide 3-component vectors with one component for each color channel:  
  
After this function has been called at least once, the following formula  
will be used to map input values to output values ['gamma' is as set by  
the 'SetEncodingGamma' function, 'in' is input, 'out' is output value]:  
  
out = bias + gain \* ( ((in-minL) / (maxL-minL)) ^ gamma )  
  
Required parameters:  
'minL' Minimum expected input luminance/intensity value (Default is 0.0).  
'maxL' Maximum expected input luminance/intensity value (Default is 1.0).  
'gain' Gain factor to apply after power-law mapping (Default is 1.0).  
'bias' Bias/Offset to apply to final result before output (Default is 0.0).  
  
  
[PsychColorCorrection](PsychColorCorrection)('SetMultMatrix4', window, matrix [, viewId]);  
- Set the 4-by-4 color transformation matrix to use for the 'MatrixMultiply4'  
color correction method. 'matrix' must be the 2D 4 rows by 4 columns  
matrix to use. By default, the matrix is set to an identity matrix.  
  
  
[PsychColorCorrection](PsychColorCorrection)('SetSensorToPrimary', window, cal [, viewId]);  
- Set the 'cal'ibration struct to use for the 'SensorToPrimary' color  
correction method. 'cal' must be the same input format as used for the  
M-Function [SensorToPrimary](SensorToPrimary)(). By default, the transformation is a "no  
operation".  
  
  
[PsychColorCorrection](PsychColorCorrection)('SetLookupTable', window, clut [, viewId][, maxinput=1][, scalefactor]);  
- Assign color lookup table 'clut' for use with color correction method  
'LookupTable'. 'clut' must be a 1 column vector for pure luminance lookup  
tables, or a 3 column matrix for RGB color lookup tables with one column  
per color channel, ie., [1,2,3] = [Red, Green, Blue]. clut must have at  
least 1 row, but usually will have way more than 2 rows, typically almost  
as many rows as n = 2^bpc for a given output device bitdepths bpc. For a  
10 bit output device, n would be usually 2^10 = 1024 rows for a perfect  
one-to-one mapping. At runtime, color correction will be performed by the  
following formula: Be Rin, Gin, Bin the input red, green and blue color  
components, and Rout, Gout, Bout the final output value for the  
framebuffer. First Rin, Gin and Bin are clamped individually to the range  
0.0 - 'maxinput' (maxinput is 1.0 by default), scalefactor is chosen by  
default as scalefactor = [number of rows in clut - 1] / maxinput, ie., it  
maps the possible input range 0 - maxinput to the full range of row  
indices 1 - rowcount to cover the full range of entries stored in the  
clut. This is the most reasonable default, but can be changed by the  
optional 'scalefactor' and 'maxinput' arguments.  
  
Then the output color for each component is looked up in the proper slot  
(= row index) of the passed clut:  
  
Rout = clut(Rin \* scalefactor,1);  
Gout = clut(Gin \* scalefactor,2);  
Bout = clut(Bin \* scalefactor,3);  
  
Color values for fractional indices inbetween reference values in the  
clut are interpolated linearly between the two nearest neighbour  
reference values --\> linear interpolation.  
  
Finally, Rout, Gout and Bout are clamped to the valid output range as set  
by the function [PsychColorCorrection](PsychColorCorrection)('SetColorClampingRange', ...); by  
default to the range 0.0 - 1.0.  
  
  
[PsychColorCorrection](PsychColorCorrection)('SetLookupTable3D', window, clut [, viewId][, maxinput=1][, scalefactor][, precision=0][, interpolate=1]);  
- Assign 4D color lookup table 'clut' for use with color correction method  
'LookupTable3D'. 'clut' must be a 4D 3-by-m-by-n-by-p matrix. The first dimension encodes the  
output color values to use:  
clut(1,r,g,b) == Corrected red color value for input color [r,g,b].  
clut(2,r,g,b) == Corrected green color value for input color [r,g,b].  
clut(3,r,g,b) == Corrected blue color value for input color [r,g,b].  
  
clut must have at least one element in each color index dimension, ie., m, n  
and p must be \>= 1, but usually will have more elements in each dimension  
for a meaningful lookup color correction. In theory you would need m, n  
and p to be == 2^bpc for a given output device bitdepths bpc, e.g, for a  
8 bit output device, m,n,p would need to be 2^8 = 256 elements for a perfect  
one-to-one mapping. In reality you likely don't want to use such large  
sizes, as such a huge and dense 3D CLUT would take up considerable  
amounts of graphics memory and cause large slowdowns of all drawing  
operations. For good performance and portability of your code to older  
graphics cards, choose modest sizes, as small as possible.  
  
At runtime, color correction will be performed by the following 3D table  
lookup procedure: Let Rin, Gin, Bin be the input red, green and blue  
color components, and Rout, Gout, Bout the final output values for the  
framebuffer. First Rin, Gin and Bin are clamped individually to the range  
0.0 - 'maxinput' (maxinput is 1.0 by default), scalefactor is chosen by  
default as scalefactor = (1.0 / maxinput), ie., it maps the possible  
input range 0 - 'maxinput' to the range 0.0 - 1.0, which covers the full  
range of entries stored in the clut. This is the most reasonable default,  
but can be changed by the optional 'scalefactor' and 'maxinput'  
arguments.  
  
Then the output color for each component is looked up in the proper 3D  
slot of the passed clut:  
  
Rout = clut(1, Rin \* scalefactor, Gin \* scalefactor, Bin \* scalefactor);  
Gout = clut(2, Rin \* scalefactor, Gin \* scalefactor, Bin \* scalefactor);  
Bout = clut(3, Rin \* scalefactor, Gin \* scalefactor, Bin \* scalefactor);  
  
Color values (Rin, Gin, Bin) == (0,0,0) map to the first elements in the  
cluts dimensions, ie., clut(:,1,1,1). Maximum values (maxinput, maxinput,  
maxinput) map - after scaling with the default scalefactor - to  
coordinates (1.0, 1.0, 1.0) in the normalized 3D color coordinate space  
and are looked up in the maximal clut element indices of each dimension,  
ie., clut(:,m,n,p) for our 3-by-m-by-n-by-p clut. Intermediate values are  
mapped accordingly to proper clut element indices.  
  
By default, color values for fractional indices inbetween reference  
values in the clut are interpolated linearly between the eight nearest  
neighbour reference values in the 3 dimensional space --\> This is  
trilinear interpolation across all 3 color dimensions of the CLUT. If you  
set the optional parameter 'interpolate' to zero, then simple nearest  
neighbour sampling is performed instead.  
  
The optional 'precision' flag controls the precision with which entries  
in the CLUT should be stored and processed: precision = 0 is the default  
and stores values with 8 bit precision for 256 different intensity levels  
for Rout, Gout and Bout. A setting of 1 will store values with 16 bpc  
floating point precision to resolve up to 10 bits or 1024 levels of  
linear precision. A setting of 2 will store values with 32 bpc floating  
point precision for up to 23 bits of linear precision. Be aware that  
precision values \> 0 will increase memory consumption by a factor of 2x  
or 4x, which can be significant for lookup tables of non-trivial size.  
  
Final looked up, Rout, Gout and Bout are clamped to the valid output range as set  
by the function [PsychColorCorrection](PsychColorCorrection)('SetColorClampingRange', ...); by  
default to the range 0.0 - 1.0.  
  
Essentially, this color correction allows to define arbitrary mappings of  
RGB input triplets to RGB output triplets, providing a large amount of  
flexibility. Be aware though that strongly discontinuous mappings of input  
colors to output colors can have a significant negative impact on the  
drawing performance of your graphics card. Define your clut's wisely!  
  
  
[PsychColorCorrection](PsychColorCorrection)('SetGainMatrix', window, matrix [, viewId][, precision=2]);  
  
- Set gain matrix for method 'GainMatrix'.  
If matrix is a 2D matrix, the gain will be applied to all color  
channels equally. If matrix is a 3D matrix, matrix(y,x,1) will define  
the red channel gain, matrix(y,x,2) will define the green channel gain,   
and matrix(y,x,3) will define the blue channel gain.  
  
The optional 'precision' parameter defines the numerical precision with  
which the gain factors are stored. The default setting of 2 stores with  
32 bit floating point precision - about 6 digits behind the decimal  
point. A Setting of 1 stores with 16 bit float precision, about 3 digits.  
A Setting of 0 stores with 256 levels, about 2 digits. A lower precision  
is less precise but allows for faster processing and higher redraw rates  
if needed.  
  
  
  
Internal commands, usually not meant for direct use by pure mortals:  
====================================================================  
  
All these methods are usually called from within [PsychImaging](PsychImaging)() to do the  
dirty setup work...  
  
### Call this \*before\* opening a window:  
  
  
[PsychColorCorrection](PsychColorCorrection)('ChooseColorCorrection', methodname);  
- Specify the method to be used for color correction for the next  
onscreen window that will be opened. This needs to be called \*before\* the  
window is opened, however its usually done automatically at the right  
moment by routines like [PsychImaging](PsychImaging)() or [BitsPlusPlus](BitsPlusPlus)() if you use these  
to open windows.  
  
  
### Called after [Screen](Screen)('OpenWindow') during shader and pipeline setup:  
  
[shader, idstring, configString, overrideMain] = [PsychColorCorrection](PsychColorCorrection)('GetCompiledShaders', window, debuglevel);  
- Compile corresponding shaders for chosen color correction method,  
return shaderhandles and idstring to calling routine. That routine will  
link the returned shaders with other shader code to produce the final  
GLSL program object for color conversion and output formatting. 'shader'  
is the GLSL shader handle, idstring the name string for the shader,  
configString the shader option string for the 'Hookfunction' call, e.g.,  
to bind additional LUT textures, etc.  
  
  
Called after linking and attaching the final processing GLSL program  
objects and slots to the imaging pipelines hook chain(s):  
  
  
[PsychColorCorrection](PsychColorCorrection)('ApplyPostGLSLLinkSetup', window, viewId);  
- Perform whatever setup work is needed after final GLSL program object  
has been created and attached to imaging pipeline.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/PsychColorCorrection.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/PsychColorCorrection.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/PsychColorCorrection.m</code>
</div>

