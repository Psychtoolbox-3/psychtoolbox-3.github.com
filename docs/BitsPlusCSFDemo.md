# [BitsPlusCSFDemo](BitsPlusCSFDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)>[BitsPlusDemos](BitsPlusDemos)

[BitsPlusCSFDemo](BitsPlusCSFDemo)([screenid=max] [, gamma = 2.2][, method=0][, charttype=0])  
  
Demonstrates advantage of the 14 bpc Mono++ display mode, and similar high  
bit depths display modes over the standard 8 bpc display mode of standard  
graphics hardware. The demo displays either the Campbell-Robson CSF chart  
if you set 'charttype' == 0, or a linear intensity gradient, if you set  
'charttype' == 1. By default, the CSF chart is shown.  
  
The optional 'method' argument selects among different display output  
modes:  
  
A 'method' of 0 outputs to a regular 8 bit framebuffer. This is the  
default, if no method argument is provided.  
  
A 'method' of 1 tries to utilize the native 10 bpc framebuffers of modern  
hardware.  
  
A 'method' of 2 uses a method known as "[PseudoGray](PseudoGray)" or "Bitstealing" for  
output.  
  
In 'method' == 3, the Mono++ display mode of the Bits++ box is used.  
  
A 'method' == 4 uses the Xiangrui Li et al. "[VideoSwitcher](VideoSwitcher)", video  
attenuator device.  
  
In 'method' == 5, the M16 display mode of the [VPixx](VPixx) - [DataPixx](DataPixx) box is used.  
  
A 'method' of 6 tries to utilize the native ~11 bpc framebuffers of  
modern AMD hardware with DCE display engines on Linux.  
  
A 'method' of 7 tries to utilize the native up to 16 bpc framebuffers of  
modern AMD hardware.  
  
A 'method' of 8 tries to utilize the native 16 bpc float framebuffers of recent  
hardware.  
  
The optional 'gamma' parameter allows to select the initial gamma value  
of your display to correct for. This can be changed interactively later  
on.  
  
The optional 'screenid' parameter allows to select the id of the output  
display on multi-display setups. By default, the secondary display is  
chosen.  
  
# Keyboard control keys  
  
At each press of space key, the display alternates between a high bpc  
version and a 8 bpc version to hopefully show a perceptible difference in  
contrast resolution. The [ESCape](ESCape) key exits the demo.  
  
The left- and right cursor keys allow you to change the gamma-correction  
setting. The demo starts with standard power-function gamma correction  
for a display with gamma 2.2, i.e., out = in ^ (1/gamma) with gamma =  
2.2.  
  
This demo is derived from a similar demo (written in C) which is part of  
the sample code collection for Bits++ from Cambridge Research Systems  
support website. It mostly replicates that C sample, however there are  
small differences.  
  
The original description of the CSF chart seems to be in (not checked):  
Campbell, F. W. and Robson, J. G. (1968) Application of Fourier analysis  
to the visibility of gratings. Journal of Physiology (London) 197:  
551-566.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusDemos/BitsPlusCSFDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusDemos/BitsPlusCSFDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusDemos/BitsPlusCSFDemo.m</code>
</div>

