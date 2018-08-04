# [DisplayUndistortionLabRiggerMouseStim](DisplayUndistortionLabRiggerMouseStim)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

scal = [DisplayUndistortionLabRiggerMouseStim](DisplayUndistortionLabRiggerMouseStim)(caliboutfilename[, screenid])  
  
Hi-Def TV for mice - Courtesy of Labrigger.  
  
CAUTION: This is not a finished, polished routine, but a template for  
actual producers of TV for mice to get started. Make sure you understand  
this code before using it!  
  
Geometric display calibration procedure for undistortion of distorted  
displays. Needs graphics hardware with basic support for the PTB imaging  
pipeline.  
  
This one is an example of how to integrate sample code from [LabRigger](LabRigger)  
for visual stimulation of a mouse with a single flat screen. It does the  
neccessary undistortion. For explanation and detail go to the original  
code and method presented at:  
  
http://labrigger.com/blog/2012/03/06/mouse-visual-stim/comment-page-1/  
  
Please note this is quickly hacked together throwaway sample code. It  
almost literally copy and pasted the code from [LabRigger](LabRigger) into the  
subroutine [MouseStim](MouseStim)() and then converts its output calibration matrices  
into a calibration file useable by Psychtoolbox [DisplayUndistortionCSV](DisplayUndistortionCSV)  
method, so these undistortions can be applied to live visual stimuli  
fast and in realtime. All display and stimulation setup parameters are  
hard-coded in [MouseStim](MouseStim)(). Somebody should really clean up this routine  
and test it on a real stimulation setup. If you've successfully done so,  
please contribute the enhanced version of this M-File back to the PTB  
for integration into future releases.  
  
### General boiler-plate description of working and use:  
  
Psychtoolbox can "undistort" your visual stimuli for you: At stimulus  
onset time, PTB applies a geometric warping transformation to your  
stimulus which is meant to counteract or cancel out the geometric  
distortion caused by your display device. If both, PTB's warp transform  
and the implicit distortion transform of the display match, your stimulus  
will show up undistorted on the display device.  
  
For this to work, PTB needs a non-ancient graphics card with support for  
the PTB imaging pipeline. All ATI/AMD cards starting with Radeon 9500 and  
all [NVidia](NVidia) cards of type [GeForce](GeForce)-FX5200 and later, as well as the Intel-GMA 950  
and later should be able to do it, although more recent cards will have a higher  
performance.  
  
[DisplayUndistortionLabRiggerMouseStim](DisplayUndistortionLabRiggerMouseStim) defines a continous mapping  
(x', y') = f(x, y) from uncorrected input pixel locations (x,y) in  
your stimulus image to output locations (x', y') on your display.  
This mapping is defined by a linear mesh of quadrilaterals, as computed  
in the subfunction [MouseStim](MouseStim)().  
  
# How to use  
  
### Execute the function with the following parameters:  
  
`caliboutfilename` Name of the file to which calibration results should  
be stored. If no name is provided, the file will be stored inside the  
'GeometryCalibration' subfolder of your Psychtoolbox configuration  
directory (path is [PsychToolboxConfigDir](PsychToolboxConfigDir)('GeometryCalibration'). The  
filename will contain the screenid of the display that was calibrated.  
  
`screenid` screen id of the target display for calibration. The parameter  
is optional, defaults to zero, and is only used to generate the default  
filename for the output file.  
  
This script will print out a little snippet of code that you can paste  
and include into your experiment script - That will automatically load  
the calibration result file and apply the proper undistortion operation.  
  
You can see an example use of it in [ImagingVideoCaptureDemo](ImagingVideoCaptureDemo).m  
  
A quick way to test your calibration created with this script is to  
call [ImageUndistortionDemo](ImageUndistortionDemo) (caliboutfilename, 'checkerboard'). However,  
for production use you'd rather use your calibration via [PsychImaging](PsychImaging),  
as shown in [ImagingVideoCaptureDemo](ImagingVideoCaptureDemo) or the code snippet printed by this  
function.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionLabRiggerMouseStim.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionLabRiggerMouseStim.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/DisplayUndistortionLabRiggerMouseStim.m</code>
</div>

