# [RetinalMMToDegrees](RetinalMMToDegrees)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

degs = [RetinalMMToDegrees](RetinalMMToDegrees)(mm,eyeLengthMM,[fulltrig])  
  
Convert fovela extent in mm of retina in the fovea to degrees of visual  
angle.  
  
This is implemented by default as a simple linear scaling based on the  
appropriate conversion for small angles.  It does not take the  
non-linearity of the tangent for larger angles into account, nor the  
actual shape and optics of the eye.  Interestingly, although the trig  
calculation would be exactly correct for pinhole camera and a planar  
retina oriented orthogonal to the optical axis, it deviates more from  
what the real eye does than the linear approximation.  
  
In addition, this routine is implemented as the exact inverse of what  
[DegreesToRetinalMM](DegreesToRetinalMM) does, rather than having the two routines do  
independent forward and backward linear approximations.  
  
If optional argument fulltrig is passed as true (it is false by default),  
then it uses the inverse tangent on the actuall passed mm.  This was the  
behavior prior to July 2015. This behavior does not exactly self invert  
with [DegreesToRetinalMM](DegreesToRetinalMM).  Nor does it account for the shape and optics of  
the eye.  
  
Routine [EyeLength](EyeLength) returns posterior nodal eye lengths for various species  
and sources.  Use 'Human' and 'Rodieck' to get the eye lenght implicit in  
[RetinalEccentricityMMToDegrees](RetinalEccentricityMMToDegrees) and [DegreesToRetinalEccentricityMM](DegreesToRetinalEccentricityMM) for  
human, and similarly 'Rhesus' and 'PerryCowey' for rhesus.  
  
See also: [DegreesToRetinalMM](DegreesToRetinalMM), [EyeLength](EyeLength), [RetinalEccentricityMMToDegrees](RetinalEccentricityMMToDegrees), [DegreesToRetinalEccentricityMM](DegreesToRetinalEccentricityMM)  
  
7/15/03  dhb  Wrote it.  
7/01/15  dhb  Update comments, change default behavior, preserve old behavior optionally.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/RetinalMMToDegrees.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/RetinalMMToDegrees.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/RetinalMMToDegrees.m</code>
</div>

