# [PsychKinect](PsychKinect)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[PsychKinect](PsychKinect) -- Control and access the Microsoft Kinect depth camera.  
  
This is a high level driver to allow convenient access to the Microsoft  
Kinect box. The Kinect is a depth-sensing "3D camera". The Kinect  
consists of a standard color camera (like any standard USB webcam)  
to capture a scene at 640x480 pixels resolution in RGB8 color with up to  
30 frames per second. In addition it has a depth sensor that measures the  
distance of each "pixel" from the camera. The Kinect delivers a color  
image with depth information which can be used to infer the 3D structure  
of the observed visual scene and to perform a 3D reconstruction of the  
scene.  
  
See [KinectDemo](KinectDemo) and [Kinect3DDemo](Kinect3DDemo) for two demos utilizing [PsychKinect](PsychKinect) to  
demonstrate this basic functions of the Kinect.  
  
[PsychKinect](PsychKinect) internally uses the [PsychKinectCore](PsychKinectCore) MEX file which actually  
interfaces with the Kinect.  
  
The driver is currently supported on Microsoft Windows under  
Matlab version 7.4 (R2007a) and later. It is also supported on  
GNU/Linux with Matlab or Octave and on Intel based Macintosh computers  
under OS/X with Matlab or Octave. The driver supports all versions of  
the Microsoft Kinect on Linux and OSX, but currently only the original  
XBOX-360 Kinect under Microsoft Windows.  
  
To use this driver you need:  
1. A Microsoft Kinect (price tag about 150$ at December 2010).  
2. A interface cable to connect the Kinect to a standard USB port of a  
   computer - sold separately or included in standalone Kinects.  
3. The free and open-source libfreenect + libusb libraries and drivers  
   from the [OpenKinect](OpenKinect) project (Homepage: http://www.openkinect.org )  
  
You need to install these libraries separately, otherwise our driver will  
abort with an "Invalid MEX file" error.  
  
Type "help [InstallKinect](InstallKinect)" for installation instructions and licensing  
terms.  
  
  
### Subfunctions:  
  
Most functions are part of the [PsychKinectCore](PsychKinectCore)() mex file, so you can get  
help for them by typing [PsychKinectCore](PsychKinectCore) FUNCTIONNAME ? as usual, with  
FUNCTIONNAME being the name of the function you want to get help for.  
  
[PsychKinect](PsychKinect)('Shutdown');  
- Release all internal resources of [PsychKinect](PsychKinect).  
  
  
[PsychKinect](PsychKinect)('ApplyCalibrationFile', kinect, calibFileName);  
- Load Kinect calibration from a .yml calibration file 'calibFileName', as  
created by rgbDemo software and apply it to Kinect with handle 'kinect'.  
  
  
kobject = [PsychKinect](PsychKinect)('CreateObject', window, kinect [, oldkobject]);  
- Create a new kobject for the specified 'window', using the Kinect box  
specified by the given 'kinect' handle. Recycle 'oldkobject' so save  
memory and resources if 'oldkobject' is provided. Otherwise create a new  
object.  
  
Do not use within [Screen](Screen)('BeginOpenGL', window); and [Screen](Screen)('EndOpenGL',  
window); calls, as 2D mode is needed.  
  
  
kobject encodes the 3D geometry of the scene as sensed by the Kinect. It  
corresponds to the currently selected "3d video frame" from the kinect,  
as selected by [PsychKinect](PsychKinect)('GrabFrame', kinect);  
kobject can then by accessed directly (it is a struct variable) or passed  
to other [PsychKinect](PsychKinect) functions for display and processing.  
  
[PsychKinect](PsychKinect)('DeleteObject', window, kobject);  
- Delete given 'kobject' for given 'window' once you no longer need it.  
During a work-loop you could also pass 'kobject' to the next  
[PsychKinect](PsychKinect)('CreateObject', ...); call as 'oldkobject' to recycle it for  
reasons of computational efficiency.  
  
Do not use within [Screen](Screen)('BeginOpenGL', window); and [Screen](Screen)('EndOpenGL',  
window); calls, as 2D mode is needed.  
  
  
[PsychKinect](PsychKinect)('DrawObject', window, kobject [, drawtype=0]);  
Draw the 3D scene stored in 'kobject' into the 'window' selected. Use the  
current [OpenGL](OpenGL) settings for this. 'drawtype' is optional and defines kind  
of rendering: 0 (the default) draws a colored point-cloud of all sensed  
3D points. 1 draws a dense textured 3D surface mesh.  
  
This function must be enclosed between [Screen](Screen)('BeginOpenGL', window);  
and [Screen](Screen)('EndOpenGL', window); calls, as 3D mode is needed.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/PsychKinect.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/PsychKinect.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/PsychKinect.m</code>
</div>

