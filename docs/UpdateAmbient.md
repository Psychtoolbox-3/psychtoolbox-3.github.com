# [UpdateAmbient](UpdateAmbient)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

 cal = [UpdateAmbient](UpdateAmbient)(cal,newP\_ambient,[ADD])  
  
 Update the ambient light used in the conversions.  The  
 value of P\_ambient in the structure is replaced with the  
 passed value and the computed quantities that depend on  
 it are updated.  
  
 The ambient must be specified in the same measurement units as it  
 was in the cal at the initial call to [SetColorSpace](SetColorSpace).  If different  
 units are desired, all ambient fields in the structure must be updated  
 and [SetColorSpace](SetColorSpace) called again.  I have never wanted to do this,  
 so I haven't written a separate routine.  
  
 It is sometimes useful, however, to update the ambient in the  
 linear color space defined by the call to [SetColorSpace](SetColorSpace).  To  
 do this, use [UpdateAmbientLinear](UpdateAmbientLinear).  
  
 If flag ADD is true, passed ambient is added to current  
 value.  Otherwise passed value replaces current value.  
 ADD is false if not passed.  Use caution when setting ADD  
 true -- if the ambient is changing during the experiment  
 you typically don't want to keep adding multiple times.  
  
 11/17/93  dhb      Wrote it.  
 8/4/96    dhb   Updated for modern scheme.  
 8/21/97   dhb   Update for structures.  
 3/2/98     dhb     Fix bug in checks introduce 8/21/97, pointed out by dgp.  
 3/10/98        dhb     Change T\_ to P\_.  
 10/26/99  dhb, mdr  Fix bug in checks. There was also a variable name  
                                    glitch.  I don't think this could have worked the way  
                                    it was.  Perhaps no one calls it.  
 5/2/02    dhb, kr  Add ADD flag.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/UpdateAmbient.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/UpdateAmbient.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/UpdateAmbient.m</code>
</div>

