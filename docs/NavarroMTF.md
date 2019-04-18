# [NavarroMTF](NavarroMTF)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOptics](PsychOptics)

NAVARROMTF  Compute the MTF measured by Navarror, Artal and Williams  
   mtf = NAVARRORMTF(s)  
  
   Compute the MTF measured by Navarro et al. The MTF was measured for a  
   4 mm pupil, and for a varietry of eccentricities. We return the foveal  
   MTF by default.  The desired eccentricity can be passed as a key-value  
   pair, i.e., mtf10deg = [NavarroMTF](NavarroMTF)(1:60, 'eccentricity', '10 deg')  
  
   Navarro, R., Artal, P., & Williams, D. R. (1993).   
   Modulation transfer function of the human eye as a function of retinal   
   eccentricity. Journal of the Optical Society of America A, 10, 201?212.  
  
   Spatial frequency passed in cycles/deg.  
  
   See also WILLIAMSMTF, OTFTOPSF, WILLIAMSRESTMTF, DIFFRACTIONMTF,  
   WILLIAMSTABULATEDPSF, PSYCHOPTICSTEST.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOptics/NavarroMTF.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOptics/NavarroMTF.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOptics/NavarroMTF.m</code>
</div>

