# [AbsorptanceToAbsorbance](AbsorptanceToAbsorbance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[absorbanceSpectra, absorbanceSpectraWls] =...  
  [AbsorptanceToAbsorbance](AbsorptanceToAbsorbance)(absorptanceSpectra, absorptanceSpectraWls, axialOpticalDensities, [NORMALIZE])  
  
This code inverts [AbsorbanceToAbsorptance](AbsorbanceToAbsorptance).  You might want to do this if you were trying  
to take cone fundamentals and back down all the way to the component parts, so that you  
could for example vary the axial density and recompute the fundamentals.  
  
The absorbance/absorptance terminology is described at the  
CVRL web page, http://cvrl.ucl.ac.uk.  Wyszecki and Stiles refere to absorbance  
the absorption coefficient (p. 588).  
  
Both absorptance spectra and absorbance spectra describe quantal absorption.  
  
Absorbance spectra are normalized to a peak value of 1.  
Absorptance spectra are the proportion of quanta actually absorbed.  
  
Equation: absorptanceSpectra = 1 - 10.^(-OD \* absorbanceSpectra)  
  
Multiple spectra may be passed in the rows of absorbanceSpectra.  If  
so, then the same number of densities should be passed in the vector  
axialOpticalDensities, and multiple answers are returned in the rows  
of absorptanceSpectra.  
  
NORMALIZE (default true) causes this routine to normalize the returned absorbances to  
have a maximum of 1.  
  
Note, we now have ways of building up most fundamentals that we care about  
from constituant parts, and thus probably don't need to do that.  See  
  [CIEConeConeFundamentlsTest](CIEConeConeFundamentlsTest), [ComputeCIEConeFundamentals](ComputeCIEConeFundamentals), [DefaultPhotoreceptors](DefaultPhotoreceptors), [FillInPhotoreceptors](FillInPhotoreceptors),  
  [IsomerizationsInEyeDemo](IsomerizationsInEyeDemo).  
  
Originally written by HH, Copyright HH, Vista Lab, 2010  
  
8/11/13  dhb  Moved into PTB, modified comments so as not to refer to non-PTB routines.  
         dhb  That this actually inverts is tested in [IsomerizationsInEyeDemo](IsomerizationsInEyeDemo).  
12/02/13 dhb  Fix spelling of "absorptance" in routine names and throughout.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/AbsorptanceToAbsorbance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/AbsorptanceToAbsorbance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/AbsorptanceToAbsorbance.m</code>
</div>

