# [PsychGetPositionYawMatrix](PsychGetPositionYawMatrix)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

M = [PsychGetPositionYawMatrix](PsychGetPositionYawMatrix)(translation, yawRotation);  
  
Builds a 4x4 [OpenGL](OpenGL) compatible (right hand side post-multiply)  
matrix for a 3D translation followed by a rotation around the  
y-axis. Useful for positioning an observer in 3D space, then  
giving the observer a specific "looking direction" or heading.  
  
You can also use this function for incremental position and  
orientation updates by simply post-multiplying the result of  
this function to the result of a previous call to this function,  
e.g.:  
  
### 1. Select start position and orientation:  
  
   M = [PsychGetPositionYawMatrix](PsychGetPositionYawMatrix)(startPosition, startHeading);  
  
2. Update location relative to current heading direction, then  
   change new heading by deltaHeading degrees for initiating a  
   turn:  
  
   M = M \* [PsychGetPositionYawMatrix](PsychGetPositionYawMatrix)[(PositionIncrement]((PositionIncrement), deltaHeading);  
  
Initializing an observer position with step 1, then updating it  
by repeating step 2, e.g., driven by keyboard input, mouse or  
gamepad input, or some other input device or "game logic" allows  
to move the observers body through the scene in a "natural" way.  
  
  
### Parameters:  
  
'translation' a 3 component translation vector [tx, ty, tz].  
  
'yawRotation' a rotation angle in degrees along the y-axis, also  
known as heading direction or upright direction.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/PsychGetPositionYawMatrix.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/PsychGetPositionYawMatrix.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/PsychGetPositionYawMatrix.m</code>
</div>

