# [CreatePseudoGrayLUT](CreatePseudoGrayLUT)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[lut, numuniquelevels] = [CreatePseudoGrayLUT](CreatePseudoGrayLUT)(nativeBpc)  
  
Create and return a 3 rows by 2^(nativeBpc + 4) columns RGB16 uint16  
color lookup table 'lut', suitable as lut for the generic LUT based  
luminance output formatter of the Psychtoolbox imaging pipeline. This  
is a helper function for [PsychImaging](PsychImaging)(), usually not directly called by  
user code.  
  
This will setup the pipeline for output of luminance images with about  
1786 different levels of perceived luminance on a standard 8 bits per  
color channel RGB framebuffer of a standard graphics card. Also supports  
more levels on a 10 bpc or 12 bpc framebuffer.  
  
In general, under optimal conditions, for a suitable and well calibrated  
display, a luminance precision increase of up to 2.8 bits on top of the  
native output precision of the framebuffer and display device should be  
possible. However, this has not been verified yet, especially for the higher  
bit depths modes.  
  
### Usage:  
  
At the beginning of your script, replace the standard ...  
  
win = [Screen](Screen)('OpenWindow', screenid, ...);  
  
### ... call by the following commands:  
  
[PsychImaging](PsychImaging)('PrepareConfiguration');  
[PsychImaging](PsychImaging)('AddTask', 'General', 'EnablePseudoGrayOutput');  
win = [PsychImaging](PsychImaging)('OpenWindow', screenid, ....);  
  
  
### Further explanation:  
  
The technique to represent 10.7 bits (log2(1786)) of luminance on a 8 bit  
display is called "Pseudo Gray" or "Bit-Stealing". It adds small delta  
values to the different color channels to "tilt" the RGB color vector of  
each pixel a bit away from the "pure luminance' axis. This slight tilt,  
combined with the different emission characteristics of red, green and  
blue monitor phospor and the different sensitivity of the human eye for the  
three different colors, will create the perception (or illusion) of extra  
luminance values. So far the theory. In practice you'll need a well  
calibrated and gamma corrected color monitor for this to work, and there  
may be some smallish color artifacts in your stimuli.  
  
Anyway, this is the "poor man's solution" to high bitdepths luminance  
output, mostly here for illustration and demo purposes. If you need well  
controlled high quality high resolution luminance output, check out our  
different drivers for different high precision display devices like video  
attenuators, the [VideoSwitcher](VideoSwitcher), CRS Bits++ box and the AMD/ATI 10 bit  
framebuffer driver. See "help [PsychImaging](PsychImaging)" for an overview and usage.  
  
The LUT encoding used here is based solely on the algorithm described at  
this webpage by Richard W. Franzen:  
  
<http://r0k.us/graphics/pseudoGrey.html\>  
  
The webpage refers to multiple different sources of this type of  
algorithm, as apparently the principle was described by multiple independent  
authors. There is also a reference to the "Bit stealing" technique by:  
  
Tyler C.W., Chan H., Liu L., [McBride](McBride) B. & Kontsevich L.L. (1992)  
"Bit-stealing: How to get 1786 or more grey levels from an 8-bit color  
monitor", Proc. SPIE \#1666, pp 351-364.  
  
However, i haven't ever read that article, so i don't know if it proposes  
exactly the same procedure although readers of that article told me that  
it is "basically the same".  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreatePseudoGrayLUT.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreatePseudoGrayLUT.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreatePseudoGrayLUT.m</code>
</div>

