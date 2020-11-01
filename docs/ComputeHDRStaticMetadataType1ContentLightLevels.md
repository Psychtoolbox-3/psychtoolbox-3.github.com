# [ComputeHDRStaticMetadataType1ContentLightLevels](ComputeHDRStaticMetadataType1ContentLightLevels)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[safemaxFALL, safemaxCLL, maxFALL, maxCLL, errmsg] = [ComputeHDRStaticMetadataType1ContentLightLevels](ComputeHDRStaticMetadataType1ContentLightLevels)(images [, integerScalesToSDRRange=80Nits][, nanflag='omitnan'][, continueOnError=0]);  
  
Compute CTA-861-G static content light levels for an image or a cell array of images.  
  
Compute the maximum frame average light level in nits and return it in  
'maxFALL'. Compute the maximum content light level in nits and return it  
in 'maxCLL'. Return diagnostic error messages when appropriate in  
'errmsg', or an empty 'errmsg' if there weren't any notable issues.  
'safemaxFALL' and 'safemaxCLL' are clamped versions of 'maxFALL' and  
'maxCLL', ie. as long as calculated values are within the specified range  
for HDR static metadata type 1, they are identical. Otherwise, the safe  
variants are clamped to the limits of the safe range, ie. the range from  
0 to 65535 nits. [NaN](NaN) values for maxFALL or maxCLL result in safemaxFALL  
or safemaxCLL values of zero, as these signal "unknown" according to the  
standard.  
  
The returned maxFALL and maxCLL values are computed according to standard  
CTA-861-G, Annex P. 'maxCLL' the "maximum content light level" is defined  
as the luminance value in units of nits of the brightest pixel color  
component over all pixels in all frames of the image sequence. 'maxFALL'  
the "maximum frame average light level" is defined as the maximum over  
the average luminance values of all frames in the image sequence, where  
the average luminance of each frame is calculated over all pixels, but  
for each pixel only the value of the brightest color component is taken  
into account for calculation of the average, not the combined luminance  
of the whole pixel! One consequence of these definitions is that the computed  
maxFALL, maxCLL luminance values are only strictly correct under the  
assumption of an achromatic pixel, where the chromaticity coordinates of  
the pixel would correspond to those of the white-point of the display.  
Therefore, for an actual color image, maxFALL and maxCLL as measured by a  
colorimeter would likely be (much) lower than the maxFALL and maxCLL  
calculated by this function according to the standard.  
  
The maxFALL and maxCLL values calculated here can be used as arguments to  
a call to [PsychHDR](PsychHDR)('HDRMetadata', ...) to define what is transmitted to a  
connected HDR display device. They are meant as guidance and conservative  
estimates of what content light levels to expect, to aid potential vendor  
and display-model specific algorithms for tone-mapping and thermal-/power-/  
backlight-dimming management which may be implemented in the display device.  
Those algorithms try to reproduce HDR content which is outside the  
operating range of the display device in a faithful manner, using maxCLL,  
maxFALL and other static HDR metadata to help with the tradeoff between  
proper image reproduction and not damaging or overheating the display device.  
  
  
### Input arguments:  
  
'images' can be a single image matrix of height-by-width-by-channels  
pixel color components, for a height-by-width pixels image, with channels  
being 1 for a luminance image, 2 for a luminance + alpha channel image, 3  
for a RGB color image, or 4 for a RGBA image with additional alpha  
channel. The alpha channel of a 2 channel matrix or a 4 channel matrix is  
ignored for light level computations. 'images' will usually be a floating  
point HDR image, but integer images are also accepted, in which case  
returned 'maxFALL' and 'maxCLL' values are adapted according to the  
optional parameter 'integerScalesToSDRRange'. 'images' can also be a  
cell() array of image matrices, representing a whole image sequence. In  
case of a cell array, each image in the array contributes to light level  
property calculations and you get the maxCLL over the whole sequence, and  
maxFALL over the whole sequence.  
  
'integerScalesToSDRRange' Optional: How to treat 'images' of integer  
type, instead of floating point type. Currently the [Screen](Screen)('MakeTexture')  
command for turning image matrices into displayable image textures only  
accepts integer image matrices of type uint8, and floating point matrices  
of type double(). double() matrices are used "as is" for HDR display.  
  
Integer uint8 matrices are by default converted into HDR images with a  
value range that corresponds to typical standard dynamic range (SDR).  
Values from 0 to 255 are assumed to represent the HDR subrange [0; 80]  
nits. Iow. by default 0 maps to 0 nits and the maximum uint8 value of  
255 maps to 80 nits. See the help text of "[Screen](Screen) [MakeTexture](MakeTexture)?" and for  
the [PsychImaging](PsychImaging)() HDR setup functions for details on how this behaviour  
can be customized. 'integerScalesToSDRRange' defines how to adapt the  
returned 'maxFALL' and 'maxCLL' values if a integer image matrix is  
passed in: A value of 0 will just treat it like a floating point matrix.  
A value \> 0 will map the possible value range in the integer matrix to  
the range 0 - integerScalesToSDRRange. The default setting if this  
parameter is omitted, is to map the integer range to a range of 0 - 80  
nits, iow. returned maxCLL and maxFALL will be in the range 0 - 80 nits.  
This is the most reasonable behaviour if HDR display mode is requested  
with all parameters at their default and [Screen](Screen)('MakeTexture') is used  
with all precision related parameters at their defaults.  
  
'nanflag' Optional: How to treat [NaN](NaN) "not a number" values in pixel color  
components: By default 'nanflag' is 'omitnan' - Only non-[NaN](NaN) elements  
contribute to maximum and mean calculations for maxCLL, maxFALL. The  
other valid setting would be 'includenan' - If any pixel color component  
in any of the passed in 'images' is [NaN](NaN), the returned maxCLL and maxFALL  
will be [NaN](NaN).  
  
'continueOnError' Optional: If set to 0 (the default), abort with an  
error message on invalid input. If set to 1, try to continue if possible,  
just printing a warning message and return a user comprehensible error  
string in 'errmsg'.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/ComputeHDRStaticMetadataType1ContentLightLevels.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/ComputeHDRStaticMetadataType1ContentLightLevels.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/ComputeHDRStaticMetadataType1ContentLightLevels.m</code>
</div>

