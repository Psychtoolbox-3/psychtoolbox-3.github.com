# [Rot3d](Rot3d)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

out = Rot3d(in,n,dim)  
rotates input matrix around x-, y- of z-axis  
IN is a vector, a 2D or a 3D matrix (all three can be rotated three  
dimensionally)  
  
rotation can only be performed by multiples of 90 degrees, N is the  
number of 90 degree steps by which the matrix will be rotated (clockwise,  
same as rot90())  
DIM indicates the axis to rotate about:  
  1=y; 2=x; 3=z  
  
Rot3d([1 2 3 4; 3 5 6 7],1,1)  
  ans(:,:,1) =  
       4  
       7  
  ans(:,:,2) =  
       3  
       6  
  ans(:,:,3) =  
       2  
       5  
  ans(:,:,4) =  
       1  
       3  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/Rot3d.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/Rot3d.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/Rot3d.m</code>
</div>

