# [RetinalEccentricityMMToDegrees](RetinalEccentricityMMToDegrees)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

eccMm = [DegreesToRetinalEccentricityMM](DegreesToRetinalEccentricityMM)(eccDegrees,[species],[method],[eyeLengthMm])  
  
Convert eccentricity in degrees to retinal eccentricity in mm.  By  
default, this takes into account a simple model eye, rather than just  
relying on a linear small angle approximation.  
  
Input:  
  eccDegrees -- retinal eccentricity in degrees  
  species -- what species  
    'Human'  -- Human eye [default]  
    'Rhesus' -- Rhesus monkey  
  method -- what method  
    'DaceyPeterson'  -- formulae from Dacey & Peterson (1992) [default]  
    'Linear' -- linear, based on small angle approx  
 eyeLengthMm -- Eye length to assume for linear calculation, should be  
     the posterior nodal distance. Defaults to the default values returned  
     by function [EyeLength](EyeLength) for the chosen species.  
  
The Dacey and Peterson formulae are based on digitizing and fitting  
curves published by  
   1) Drasdo and Fowler, 1974 (British J. Opthth, 58,pp. 709 ff., Figure 2,  
   for human.  
   2) Perry and Cowey (1985, Vision Reserch, 25, pp. 1795-1810, Figure 4,  
   for rhesus monkey.  
These curves, I think, were produced by ray tracing or otherwise solving  
model eyes.  
  
The default eye length returned by [EyeLength](EyeLength) for Human is currently the Rodiek value of  
16.1 mm.  Drasdo and Fowler formulae are based on a length of about this,   
so the linear and [DaceyPeterson](DaceyPeterson) methods are roughly consistent for small  
angles.  Similarly with the Rhesus default.  Using other EyeLength's will  
make the two methods inconsistent.  
  
The Dacey and Peterson equations don't go through (0,0), but rather  
produce a visual angle of 0.1 degree for an eccentricity of 0.  This  
seems bad to me. I modified the formulae so that they use the linear  
approximation for small angles, producing a result that does go through  
(0,0).  This may be related to the fact that there is some ambiguity in  
the papers between whether the center should be thought of as the fovea  
or the center of the optical axis.  But I think this difference is small  
enough that the same formulae would apply across such a shift in origin.  
  
I digitized Drasdo and Fowler Figure 2 and compared it to what  
[DegreesToRetinalEccentricity](DegreesToRetinalEccentricity) produces.  I'd call agreement so-so, but  
considerably better than what the linear approximation produces.  One  
could probably do better, but my intuition is that the deviations are  
small compared to eye to eye differences and differences that would be  
produced by different model eyes, so that juice isn't worth the squeeze.  
I pasted my digitization at the end of [DegreesToRetinalEccentricity](DegreesToRetinalEccentricity) if  
anyone wants to fuss with this.  But probably if you're going to do that,  
you should do the whole ray tracing thing with our best current model  
eye.  
  
I have not checked the fit to the Perrry and Cowey curve for Rhesus  
against a digitization of that figure.  
  
See also: [EyeLength](EyeLength), [DegreesToRetinalEccentricityMM](DegreesToRetinalEccentricityMM), [DegreesToRetinalMM](DegreesToRetinalMM), [RetinalMMToDegrees](RetinalMMToDegrees)  
  
6/30/2015  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/RetinalEccentricityMMToDegrees.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/RetinalEccentricityMMToDegrees.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/RetinalEccentricityMMToDegrees.m</code>
</div>

