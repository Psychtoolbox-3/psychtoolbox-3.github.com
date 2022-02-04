# [DefaultPhotoreceptors](DefaultPhotoreceptors)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

photoreceptors = [DefaultPhotoreceptors](DefaultPhotoreceptors)(kind)  
  
Return a structure containing default sources   
for photoreceptor complements of various kinds.  
  
Available kinds  
  [LivingHumanFovea](LivingHumanFovea) (Default) - Human foveal cones in the eye  
  [CIE2Deg](CIE2Deg) - Leads to CIE 2-Deg fundamentals  
  [CIE10Deg](CIE10Deg) - Leads to CIE 10-Deg fundamentals  
  [LivingHumanMelanopsin](LivingHumanMelanopsin) - Most recent melanopsin spectral sensitivity in living eye.  
  [LivingHumanMelanopsinTsujimura2010](LivingHumanMelanopsinTsujimura2010) - Older estimate of melanopsin gc spectral sensitivity in living eye  
  [LivingDog](LivingDog) - Canine  
  [GuineaPig](GuineaPig) - Guinea pig in dish  
  
See also:  [FillInPhotoreceptors](FillInPhotoreceptors), [PrintPhotoreceptors](PrintPhotoreceptors), [RetIrradianceToIsoRecSec](RetIrradianceToIsoRecSec)  
 [IsomerizationsInEyeDemo](IsomerizationsInEyeDemo), [IsomerizationsInDishDemo](IsomerizationsInDishDemo), [ComputeCIEConeFundamentals](ComputeCIEConeFundamentals),  
 [RodFundamentalTest](RodFundamentalTest), [MelanopsinFundamentalTest](MelanopsinFundamentalTest).  
  
7/25/03  dhb  Wrote it.  
12/04/07 dhb  Added dog parameters  
8/14/11  dhb  Added fieldSizeDegrees and ageInYears fields to photoreceptors for [LivingHumanFovea](LivingHumanFovea) case.  
              These defaults match the CIE standard.  
4/20/12  dhb  Add [LivingHumanMelanopsin](LivingHumanMelanopsin)  
5/10/12  dhb  Changed name for [LivingHumanMelanopsin](LivingHumanMelanopsin) to postpend Tsujimura2010  
8/12/13  dhb  Change field order to make printouts look nicer.  
11/13/13 dhb  Add 'LivingHumanRod' and 'LivingHumanMelanopsin' options.  
5/26/14  dhb  Add pupilDimater.value = [] to fix [FillInPhotoreceptors](FillInPhotoreceptors).  
1/11/21  dhb  Comment tuning.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/DefaultPhotoreceptors.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/DefaultPhotoreceptors.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/DefaultPhotoreceptors.m</code>
</div>

