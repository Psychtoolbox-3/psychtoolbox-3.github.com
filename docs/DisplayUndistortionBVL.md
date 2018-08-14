# [DisplayUndistortionBVL](DisplayUndistortionBVL)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[scal] = [DisplayUndistortionBVL](DisplayUndistortionBVL)([caliboutfilename][, screenid][, xnum=37][, ynum=27][, referenceImage=None][, stereomode=0])  
[scal] = [DisplayUndistortionBVL](DisplayUndistortionBVL)([caliboutfilename][, calibinfilename])  
  
Geometric display calibration procedure for undistortion of distorted  
displays. Needs graphics hardware with basic support for the PTB imaging  
pipeline (see below).  
  
This code was contributed by the members of the Banks Vision Lab at  
University of California, Berkeley. It is a subset of their internal  
"BVL" library and used since many years for their display devices,  
haploscopes etc., so it should be reasonably bug-free and mature.  
  
Many display devices, e.g., video beamers and most CRT displays cause  
some amount of spatial distortion to your visual stimuli during display.  
Psychtoolbox can "undistort" your visual stimuli for you: At stimulus  
onset time, PTB applies a geometric warping transformation to your  
stimulus which is meant to counteract or cancel out the geometric  
distortion caused by your display device. If both, PTB's warp transform  
and the implicit distortion transform of the display match, your stimulus  
will show up undistorted on the display device.  
  
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
interactive procedure: You can change and tweak the transformation until  
it fits your needs, ie. until it nicely undistorts your display. Then the  
corresponding calibration file is saved for later use with that display.  
  
[DisplayUndistortionBVL](DisplayUndistortionBVL) defines a continous mapping (x', y') = f(x, y)  
from uncorrected input pixel locations (x,y) in your stimulus image to  
output locations (x', y') on your display. This mapping is defined by a  
3rd order, 2-dimensional polynomial that is fitted to the calibration data.  
  
  
### How to use:  
  
1. Start the script, providing all parameters that you don't want to have  
at default settings (all parameters have reasonable defaults):  
  
'caliboutfilename' Name of the file to which calibration results should  
be stored. If no name is provided, the file will be stored inside the  
'GeometryCalibration' subfolder of your psychtoolbox configuration  
directory (path is [PsychToolboxConfigDir](PsychToolboxConfigDir)('GeometryCalibration'). The  
filename will contain the screenid and resolution of the display that was  
calibrated.  
  
'calibinfilename' is the optional path and filename of an existing  
calibration file that you want to use as a template or starting point for  
your calibration, e.g., from previous calibrations in order to save you  
some setup work. If no 'calibinfilename' is provided or if 'screenid' and  
other parameters are provided instead, the script will start with a  
default rectilinear calibration grid of equally spaced points.  
  
### These parameters only have meaning if no 'calibinfilename' was provided:  
  
'screenid' screen id of the target display for calibration. If  
'calibinfilename' was provided, the screenid encoded in that file will be  
used. Otherwise, the provided screenid will be used. If this parameter is  
omitted, PTB will use the single screen on a single display setup. On a  
multi-display setup, PTB will ask for the screenid.  
  
'xnum' and 'ynum' Optional number of horizontal and vertical calibration  
points to use. Their number doesn't affect runtime behaviour of your  
stimulus script, only the quality of your calibration and the amount of  
time you'll need to calibrate. The default settings are xnum = 37 and  
ynum = 27. 'xnum' and 'ynum' should be odd numbers. If you provide an  
even number it will be rounded up to the next odd number.  
  
'referenceImage' Optional name of an image file in a format supported by  
Matlab/Octaves imread() command: If provided, the image will be loaded  
from filesystem and drawn as a backdrop to the calibration grid. You can  
use this if you want to use this routine not to undistort a physical  
display, but want to undistort an existing image, e.g., create a proper  
calibration file for the [ImageUndistortionDemo](ImageUndistortionDemo) routine.  
  
'stereomode' Optional stereo mode for display of calibration. Defaults to  
zero, i.e., monoscopic display.  
  
2. After startup, the script will display a grid of mostly evenly spaced  
points onscreen. The points will not be perfectly aligned to a grid due  
to the distortion caused by your display. Your job is to tweak and shift  
those points so that they line up to a rectilinear grid as good as  
possible on your display from the viewpoint of your subject.  
  
The best way to do this is to build a real mechanical rectilinear grid of  
fine wires and mount it to your display as a "real world" reference for a  
perfect grid. Then you move the displayed calibration dots so that they  
perfectly align with the crossings of the horizontal- and vertical wires  
of your mechanical reference grid.  
  
### Mouse operation:  
  
In 'global mode' (when you see the hair-cross in the center of the  
screen), the mouse buttons do the following:  
  
'Left mouse' or 'l' key:   Switch to local mode.  
'Middle mouse' or 'm' key: Change stepsize for parameter adjustments.  
'Right mouse' or 'r' key:  Change type of parameter to adjust.  
  
Following global parameters can be adjusted in global mode:  
'Translation' of whole dot field.  
'[Scale](Scale)' of dot field.  
'Shear' of dot field.  
'Trapezoid' correction.  
'Barrel and pincusion' distortion.  
  
In 'local mode': The location of a selected dot or a selection of dots  
can be changed:  
  
'Left mouse' + mouse drag: Select a single dot close to mouse cursor, or  
                           draw a bounding rectangle around a region of  
                           dots to select.  
  
'Middle mouse' or 'm' key: Change stepsize for translation of dot(s).  
'Right mouse' or 'r' key:  Unselect dot(s) if dot(s) is/are selected.  
                           Switch to 'global mode' if no dot(s) selected.  
  
  
  
### Keys and their meaning:  
  
'l' 'm' and 'r' buttons are synonyms for left- middle- and right mouse  
buttons. However, its much more convenient to use a three button mouse.  
  
Cursor arrow keys move selected dot(s) or change selected global  
parameters.  
  
'space' key toggles the display of the online help text.  
  
You finish the calibration and write it into a calibration file by  
pressing the [ESCape](ESCape) key. This will end the calibration script. The  
structure 'scal' which contains all calibration results will also be  
returned by this function as optional return argument.  
  
This script will print out a little snippet of code that you can paste  
and include into your experiment script - That will automatically load  
the calibration result file and apply the proper undistortion operation.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionBVL.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionBVL.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionBVL.m</code>
</div>

