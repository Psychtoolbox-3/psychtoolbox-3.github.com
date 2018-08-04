# [AlphaMultiplicationTest](AlphaMultiplicationTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

passedFlag=[AlphaMultipicationTest](AlphaMultipicationTest)([screenNumber])  
  
### [AlphaMultiplicationTest](AlphaMultiplicationTest):   
  
    Test for perfect alpha multiplication precision for alpha values 0 and  
    1. [OpenGL](OpenGL) guarantees precise alpha muliplicaion for only those alpha  
    values. [TestTestAlphaMultipicationAlphaTimes](TestTestAlphaMultipicationAlphaTimes) tests that guarantee.   
  
    Test all alpha modes in all combinations.  This verifies that [Screen](Screen) sets  
    modes properly  
  
Note that [Screen](Screen) alpha values fall in the range 0-255 while [OpenGL](OpenGL) alpha  
values are normalized between 0-1; [OpenGL](OpenGL) alpha value 1 is equivalent to  
[Screen](Screen) alpha value 255.  
  
If no return argument is provided, then [AlphaMultiplicationTest](AlphaMultiplicationTest) issues an error  
when a test fails.  If a return argument is supplied then it signals a  
failed test only by returning true, without issuing an error.    
  
See also: [AlphaBlendingTest](AlphaBlendingTest), [PsychAlphaBlending](PsychAlphaBlending)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/AlphaMultiplicationTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/AlphaMultiplicationTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/AlphaMultiplicationTest.m</code>
</div>

