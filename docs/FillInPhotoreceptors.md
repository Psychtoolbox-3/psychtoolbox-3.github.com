# [FillInPhotoreceptors](FillInPhotoreceptors)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

photoreceptors = [FillInPhotoreceptors](FillInPhotoreceptors)(photoreceptors)  
  
Convert all source strings in a photoreceptors structures  
to numerical values, so that the result is ready to compute  
on.  
  
### The typical usage of this routine would be:  
  
  clear photoreceptors  
  photoreceptors = [DefaultPhotoreceptors](DefaultPhotoreceptors)('LivingHumanFovea');  
  ... statements here set value fields, to override default values  
      that are either filled in from source or that we directly set.  
  photoreceptors = [FillInPhotoreceptors](FillInPhotoreceptors);  
  
Values supplied for fields that could be computed from other fields  
override the computed values, with those computed later in the code  
taking precedence over those computed earlier.  As of August, 2013  
a fair number of checks are in place to throw an error if you  
try to override a value that could have been computed from other passed  
parameters.  
  
This routine does not deal with filling in the pupil diameter field of the photoreceptors  
structure, which might be a mistake.  Pupil diameter is now used in the CIE calculations  
for lens density.  So perhaps this routine should fill in pupil diameter value of it  
doesn't exist. The problem is that computing pupil diameter from a source requires  
knowing the luminance of the stimulus, and this routine definitely does not want  
to know that.  So perhaps what should happen here is just a check that values needed  
exist.  See [PupilDiameterFromLuminance](PupilDiameterFromLuminance) if you are interested in knowing how pupil  
diameter might be determined given luminance.  
  
There are some useful comments towards the end of this routine about how to compute  
isomerizations from the absorptances that this routine produces.  
  
See also: [DefaultPhotoreceptors](DefaultPhotoreceptors), [RetIrradianceToIsoRecSec](RetIrradianceToIsoRecSec)  
  [IsomerizationsInEyeDemo](IsomerizationsInEyeDemo), [IsomerizationsInDishDemo](IsomerizationsInDishDemo), [ComputeCIEConeFundamentals](ComputeCIEConeFundamentals),  
  [CIEConeFundamentalsTest](CIEConeFundamentalsTest), [PrintPhotoreceptors](PrintPhotoreceptors).  
  
7/25/03  dhb  Wrote it.  
8/14/11  dhb  Allow pass through of field size, pupil diameter, and age.  
              Try not to break old code in how this is handled.  
4/26/12  dhb  Return density as well as transmittance for lens and macular pigment.  
8/9/13   dhb  Bulletproofing, by putting in a lot more consistency checks, and requiring  
              the calling program not to pass inconsistent information (e.g., you can't pass  
              a nomogram and an absorbance spectrum.)  
8/11/13  dhb  More checking.  Add ability to adjust lens/macular density.  Return energy and quantal fundamentals (normalized to unity).  
8/12/13  dhb  Fixed buglet resulting from forgetting to update after copy/paste.  
10/16/13  mk  [Replace](Replace) obsolete isstr() by ischar() to future-proof this.  
5/24/14  dhb  Compute axialDensity.bleachedValue by fractionPigmentBleached.value field, if the latter exists.  
              This is set to the axialDensity.value field if no bleaching is provided.  The bleachedValue number is  
              then passed to [AbsorbanceToAbsorptance](AbsorbanceToAbsorptance).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/FillInPhotoreceptors.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/FillInPhotoreceptors.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/FillInPhotoreceptors.m</code>
</div>

