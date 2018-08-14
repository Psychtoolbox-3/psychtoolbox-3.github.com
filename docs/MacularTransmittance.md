# [MacularTransmittance](MacularTransmittance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

[macTransmit,macDensity] = [MacularTransmittance](MacularTransmittance)(S,[species],[source],[fieldSizeDegrees])  
  
Return an estimate of the transmittance of the macular pigment transmittance  
as a function of wavelength.  
  
Allowable species:  
  Human (Default)  
  
Allowable sources:  
  CIE (Default)            - CIE 170-1:2006 values.  
  Bone                     - From Bone et al.  See CVRL database.  
  [WyszeckiStiles](WyszeckiStiles)           - From W&S, Table 2(2.4.6), p. 112.  
  Vos                      - From Vos.  See CVRL database.  
  None                     - Unity transmittance.  
  
For the CIE option, can pass fieldSizeDegrees [Default 2 degrees].  
This was buggy until the version of 5/8/12.  
  
The Bone values that we use a the basis for this calculation  
match those in  CIE 170-1:2006, Table 6.4 for a 2-degree observer.  
  
The answer is returned in a row vector.  This function  
depends on data contained in directory  
[PsychColorimetricData](PsychColorimetricData):[PsychColorimetricMatFiles](PsychColorimetricMatFiles).  
  
7/8/03  dhb  Made this a separate function.  
7/11/03 dhb  Species arg, change name.  
7/23/03 dhb  Change default.  
7/26/03 dhb  Extend functions, rather than zero truncate.  
8/12/11 dhb  Fixed default to match comments.  
        dhb  Add CIE option and made it default.  
        dhb  For CIE, can pass field size  
        dhb  Also return density  
8/13/11 dhb  Linearly extrapolate read functions outside of range.  
5/8/12  dhb  Fixed two bugs.  First, peak optical density correction is  
             multiplicative rather than additive.  Second, there was  
             an operator precedence grouping error in the computation  
             of the correction factor.  
5/8/12  dhb  Removed comment that we can't reproduce CIE tabular 10 deg values.  
9/17/12 dhb  Return density for 'None' case as well.  
8/9/13  dhb  More consistent returning of density for 'None' case.  
8/11/13 dhb  Try to make dimensions of returned density match those of returned transmittance.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/MacularTransmittance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/MacularTransmittance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/MacularTransmittance.m</code>
</div>

