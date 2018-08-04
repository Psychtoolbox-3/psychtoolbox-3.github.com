# [MinimumMotionExp](MinimumMotionExp)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[PsychExampleExperiments](PsychExampleExperiments)

[MinimumMotionExp](MinimumMotionExp)([writeResult=0])  
  
Minimum motion luminance measurement (Anstis and Cavanagh). Rapid,  
precise, and works well down to 1hz, or 1  cpd. Self-contained script,  
with optional gamma file input or default.  
  
Measures red/green and blue/green foveal or extrafoveal equiluminance  
using the Cavanagh, [MacLeod](MacLeod) and Anstis (1987) sinusoidal minimum motion  
stimulus, here drawn as a windmill.  
  
One component of the test stimulus is a rotary sine wave where peaks of 1  
phosphor coincide with troughs of a second phosphor. This is counterphase  
modulated in cosine phase is space and time. A "luminance lure" grating  
is added in spatial and temporal quadrature (sine phase). The stimulus  
appears in clockwise or anticlockwise motion, depending on the relative  
luminance of two phosphors. The ratio of the two phosphor intensities is  
adjusted using the mouse. The isoluminant point is the precise point  
where the motion direction changes, and there the motion is replaced by  
counterphase flicker. User selects whether to measure the red phosphor  
luminance relative to the green, the blue phosphor luminance relative to  
the green, or the blue phosphor luminance relative to the red. Reported  
values are the ratios of phosphor luminances when each phosphor is at  
maximum intensity. Average stimulus chromaticity and luminance are kept  
constant during the adjustment.  
  
The stimulus is produced by clut animation (palette mode). If BPP is  
nonzero, we assume that DVI video output is relayed to the monitor via a  
CRS [BitsPlusPlus](BitsPlusPlus) device, or via a [DataPixx](DataPixx)/[ViewPixx](ViewPixx) device allowing fine  
control of modulation depths and corresponding precision in luminance  
estimates. Otherwise set BPP to zero. In either case, Psychophysics  
Toolbox 3 and Matlab 7.4 or later (or Octave 3.2 or later) are required.  
  
Note: Writing of result files is disabled, but can be enabled in a  
"production setting" by providing the optional argument 'writeResult' as  
1.  
  
This script is contributed by Don [MacLeod](MacLeod), UCSD. It was modified by Mario  
Kleiner for portability across all supported operating systems and for  
optimized speed.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PsychExampleExperiments/MinimumMotionExp.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PsychExampleExperiments/MinimumMotionExp.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PsychExampleExperiments/MinimumMotionExp.m</code>
</div>

