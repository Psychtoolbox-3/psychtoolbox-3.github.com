# [AlphaBlendingTest](AlphaBlendingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[AlphaBlendingTest](AlphaBlendingTest)([screenNumber])  
  
Perform tests of [OpenGL](OpenGL) alpha blending by drawing to the screen using  
'PutImage', reading back the actual values on the [Screen](Screen) using  
'GetImage' and comparing the actual values to predicted values  
calcualated in MATLAB.  
  
[AlphaBlendingTest](AlphaBlendingTest) combines tests implemented separately.  You may perform  
any of these tests individually, or call [AlphaBlendingTest](AlphaBlendingTest) to perform  
them all:  
  
[AlphaBlendSettingTest](AlphaBlendSettingTest) -   
  Test the [Screen](Screen)('BlendFunction') recalls previously stored  
  alpha values.  
  
[AlphaMultiplicationTest](AlphaMultiplicationTest) -  
  Test that alpha multiplication by values 0 and 1 ([Screen](Screen) 255) works  
  with perfect precision.  [OpenGL](OpenGL) guarantees perfect precision for those  
  alpha values only.  
  
[AlphaMultiplicationAccuracyTest](AlphaMultiplicationAccuracyTest) -   
  Measure the precision of alpha values between 0 and 1 ([Screen](Screen) 0 and 255) by  
  drawing to the screen, then taking the difference between what was  
  drawn to the screen and results of simulated blending done with  
  double-precision floats.      
  
[AlphaAdditionTest](AlphaAdditionTest) -   
  Test that addition of source and destination terms has perfect  
  precision.      




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/AlphaBlendingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/AlphaBlendingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/AlphaBlendingTest.m</code>
</div>

