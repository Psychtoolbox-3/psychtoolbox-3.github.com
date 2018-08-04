# [DisplayUndistortionHalfCylinder](DisplayUndistortionHalfCylinder)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

Create geometric display calibration file for projection onto a cylinder or sphere.  
  
CAUTION: This function is not fully implemented and tested! It may or  
may not work for your purpose and may give totally wrong results.  
  
### Usage:  
  
[DisplayUndistortionHalfCylinder](DisplayUndistortionHalfCylinder)([calibfilename][, screenid]);  
  
Prepare display calibration file for projection of a flat screen image to  
a half-cylindrical projection surface.  
  
The script displays a calibration grid on screen 'screenid' (or the  
auto-selected screen if this parameter is omitted). Use the keys  
mentioned below to modify the grid until it is optimally aligned with  
your cylindrical projection surface. Save the final calibration settings  
to file 'calibfilename' (or an auto-selected default filename, if  
parameter is omitted) by pressing the 's' key. Exit the procedure via  
pressing the [ESCape](ESCape) key.  
  
The saved calibration file can be later loaded and applied in a script  
via the command sequence that this script will diplay when it is  
finished.  
  
  
Keys and their meaning:  
[ESCape](ESCape) = Quit script. Unsaved changes will be lost!  
s      = Save current settings in calibration file.  
r      = Change rotation angle.  
t      = Change translation of output image.  
o      = Change size of output image.  
i      = Change size of input image.  
w      = Width of the projection area at a radius distance R in cm for  
         sphere curvature correction.  
b      = Radius of the spherical projection screen for sphere curvature correction.  
  
-\> Type "edit [SphereProjectionShader](SphereProjectionShader).frag.txt" and look at the warp  
shader code for a full understanding of the roff and rpow coefficients  
for spherical remapping. Also see Psychtoolbox forum message 11660.  
  
  
Arrow keys change the parameter that is selected via 'r', 't', 'o' or 'i'  
key.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionHalfCylinder.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionHalfCylinder.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionHalfCylinder.m</code>
</div>

