# [SmartVec](SmartVec)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

vect = [SmartVec](SmartVec)(start,slength,step,mode)  
makes sequence that satisfies certain conditions.  
  
START is a scalar or vector with starting values of an sequence  
SLENGTH is a scalar or vector (with the same length as START) and  
  indicates the length of all sequences or the length of the  
  corresponding sequence in START.  
STEP is optional and indicates the stepsize of the series. Default is 1  
  STEP can be a scalar and indicate the stepsize for all segments, or it  
  can be the same lenght as START if you want to provide a different  
  stepsize for each segment  
MODE is optional and has two options:  
  'neg'  : the produced sequence will satisfy  : diff([n n+1]) = -1   
  'flat' : the produced sequence will satisfy  : diff([n n+1]) =  0  
if no mode, the produced sequence will satisfy : diff([n n+1]) =  1  
MODE can be the third input to the function if you do not wish to  
override the default stepsize  
  
examples:  
  [SmartVec](SmartVec)([1 5],3)  
  ans =  
       1     2     3     5     6     7  
  [SmartVec](SmartVec)([1 5],[3 5])  
  ans =  
       1     2     3     5     6     7     8     9  
  [SmartVec](SmartVec)([1 5],[3 5],'neg')  
  ans =  
       1     0    -1     5     4     3     2     1  
  [SmartVec](SmartVec)([1 5],[3 5],2,'neg')  
  ans =  
       1     -1   -3     5     3     1     -1    -3  
  [SmartVec](SmartVec)([1 5],3,'neg')  
  ans =  
       1     0    -1     5     4     3  
  [SmartVec](SmartVec)([1 5],[3 5],'flat')  
  ans =  
       1     1     1     5     5     5     5     5  
  [SmartVec](SmartVec)([1 5],3,'flat')  
  ans =  
       1     1     1     5     5     5  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/SmartVec.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/SmartVec.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/SmartVec.m</code>
</div>

