# [DisplayUndistortionBezier](DisplayUndistortionBezier)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[DisplayUndistortionBezier](DisplayUndistortionBezier)([caliboutfilename] [, xnum=2][, ynum=2][, subdivision=100][, imagename=default][, screenid=max][, stereomode=0][, winrect=[]][, calibinfilename][, refimagename])  
  
Geometric display calibration procedure for geometric undistortion of  
distorted displays. Needs graphics hardware with support for PTB imaging  
pipeline.  
  
IMPORTANT: While this routine is easy to use, it is also limited! The  
Banks Vision Lab (University of California, Berkeley) has contributed a  
much more powerful and flexible calibration procedure.  
  
Read "help [DisplayUndistortionBVL](DisplayUndistortionBVL)" for help and info on that one.  
  
  
Many display devices, e.g., video beamers and most CRT displays, cause  
some amount of spatial distortion to your visual stimuli during display.  
Psychtoolbox can "undistort" your visual stimuli for you: At stimulus  
onset time, PTB applies a geometric warping transformation to your  
stimulus which is meant to counteract or cancel out the geometric  
distortion caused by your display device. If both PTB's warp transform  
and the distortion transform of the display match, your stimulus will  
show up undistorted on the display device.  
  
### For this to work, PTB needs two things:  
  
1. Recent graphics hardware with support for the PTB imaging pipeline:  
See our Wiki for recommendations. However, all ATI cards starting with  
Radeon 9500 and all [NVidia](NVidia) cards of type [GeForce](GeForce)-FX5200 and later, as  
well as the Intel-GMA 950 and later should be able to do it, although  
more recent cards will have a higher performance.  
  
2. A calibration file that defines the warp transformation to apply. Your  
experiment script will load that file into [Screen](Screen)'s "warp engine" at the  
beginning of your experiment.  
  
This routine allows you to create such a calibration file in an  
interactive procedure: It applies some warp transformation, shows the  
result on your display, and you can change and tweak the transformation  
until it fits your needs, ie. it nicely undistorts your display. Then the  
corresponding calibration file is saved for later use with that display.  
  
As the name suggests, [DisplayUndistortionBezier](DisplayUndistortionBezier) supports a continous  
mapping (x', y') = Beziersurface(x, y) from input pixel locations (x,y)  
in your stimulus image to output locations (x', y') on your display. This  
mapping is defined by a Bezier surface (see Chapter 12 "Evaluators and  
NURBS" or any other textbook about NURBS for a description of their  
mathematical properties).  
  
The shape of the Bezier surface is defined by the location of a couple of  
control points, which you can move around during the calibration  
procedure to modify the shape of the surface. You can select the number  
of control points to use: More control points (=degrees of freedom) allow  
for more flexibility and finer control, but make the calibration procedure  
more tedious for you. Their number doesn't affect computation time when  
your experiment script is running.  
  
### How to use:  
  
1. Start the script, providing all parameters that you don't want to have  
at default settings (all parameters have defaults):  
  
'caliboutfilename' Name of the file to which calibration results should  
be stored. Defaults to 'BezierCalibdata.mat' in your current working directory.  
  
'xnum' and 'ynum' Number of horizontal and vertical control points to  
use. Higher numbers mean finer and more flexible control, but also a more  
tedious calibration for you. Their number doesn't affect runtime  
behaviour of your stimulus script. For simple trapezoid correction or  
translation/rotation, the minimum allowed number of control points xnum=2  
and ynum=2 is sufficient - this is the default. For most other purposes  
a 3 by 3 grid of control points xnum=3 and ynum=3 may suffice. However,  
you are not limited by any upper bound...  
  
'subdivision' Number of vertical and horizontal subdivisions of the  
bezier surface - the grid resolution: Higher numbers mean higher accuracy  
but also higher computational overhead in your script. However, recent  
graphics hardware shouldn't have much problems handling reasonably sized  
meshes. Defaults to a 100 by 100 grid.  
  
'imagename' Name of the image file for the test image to be rendered as  
an alternative to the mesh grid. We default to our standard 'konintjes'  
image.  
  
'screenid' screen id of the target display for calibration.  
max([Screen](Screen)('Screens')) by default.  
  
'stereomode' Stereomode for which calibration should be applied: Defaults  
to 0 == Mono mode. [6 1] would mean: "Use stereomode 6 (Anaglyph stereo)  
and the right-eye view (1)".  
  
'winrect' Size of the calibration window: Defaults to full-screen.  
  
'calibinfilename' Defaults to none. If provided, results of a previous  
calibration are loaded from file 'calibinfilename' instead of starting  
from scratch. Useful for incremental calibration.  
  
2. After startup, the script will display a grid onscreen, which  
represents the displayed area after calibration. Your job is to tweak,  
shift and bend that grid so that it looks as flat and rectilinear as  
possible on your display from the viewpoint of your subject. The grid has  
green control points placed at regular intervals. These are the tweakable  
points that you can move: Moving these control points will bend the  
calibration grid in a smooth fashion, as if the grid would be attached to  
the points with some springs.  
  
### Mouse operation:  
  
To select a control point, just move the mouse pointer close to it, then  
press a mouse key. The selected control point will change color to yellow  
and a yellow line will connect its current position to its original  
position in the uncalibrated display.  
  
You can move the point by moving the mouse pointer while keeping the  
mouse key pressed.  
  
  
### Keys and their meaning:  
  
You can also move the currently selected control point via the Cursor  
keys, at slow speed, or at a faster speed when holding down the shift  
key.  
  
Press the 'space' key to toggle between grid display and display of the  
test image 'imagename'. A good way to test the calibration would be to  
load a screenshot of one of your typical stimuli as image file  
'imagename'.  
  
You finish the calibration and write it into a calibration file by  
pressing the [ESCape](ESCape) key. This will end the calibration script.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionBezier.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionBezier.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionBezier.m</code>
</div>

