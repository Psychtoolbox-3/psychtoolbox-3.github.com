# [AdditiveBlendingForLinearSuperpositionTutorial](AdditiveBlendingForLinearSuperpositionTutorial)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[PsychTutorials](PsychTutorials)

[AdditiveBlendingForLinearSuperpositionTutorial](AdditiveBlendingForLinearSuperpositionTutorial)([outputdevice='None'] [, overlay=1] [, colorclut=0] [, doGainCorrection=0]);  
  
Illustrates use of floating point textures in combination with  
source-weighted additive alpha blending to create linear superpositions  
of image patches, in this case of two superimposed gratings. Due to the  
use of additive alpha-blending, you'll see that the two gratings will  
superimpose onto each other in a mathematically correct way -- pixel-wise  
addition/subtraction of luminance values. The demo uses a 32 bit floating  
point framebuffer on the latest hardware. This allows for an effective 23  
bits of precision in all math done and in the final stimuli - more than  
any display device in existence could resolve. On previous generation  
hardware (older than [NVidia](NVidia) Geforce 88000 or ATI Radeon HD2000), alpha  
blending isn't supported in 32 bpc float precision. Therefore the demo  
will select 16 bpc floating point precision, where alpha blending works.  
This way the effective precision is 11 bits, a bit less than what special  
display devices can resolve. However, final gamma correction is done in  
full 23 bits precision, so you can make use of the extra bits for proper  
display linearization.  
  
The demo also demonstrates Psychtoolbox support for high precision  
display output devices, ie., display extenders, graphics cards and  
display modes that allow for luminance display with more than the  
standard 8 bits precision. By default the standard 8 bit framebuffer of  
standard graphics cards is demonstrated.  
  
However, by providing the first optional parameter 'outputdevice', you  
can select amongst all devices supported by PTB:  
  
'NoneNoGamma' - Same as 'None': Use standard 8 bit framebuffer, but  
disable the gamma correction provided by PTB's imaging pipeline. This is  
usually not what you want, but it allows to test how much faster the  
display runs without gamma correction.  
  
'PseudoGray' - [PseudoGray](PseudoGray) display, also known as "Bit stealing". This  
technique allows to create the perception of up to 1786 different  
luminance levels on standard 8 bit graphics hardware by use of some  
clever color rendering trick. See "help [CreatePseudoGrayLUT](CreatePseudoGrayLUT)" for  
references and details.  
  
'Native10Bit' - Enables the native 10 bpc framebuffer support on ATI  
Radeon X1xxx / [HDxxx](HDxxx) GPU's when used under Linux or OS/X with the  
[PsychtoolboxKernelDriver](PsychtoolboxKernelDriver) loaded (see "help [PsychtoolboxKernelDriver](PsychtoolboxKernelDriver)" on  
how to do that). These GPU's do support 10 bits per color channel when  
this special mode is used. This also works with properly configured [NVidia](NVidia)  
GPU's under Linux, and with [NVidia](NVidia) Quadro and AMD Fire gpu's under  
some versions of MS-Windows.  
  
'Native11Bit' - Enables the native ~11 bpc framebuffer support on ATI  
Radeon X1xxx / [HDxxx](HDxxx) GPU's when used under Linux or OS/X with the  
[PsychtoolboxKernelDriver](PsychtoolboxKernelDriver) loaded (see "help [PsychtoolboxKernelDriver](PsychtoolboxKernelDriver)" on  
how to do that). These GPU's do support ~11 bits per color channel when  
this special mode is used (11 bits red, 11 bits green, 10 bits blue).  
  
'Native16Bit' - Enables the native up to 16 bpc framebuffer support on AMD  
GPU's when used under Linux . While this activates a 16 bpc framebuffer,  
the precision of the video output signal depends on the specific gpu, connection  
and display. As of 2014, the "Sea Islands" AMD gpu family can output at most  
12 bpc precision to suitable displays over HDMI or [DisplayPort](DisplayPort). This mode needs  
special configuration of your system and use of the Linux open-source graphics  
drivers. If you can do with 10 bpc or 11 bpc, 'Native10Bit' or 'Native11Bit' are  
much easier to use and setup and provide higher performance.  
  
'VideoSwitcher' - Enable the Xiangrui Li et al. [VideoSwitcher](VideoSwitcher), a special  
type of video attenuator (see "help [PsychVideoSwitcher](PsychVideoSwitcher)") in standard  
"simple" mode.  
  
'VideoSwitcherCalibrated' - Enable the Xiangrui Li et al. [VideoSwitcher](VideoSwitcher),  
but use the more complex (and more accurate?) mode with calibrated lookup  
tables (see "help [PsychVideoSwitcher](PsychVideoSwitcher)").  
  
'Attenuator' - Enable support for standard Pelli & Zhang style video  
attenuators by use of lookup tables.  
  
Then we have support for the different modes of operation of the  
Cambridge Research Systems Bits++ box:  
  
'Mono++' - Use 14 bit mono output mode, either with color index overlay  
(if the optional 2nd 'overlay' flag is set to 1, which is the default),  
or without color index overlay.  
  
'Color++' - User 14 bits per color component mode.  
  
Then we have support for the different modes of operation of the  
[VPixx](VPixx) Technologies [DPixx](DPixx) [(DataPixx)]((DataPixx)) box:  
  
'M16' - Use 16 bit mono output mode, either with color index overlay  
(if the optional 2nd 'overlay' flag is set to 1, which is the default),  
or without color index overlay.  
  
'C48' - User 16 bits per color component mode.  
  
  
'BrightSide' - Enable drivers for BrightSide's HDR display. This only  
works if you have a [BrightSide](BrightSide) HDR display + the proper driver libraries  
installed on MS-Windows. On other operating systems it just uses a simple  
dummy emulation of the display with less than spectacular results.  
  
'DualPipeHDR' - Use experimental output to dual-pipeline HDR display  
device.  
  
  
The third optional parameter 'colorclut' if provided, will use color  
lookup table based color correction / mapping, ie., mapping of luminance  
values to RGB values in the framebuffer - or intensity values if  
applicable. Any non-zero number will select a different CLUT. Look into  
the code for description. This just to demonstrate that you can use CLUT  
based color/intensity correction instead of simple power-law gamma  
correction if you want.  
  
  
The fourth optional parameter 'doGainCorrection' if provided and set to  
1, will demonstrate use of display per-pixel gain correction, aka  
vignetting correction. It will modulate the brightness of each pixel with  
a gain factor, the gains increasing linearly from the left border to the  
right border of the display. See "help [VignettingCorrectionDemo](VignettingCorrectionDemo)" for more  
details of this feature.  
  
  
Please note: Most of these modes only show expected results when the  
proper devices are attached and calibrated. All modes will work even on  
standard graphics without special devices, but you'll just see a false  
color image, as the standard GPU's can't interpret the special  
framebuffer encodings.  
  
The demo shows two superimposed sine wave gratings in the center of the  
screen. You can shift the 2nd grating up and down in subpixel steps by  
use of the cursor up-/down keys. You can change the contrast of the 2nd  
grating by use of the cursor left-/right keys. You can move the 2nd  
grating with the mouse, and rotate it clockwise or counterclockwise by  
pressing the mouse buttons. The keys 'i' and 'd' allow to change the  
"encoding gamma" factor used for the gamma correction algorithm. The ESC  
ape key ends the demo. Actually the demo performs some benchmark run for  
a few seconds after you've pressed ESC key, just to measure the speed of  
your graphics card in stimulus conversion.  
  
In 'VideoSwitcher' mode, it also draws some vertically moving greenish  
sync line just to show how to generate trigger signals on the  
[VideoSwitcher](VideoSwitcher) device.  
  
  
Needs hardware with support for imaging pipeline (GLSL shaders and  
floating point framebuffers). Should work well on ATI Radeon X1000 and  
later, Geforce 6000 and later and even better on [DirectX10](DirectX10) hardware like  
Radeon HD series and [NVidia](NVidia) Geforce 8 / 9 series and later.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PsychTutorials/AdditiveBlendingForLinearSuperpositionTutorial.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PsychTutorials/AdditiveBlendingForLinearSuperpositionTutorial.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PsychTutorials/AdditiveBlendingForLinearSuperpositionTutorial.m</code>
</div>

