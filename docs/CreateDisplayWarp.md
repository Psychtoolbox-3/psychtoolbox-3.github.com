# [CreateDisplayWarp](CreateDisplayWarp)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[warpstruct, filterMode] = [CreateDisplayWarp](CreateDisplayWarp)(window, calibfilename [, showCalibOutput=0]);  
  
Helper routine for Geometric display undistortion mapping, not to be  
called inside normal PTB scripts!  
  
This function reads a display calibration file 'calibfilename' and builds  
a "geometric warp function" based on the calibration information in  
'calibfilename' for the onscreen window with handle 'window'. It returns  
a struct 'warpstruct' that defines the created warp function. You could  
pass this 'warpstruct' as a parameter to the Psychtoolbox command...  
  
[PsychImaging](PsychImaging)('AddTask', viewchannel, 'GeometryCorrection', warpstruct);  
  
However, you normally do not call this routine directly from your script. Its  
called internally by the [PsychImaging](PsychImaging)() command...  
  
[PsychImaging](PsychImaging)('AddTask', viewchannel, 'GeometryCorrection', calibfilename);  
  
...in order to setup PTB's imaging pipeline for realtime geometry  
correction, based on the calibration info in the file 'calibfilename'.  
  
Example: You created a calibration file 'mycalib.mat' to undistort the  
left view display of a stereo setup. Then you could apply this  
undistortion function via the following setup code:  
  
[PsychImaging](PsychImaging)('PrepareConfiguration');  
[PsychImaging](PsychImaging)('AddTask', 'LeftView', 'GeometryCorrection', 'mycalib.mat');  
window = [PsychImaging](PsychImaging)('OpenWindow', screenid);  
  
This would open an onscreen window just as window=[Screen](Screen)('OpenWindow', screenid);  
would do. It would configure the window for automatic undistortion based  
on the data in 'mycalib.mat'.  
  
Psychtoolbox provides multiple different interactive setup routines that  
allow you to create a calibration file for your setup. Currently the  
following routines are provided:  
  
[DisplayUndistortionBVL](DisplayUndistortionBVL).m    -- Undistortion based on 3rd order polynomial  
surface. This is the recommended calibration procedure for most cases -  
Proven in real-world use on many different display types.  
  
When used with [DisplayUndistortionBVL](DisplayUndistortionBVL), the [GeometryCorrection](GeometryCorrection) takes  
up to three optional parameters:  
  
[PsychImaging](PsychImaging)('AddTask', 'LeftView', 'GeometryCorrection', 'mycalib.mat' [, debug=0][, xsampling=73][,ysampling=53][, replicate=[1,1]]);  
xsampling and ysampling specify the horizontal and vertical number of subdivisions  
for the warpmesh that is used for undistortion - higher numbers give more  
close approximations but increase drawing time. replicate is a vector which  
describes how often the mesh should be replicated into horizontal and vertical  
direction. Values other than the default [1,1] only make sense for special display  
devices like [ProPixx](ProPixx).  
  
[DisplayUndistortionBezier](DisplayUndistortionBezier).m -- Undistortion based on a NURBS surface (Non  
uniform rational bezier spline surface). A simple procedure.  
  
[DisplayUndistortionHalfCylinder](DisplayUndistortionHalfCylinder).m -- Undistortion for projection of  
images to a half-cylindrical projection surface.  
  
[DisplayUndistortionSphere](DisplayUndistortionSphere).m -- Undistortion for projection of  
images to a spherical or half-spherical projection surface.  
  
[DisplayUndistortionCSV](DisplayUndistortionCSV).m -- Import undistortion information from  
a .csv file with a warp mesh description suitable for use with NVidia's  
Warp API. This creates a compatible display warping to use of that [NVidia](NVidia)  
technology.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateDisplayWarp.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateDisplayWarp.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateDisplayWarp.m</code>
</div>

