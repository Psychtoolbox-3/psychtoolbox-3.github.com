# [JuddVosToSmithPokorny](JuddVosToSmithPokorny)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

[T\_cones\_sp,S\_cones\_sp,M\_juddVosToConesSp] = [JuddVosToSmithPokorny](JuddVosToSmithPokorny)  
  
Load in PTB's Judd-Vos XYZ cmfs and convert to Smith-Pokorny foveal cone  
fundamentals according to the matrix provided on CVRL.    
  
The returned fundamentals are normalized to a peak of 1, to match  
longtime conventions within PTB. Unnormalized versions are also returned.  
  
The normalized versions have now been stored in PTB data file T\_cones\_sp,  
with the original PTB versions saved in T\_cones\_sp\_orig.  
  
See notes on cvrl.org about slight discrepancies between various  
tabulations of the Smith-Pokorny fundamentals.  
  
Thanks to Danny Garside for pointing out that we should have tabulated  
functions that extend beyond 400-700 nm.  
  
7/21/18  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/JuddVosToSmithPokorny.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/JuddVosToSmithPokorny.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/JuddVosToSmithPokorny.m</code>
</div>

