# [DegreesToRetinalMM](DegreesToRetinalMM)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

 mm = [DegreesToRetinalMM](DegreesToRetinalMM)(degs,eyeLengthMM,[fulltrig])  
  
Convert foveal extent in degrees to mm of retina in the fovea.  
  
This is implemented by default as a simple linear scaling based on the  
appropriate conversion for small angles.  It does not take the  
non-linearity of the tangent for larger angles into account, nor the  
actual shape and optics of the eye.  Interestingly, although the trig  
calculation would be exactly correct for pinhole camera and a planar  
retina oriented orthogonal to the optical axis, it deviates more from  
what the real eye does than the linear approximation.  
  
In addition, this routine and [RetinalMMToDegrees](RetinalMMToDegrees) are implemented as the  
exact inverses of each other in this default mode.  
  
If optional argument fulltrig is passed as true (it is false by default),  
then it uses the inverse tangent on the actuall passed mm.  This was the  
behavior prior to July 2015. This behavior does not exactly self invert  
with [RetinalMMToDegrees](RetinalMMToDegrees).  Nor does it account for the shape and optics of  
the eye.  
  
Routine [EyeLength](EyeLength) returns posterior nodal eye lengths for various species  
and sources.  Use 'Human' and 'Rodieck' to get the eye lenght implicit in  
[RetinalEccentricityMMToDegrees](RetinalEccentricityMMToDegrees) and [DegreesToRetinalEccentricityMM](DegreesToRetinalEccentricityMM) for  
human, and similarly 'Rhesus' and 'PerryCowey' for rhesus.  
  
See also: [RetinalMMToDegrees](RetinalMMToDegrees), [EyeLength](EyeLength), [RetinalEccentricityMMToDegrees](RetinalEccentricityMMToDegrees), [DegreesToRetinalEccentricityMM](DegreesToRetinalEccentricityMM)  
  
7/15/03  dhb  Wrote it.  
7/01/15  dhb  Update comments, change default behavior, preserve old behavior optionally.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/DegreesToRetinalMM.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/DegreesToRetinalMM.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/DegreesToRetinalMM.m</code>
</div>

