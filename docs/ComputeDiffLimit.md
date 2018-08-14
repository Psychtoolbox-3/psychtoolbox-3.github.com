# [ComputeDiffLimit](ComputeDiffLimit)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOptics](PsychOptics)

s0 = [ComputeDiffLimit](ComputeDiffLimit)(pupil,nm)  
  
Compute the diffraction limit for coherent light.  
(For incoherent light the answer is 2\*s0.)  
See page 120 in Goodman.   
  
    "pupil" diameter in mm  
    "nm" is wavelength in nm  
    "s0" is highest spatial frequency passed by the pupil in cycles/deg  
  
Goodman, J. W. (1968) Introduction to Fourier Optics.   
San Francisco: [McGraw](McGraw)-Hill. Page 120.  
  
Goodman's formula involves di, which I think is the distance to the  
image. Goodman's formula gives the limit in  
cycles/unit length.   The formula below gives  
the answer in cycles/degree.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOptics/ComputeDiffLimit.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOptics/ComputeDiffLimit.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOptics/ComputeDiffLimit.m</code>
</div>

