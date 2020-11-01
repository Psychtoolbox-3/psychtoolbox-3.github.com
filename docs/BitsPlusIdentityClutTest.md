# [BitsPlusIdentityClutTest](BitsPlusIdentityClutTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)>[BitsPlusTests](BitsPlusTests)

Test signal transmission from the framebuffer to your CRS Bits+/Bits\#  
device or [VPixx](VPixx) Inc. [DataPixx](DataPixx)/[ViewPixx](ViewPixx)/Propixx device and similar CRS and  
[VPixx](VPixx) products.  
  
Test proper function of the T-Lock mechanism on CRS devices and PSYNC  
mechanism on [VPixx](VPixx) devices, as well as proper loading of identity gamma  
tables into the GPU, and for bad interference of dithering hardware  
with the DVI stream. This test is meant for Mono++ mode of Bits+/Bits\# or  
M16 mode of [DataPixx](DataPixx), [ViewPixx](ViewPixx), [ProPixx](ProPixx). It requires a modern graphics card  
which supports at least [OpenGL](OpenGL)-2.1 and therefore supports these modes.  
  
If you only have older graphics hardware that can only drive Bits++ or  
L48 clut display mode, or you have an old CRS Bits+ device switched to  
Bits++ mode and don't want the hassle of setting it to Mono++ mode then  
this test script can also perform a slightly more limited test in Bits++  
mode or L48 clut mode. Set the optional parameter 'useclutmodeonly' to 1  
to use this simpler test mode.  
  
Disclaimer: This test only exists because of the huge number of serious &  
embarassing bugs in the graphics drivers and operating systems from  
Microsoft, Apple, AMD and [NVidia](NVidia). All problems diagnosed here are neither  
defects in the Bits+ device or similar devices, nor Psychtoolbox bugs. As  
such, sadly they are mostly out of our control and there is only a  
limited number of ways we can try to help you to workaround the problems  
caused by miserable workmanship and insufficient quality control at those  
big companies.  
  
### Usage:  
  
[BitsPlusIdentityClutTest](BitsPlusIdentityClutTest)([whichScreen=max][, usedpixx=0][, winrect=[]][, useclutmodeonly=0][, useVulkan=0]);  
  
### How to test:  
  
1. Make sure your Bits+ box is switched to Mono++ mode by uploading the  
   proper firmware. Or make sure your [DataPixx](DataPixx)/[ViewPixx](ViewPixx)/[ProPixx](ProPixx) or CRS  
   Bits\# is connected, both DVI cable and USB cable. Alternatively set  
   'useclutmodeonly' to 1 to test in Bits++ mode on a CRS device or L48  
   mode on a [VPixx](VPixx) device. In useclutmodeonly = 1 case, skip to step 3.  
  
2. Run the [BitsPlusImagingPipelineTest](BitsPlusImagingPipelineTest) script to validate that your  
   graphics card can create properly formatted images in the framebuffer  
   for Bits+/Bits\# or [DataPixx](DataPixx)/[ViewPixx](ViewPixx)/[ProPixx](ProPixx).  
  
3. Run this script, optionally passing a screenid. It will test the  
   secondary display on a multi-display setup by default, or the external  
   display on a laptop. For a [DataPixx](DataPixx) device or similar, set the  
   optional 'usedpixx' flag to 1. Set 'useclutmodeonly' flag to 1 if you  
   want to test in Bits++ or L48 mode instead of Mono++ or M16 mode.  
  
'useVulkan' Defaults to 0. If set to 1, use Vulkan display  
backend, instead of standard [OpenGL](OpenGL) backend.  
  
If everything works, what you see onscreen should match the description  
in the blue text that is displayed.  
  
If a wrong gamma lut is uploaded into your GPU due to operating system  
and graphics driver bugs, you can try to toggle through different  
alternative lut's by repeatedly pressing the SPACE key and seeing if the  
display changes for the better. Should you find a setting that works, you  
can press the 's' key to save this configuration and Psychtoolbox will  
use this setting in all future sessions of your experiment scripts.  
  
You can exit the test by pressing the [ESCape](ESCape) key, regardless if it was  
successfull or not. The test will then ask you if you rate the results  
as success or failure and use your feedback for further operation.  
  
What could also happen is that you get a partial success: The display  
behaves roughly as described in the text, but you see the T-Lock color  
code line at the top of your display erratically appearing and  
disappearing - flickering. You also don't see a smooth animation of the  
drifting horizontal red gradient or a regular cycling of the "COLORFUL"  
words, but some jerky, irregular, jumpy animation, which may only update  
a few times per second, or even only once every couple seconds or at very  
irregular intervals. You may also see the display overlayed with random  
colorful speckles, or you may not see the gray background image and gray  
rotating gradient patch at all. In that case, the lut uploaded in your  
GPU may be correct, but due to some serious graphics driver or operating  
system bug, the GPU is applying spatial or temporal dithering to the  
video stream which will confuse your display device and cause random  
artifacts and failure of the T-Lock or PSYNC mechanism, as well as display  
of wrong or inaccurate color or luminance values!  
  
You should also double-check the cabling and connections to rule out  
connection problems and other defects.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusIdentityClutTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusIdentityClutTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusIdentityClutTest.m</code>
</div>

