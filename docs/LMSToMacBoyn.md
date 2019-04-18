# [LMSToMacBoyn](LMSToMacBoyn)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

ls = [LMSToMacBoyn](LMSToMacBoyn)(LMS,[T\_cones,T\_lum])  
  
Compute [MacLeod](MacLeod)-Boynton chromaticity from cone exciation coordinates.  
This is L/Lum and S/Lum, with appropriate normalization as described  
below. Recommended usage yields MB chromacities according to CIE 170-2:2015.  
  
\*\* Recommended Usage: Compute LMS with respect to some specified T\_cones,  
and pass both T\_cones as well as the cooresponding T\_lum (the photopic  
luminosity function.) T\_lum should be a linear combination of the L and M  
cone fundamentals.  
  
This routine will then scale passed L and M values so that they sum to  
the best linear approximation of luminance and then normalize the L  
excitation by luminance (as computed by the linear combination) to obtain  
the l chromaticity. It will normalize the S excitaiton by luminance to  
obtain s chromaticity, with an overall scaling so that the maximum value  
of this chromaticity is 1 taken over the visible spectrum.  
  
Note that the s cone scaling can vary a bit depending on the wavelength  
sampling of the passed T\_cones and T\_lum, since the max is taken over  
these. If you use the T\_cones\_ss2/T\_cones\_ss10 and T\_CIE\_Y2/T\_CIE\_Y10  
files provided in PTB, the default sampling is at 1 nm and this is fine.  
If you use subsampled wavelength spacing, the computation of the s cone  
scaling will begin to deviate from the standard.  But so will your  
computation of LMS values, so this isn't really an issue specific to this  
routine.  
  
When you use the CIE cone fundamentals and corresponding luminance  
functions, this procedure yields the [MacLeod](MacLeod)-Boynton chromaticity  
diagrams as specified in CIE 170-2:2015.  
  
\*\* Legacy Usage: Just pass LMS values. In this case, we assume that the  
passed LMS values were computed with respect to the Smith-Pokorny  
fundamentals normalized to a peak of 1 and Judd-Vos luminance (more or  
less).  That is, this usage assumes LMS was computed using the  
fundamentals stored in PTB's T\_cones\_sp. This is old usage and preserved  
for backwards compatibility, but the three argument usage as described  
above is preferred for clarity. Moreover, in this case, the s  
chromaticity is not further normalized.  This leads to S chromaticities  
considerably larger than those obtained with the new usage.  
  
\*\* A Backwards Incompatibility. The scaling for s chromaticity to match  
CIE 170-2:2015 was introduced in Janurary 2019 and is not backwards  
compatible with previous behavior when T\_cones and T\_lum are passed.  
Preserving such compatibility did not seem important enough relative to  
the gains of having this work as now specified in the CIE standard.  
  
10/30/97  dhb  Wrote it.  
7/9/02    dhb  T\_cones\_sp -\> T\_cones on line 20.  Thanks to Eiji Kimura.  
1/23/19   dhb  [Scale](Scale) s chromaticity value to be consistent with CIE  
               170-2:2015, when T\_cones and T\_lum are passed.  This is  
               not backwards compatible with previous scaling, but it  
               seems good to match the standard. Thanks to Danny Garside  
               for pointing out the scaling specified in the 2015  
               standard.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/LMSToMacBoyn.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/LMSToMacBoyn.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/LMSToMacBoyn.m</code>
</div>

