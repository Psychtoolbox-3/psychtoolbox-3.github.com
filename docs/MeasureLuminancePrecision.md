# [MeasureLuminancePrecision](MeasureLuminancePrecision)
##### >[Psychtoolbox](Psychtoolbox)>[PsychAlpha](PsychAlpha)

 data=[MeasureLuminancePrecision](MeasureLuminancePrecision)([meterType=7])  
  
 'meterType' selects type of photometer. Defaults to 7 for CRS [ColorCal2](ColorCal2), see  
 'help CMCheckInit' for other supported devices.  
  
 INSTRUCTIONS: Plug your photometer into your computer, carefully  
 place your photometer stably against your computer's screen, set  
 PARAMETERS (below), then run. The results (including the best-fitting  
 n-bit-precision model) will be displayed as a graph in a figure window,  
 and also saved in three files (in the same folder as this file) with  
 filename extensions: png, fig, and mat. The filename describes the  
 testing conditions, e.g.  
 [DenissMacBookPro5K](DenissMacBookPro5K)-Dithering61696-o.use10Bits-[LoadIdentityCLUT](LoadIdentityCLUT)-Luminances8.fig  
  
 EXPLANATION: Using Psychtoolbox SCREEN imaging, measures how precisely we  
 can control display luminance. Loads identity into the Color Lookup Table  
 (CLUT) and measures the luminance produced by each value loaded into a  
 large identical patch of image pixels. (This program varies only the  
 luminance, not hue, always varying the three RGB channels together, but  
 the conclusion about bits of precision per channel almost certainly  
 applies to general-purpose presentation of arbitrary RGB colors.) The  
 attained precision will be achieved mostly by the digital-to-analog  
 converter and, perhaps, partly through dither by the video driver. Since  
 the 1980's most digital computer displays allocate 8 bits per color  
 channel (R, G, B). In the past few years, some displays now accept 10 or  
 more bits for each channel and pass that through from the pixel in memory  
 through the color lookup table (CLUT) to the digital to analog converter  
 that controls light output. In 2016-2017, Mario Kleiner enhanced The  
 Psychtoolbox SCREEN function to allow specification of each color  
 component (R G B) as a floating point number, where 0 is black and 1 is  
 maximum output, so that your software, without change, will drive any  
 display and benefit from as much precision as the display hardware and  
 driver provide.  
  
 Typically you'll run [MeasureLuminancePrecision](MeasureLuminancePrecision) from the command line. It  
 will make all the requested measurements and plot the results, including  
 the best-fitting n-bit-precision model. Each figure is saved as both a  
 FIG and PNG file, and the data are saved as a MAT file. The data are also  
 returned as the output argument. It has luminance out "data.L" vs  
 floating point color value "data.v".  
  
 To use this program to measure the precision of your computer display you  
 need three things:  
 1. MATLAB or Octave. http://mathworks.com , https://www.gnu.org/software/octave  
 2. The Psychtoolbox, from http://psychtoolbox.org.  
 3. A photometer or colorimeter supported by [CMCheckInit](CMCheckInit)(), e.g., the CRS [ColorCal2](ColorCal2)  
 http://www.crsltd.com/tools-for-vision-science/light-measurement-display-calibation/colorcal-mkii-colorimeter/  
 It's plug and play, taking power through its USB cable.  
  
 As of April 2017, Apple documents (below) indicate that two currently  
 available macOS computers attain 10-bit precision from pixel to display  
 (in each of the three RGB channels): the Mac Pro and the iMac 27" retina  
 desktop. From my testing, I add the Apple's high-end [MacBook](MacBook) Pro laptop  
 (Retina, 15-inch, Mid 2015). I tested my [MacBook](MacBook) Pro (Retina, 15-inch,  
 Mid 2015) and iMac (Retina 5K, 27-inch, Late 2014). Both use AMD drivers.  
 Using [MeasureLuminancePrecision](MeasureLuminancePrecision), I have documented 11-bit luminance  
 precision on both of these displays, enabling both o.use10Bits and  
 o.useDithering,  
 https://www.macrumors.com/2015/10/30/4k-5k-imacs-10-bit-color-depth-osx-el-capitan/  
 https://developer.apple.com/library/content/samplecode/[DeepImageDisplayWithOpenGL](DeepImageDisplayWithOpenGL)/Introduction/Intro.html\#//apple\_ref/doc/uid/TP40016622  
 https://developer.apple.com/library/content/samplecode/[DeepImageDisplayWithOpenGL](DeepImageDisplayWithOpenGL)/Introduction/Intro.html\#//apple\_ref/doc/uid/TP40016622  
 https://macperformanceguide.com/blog/2016/20161127\_1422-[Apple2016MacBookPro](Apple2016MacBookPro)-10-bit-color.html  
  
 10 bpc precision should also work on macOS with Apple Silicon Macs,  
 pro-class gpu's from AMD and [NVidia](NVidia) on MS-Windows, and many gpu's on Linux,  
 e.g., AMD, [NVidia](NVidia), Intel, [RaspberryPi](RaspberryPi) 4 and later, other modern SoC's...  
  
 My Hewlett-Packard Z Book laptop running Linux also attains 10-bit  
 luminance precision. I have not yet succeeded in getting dither to work  
 on the Z Book. Thanks to my former student, H�rmet Yiltiz, for setting up  
 the Z Book and getting 10-bit imaging to work, with help from Mario  
 Kleiner.  
  
 [MacBook](MacBook) Pro driving NEC PA244UHD 4K display  
 https://macperformanceguide.com/blog/2016/20161127\_1422-[Apple2016MacBookPro](Apple2016MacBookPro)-10-bit-color.html  
  
###  PARAMETERS:  
 o.luminances = number of luminances to measure, 3 s each.  
 o.reciprocalOfFraction = list desired values, e.g. 1, 64, 128, 256.  
 o.usePhotometer = 1 use supported photometer; 0 simulate 8-bit rendering.  
 See SET PARAMETERS below.  
  
  
 Denis Pelli, April 24, 2017  
  
  
 History:  
 24-Apr-2017   dgp     Wrote original version.  
 ??-???-2019   mk      Hacked it, improved it somewhere somewhat.  
 14-Feb-2021   mk      Included into Psychtoolbox as baseline for cleanup.  
 07-Oct-2021   mk      Refined.  
  
% DITHERING NOTES  
 (FROM MARIO) FOR HP Z Book "Sea Islands" GPU:  
 10 bpc panel dither setup code for the zBooks "Sea Islands" (CIK) gpu:  
 http://lxr.free-electrons.com/source/drivers/gpu/drm/radeon/cik.c\#L8814  
 The constants which are or'ed / added together in that code are defined  
 here:  
 http://lxr.free-electrons.com/source/drivers/gpu/drm/radeon/cikd.h\#L989  
 I simply or'ed the proper constants to get the numbers i told you, so PTB  
 replicates the Linux display drivers behaviour. As you can see there are  
 many parameters one could tweak for any given display. E.g., add/drop  
 FMT\_FRAME\_RANDOM\_ENABLE, FMT\_HIGHPASS\_RANDOM\_ENABLE, or  
 FMT\_RGB\_RANDOM\_ENABLE for extra entertainment value. It's somewhat of a  
 black art. The gpu also has various temporal dithering modes with even  
 more parameters, or combined spatio-temporal modes. Most of these are  
 never used or even validated by gpu hardware vendors to do the right  
 thing. All the variations will have different effects on different types  
 of display panels, at different refresh rates and pixel densities, for  
 different types of still images or animations, so a panel with a true  
 native high bit depths is still a more deterministic thing that simulated  
 high bit depths. I would use dithering only for high level stimuli with  
 low spatial frequencies for that reason.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychAlpha/MeasureLuminancePrecision.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychAlpha/MeasureLuminancePrecision.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychAlpha/MeasureLuminancePrecision.m</code>
</div>

