# [Explode](Explode)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

outputcell = [Explode](Explode)(vect,splitvect,mode)  
[out1,out2,...] = [Explode](Explode)(vect,splitvect,mode)  
  
Split a string or vector VECT by a string, scalar or vector SPLITSVECT.  
Output OUTPUTCELL will be returned as an array of cells.  
  
Both VECT and SPLITSVECT must be a string or numeric vector of length 1  
or more.  
  
The way this function handles its input is different for strings and  
numeric datatypes.  
  
strings  
SPLITSVECT can be specified using two formats (MODE):  
If MODE is not specified, 'fixed' will be used  
  
  'fixed'    : a fixed string, which will be used literally to split  
               VECT. Some character combinations have a special meaning:  
                  \b Backspace  
                  \f Form feed  
                  \n New line  
                  \r Carriage return  
                  \t Horizontal tab  
               example:  
                  s1 = 'resp32|me too|"get over here"';  
                  s2 = [Explode](Explode)(s1,'|'); or s2 = [Explode](Explode)(s1,'|','fixed');  
                  s2(:)  
                  ans =   
                      'resp32'  
                      'me too'  
                      '"get over here"'  
  
  'variable' : if you want to split the input with on a string that  
               matches a certain pattern.  
               specify this pattern using a regular expression,  
               see "doc regexp"  
               example:  
                  s1 = '|fff|ja|fdf|er|fft|fofr|';  
                  s2 = [Explode](Explode)(s1,'f.f','variable'); % . means any character  
                  s2(:)  
                  ans =   
                      '|'  
                      '|ja|'  
                      '|er|fft|'  
                      'r|'  
  
numerical vectors  
SPLITSVECT can be specified using two formats (MODE):  
If MODE is not specified, 'fixed' will be used  
NB: splitting floats works, but precision will be lost  
  
  'fixed'    : a fixed number or sequence of numbers, which will be used  
               literally to split the vector.  
               example:  
                  n1 = [inf 33 12 45 13 nan 46 74 12 45 15 64];  
                  n2 = [Explode](Explode)(n1,[12 45]); of n2 = [Explode](Explode)(s1,[12 45],'fixed');  
                  n2(:)  
                  ans =   
                      [Inf    33]  
                      [ 13   [NaN](NaN)    46    74]  
                      [ 15    64]  
                  n2 = [Explode](Explode)(n1,12);  
                  n2(:)  
                  ans =   
                      [Inf    33]  
                      [ 45    13   [NaN](NaN)    46    74]  
                      [ 45    15    64]  
  
  'variable' : If you want to split on a sequence of numbers that  
               contains (a) wildcard(s). Each wilcard can match a single  
               item in the vector.  
               [NaN](NaN) specifies a wildcard. When using 'variable' for  
               numeric input, you can thus no longer use [NaN](NaN) in your  
               pattern.  
               example:  
                  n1 = [inf 33 12 45 13 nan 46 74 12 35 64 13 21];  
                  n2 = [Explode](Explode)(n1,[12 nan 13],'variable');  
                  n2(:)  
                  ans =   
                      [Inf    33]  
                      [[NaN](NaN)    46    74    12    35    64    13    21]  
  
                  n2 = [Explode](Explode)(n1,[12 nan nan 13],'variable');  
                  n2(:)  
                  ans =   
                      [Inf    33    12    45    13   [NaN](NaN)    46    74]  
                      [21]  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/Explode.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/Explode.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/Explode.m</code>
</div>

