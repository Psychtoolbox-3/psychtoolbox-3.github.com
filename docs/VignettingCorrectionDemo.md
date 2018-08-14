# [VignettingCorrectionDemo](VignettingCorrectionDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Demonstrate how to do display devignetting aka per-pixel gain correction.  
  
Usage: [VignettingCorrectionDemo](VignettingCorrectionDemo)([docolor=0][, precision=max]);  
  
'docolor' if set to non-zero will compute and apply per-color channel  
gains instead of the default luminance gain.  
  
'precision' selects the precision vs. speed tradeoff: 2 = max precision,  
min speed, 1 = balanced, 0 = max speed and minimum precision.  
  
Because gain correction is memory and compute intense, per-color  
correction is slower than global luminance only correction. Higher  
precisions for the definition of the gainmatrix are slower, and higher  
display resolutions are slower.  
  
The demo runs until a key is hit twice.  
  
On modern graphics cards, Psychtoolbox allows to automatically apply a  
luminance- or color gainfield to all presented stimuli. Each pixel  
location can get individually gain corrected. This is useful to correct  
for spatial luminance or color inhomogenities of display devices, e.g.,  
video projectors (due to lens vignetting effects), or flat panels (with  
their contrast and color view dependency).  
  
You need recent graphics hardware for this to work and to work at a  
decent speed.  
  
See "help [PsychImaging](PsychImaging)" under subsection 'ColorCorrection' and "help  
[PsychColorCorrection](PsychColorCorrection)" under subsection 'GainMatrix' for explanation of  
the math, the parameters and other notable things of interest about gain  
correction.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VignettingCorrectionDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VignettingCorrectionDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VignettingCorrectionDemo.m</code>
</div>

