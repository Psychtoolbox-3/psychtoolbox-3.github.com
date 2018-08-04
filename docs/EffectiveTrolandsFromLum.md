# [EffectiveTrolandsFromLum](EffectiveTrolandsFromLum)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

 [trolands] = [EffectiveTrolandsFromLum](EffectiveTrolandsFromLum)(lum,[method])  
  
 Compute effective trolands for large fields from photopic  
 luminance.  Based on LeGrand's work, takes Stiles-Crawford  
 effect into account.  
  
 Luminance is in cd/m2.  
  
 Method (string):  
   [PokornySmith1](PokornySmith1): (default)  
            Formula is Eq. 2 from: Pokorny and Smith, "How much light  
            reaches the retina", Colour Vision Deficiences XIII (C.  
            Cavonius, ed.), pp. 491-511.  The formula in the paper  
     has some typos, corrections provided to me by Pokorny.  
  
        [PokornySmith2](PokornySmith2):  
            Formula is Eq. 3 from: Pokorny and Smith, "How much light  
            reaches the retina", Colour Vision Deficiences XIII (C.  
            Cavonius, ed.), pp. 491-511.  Conversion to and from log  
     done here so input/output is same as above.  
  
 The agreement between the two methods is not spectacular.  See [PupilDiameterTest](PupilDiameterTest).  
  
 5/8/99  dhb  Wrote it.  
 7/11/03 dhb  More general method naming.   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/EffectiveTrolandsFromLum.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/EffectiveTrolandsFromLum.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/EffectiveTrolandsFromLum.m</code>
</div>

