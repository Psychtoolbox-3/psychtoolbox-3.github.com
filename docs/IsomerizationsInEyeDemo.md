# [IsomerizationsInEyeDemo](IsomerizationsInEyeDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[IsomerizationsInEyeDemo](IsomerizationsInEyeDemo)  
  
Shows how to compute photoreceptor isomerizations using toolbox  
routines.  These calculations are for the human eye,  
starting with a spectrum as measured by the PR-650  
in watts/sr-m^2-wlinterval, or with a relative spectrum  
and a photopic troland value.  
  
NOTE, DHB, 7/19/13. This demo routine and its associated data routines   
[(DefaultPhotoreceptors]((DefaultPhotoreceptors), [FillInPhotoreceptors](FillInPhotoreceptors), [PrintPhotoreceptors)](PrintPhotoreceptors))  
should be better integrated with the more recent code that  
implements the CIE physiological cone fundamentals, and the  
whole set of stuff should be better documented.  See also  
   [IsomerizationsInDishDemo](IsomerizationsInDishDemo)  
   [CIEConeFundamentalsTest](CIEConeFundamentalsTest)  
   [ComputeCIEConeFundamentals](ComputeCIEConeFundamentals)  
   [ComputeRawConeFundamentals](ComputeRawConeFundamentals)  
   [DefaultPhotoreceptors](DefaultPhotoreceptors)  
   [FillInPhotoreceptors](FillInPhotoreceptors)  
   [PrintPhotoreceptors](PrintPhotoreceptors)  
   [RetIrradianceToIsoRecSec](RetIrradianceToIsoRecSec)  
In particular, there should be some default for the   
photoreceptors structure that gives one the CIE cone  
fundamentals in all their parametric glory, plus additional  
parameters that yield real energy/quantal sensitivites so  
that the resulting coordinates are isomerization rates in  
real units.  I think that we're close to having that, but  
better documentation and tidying is needed.  
  
07/08/03 dhb  Wrote starting from [IsomerizationsInDishDemo](IsomerizationsInDishDemo).  
07/11/03 dhb  Grab data through subroutines.  Get rid of integration time.  
07/15/03 dhb  Take eye size from function.  
08/14/11 dhb  Comment out saving of T\_dogrec at end.  Want to be careful when and where  
              this is done, but the template may be useful someday.  
03/20/12 dhb  Update cal file for PTB 3.  
04/09/12 dhb  Add test of irradiance to troland conversion.  
04/27/13 dhb  More extensive comments.  
7/19/13  dhb  Print out photoreceptors structure using [PrintPhotoreceptors](PrintPhotoreceptors).  
         dhb  Add monochromatic light option to the section that starts with trolands.  
8/11/13  dhb  Add test of [AborbtanceToAbsorbance](AborbtanceToAbsorbance).  
         dhb  Protect against case when absorbance is provided directly.  
05/26/14 dhb  Dusted off.  
6/10/14  npc, dhb  Modifications for accessing calibration data using a @[CalStruct](CalStruct) object.  
7/7/14   dhb  Make calStruct object code conditional on the support routines existing on the path.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/IsomerizationsInEyeDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/IsomerizationsInEyeDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/IsomerizationsInEyeDemo.m</code>
</div>

