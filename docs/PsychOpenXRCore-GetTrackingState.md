# [PsychOpenXRCore('GetTrackingState')](PsychOpenXRCore-GetTrackingState) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

[state, touch, gaze, hands] = PsychOpenXRCore('GetTrackingState', openxrPtr [, predictionTime=nextFrame][, reqMask=all]);

Return current state of position and orientation tracking for [OpenXR](OpenXR) device  
'openxrPtr'.  
Position and orientation is predicted for target time 'predictionTime' in  
seconds if provided, based on the latest measurements from the tracking  
hardware. If 'predictionTime' is omitted or zero, then the prediction is  
performed for the mid-point of the next possible video frame of the device, ie.  
the most likely presentation time for immediately rendered images.  
'reqMask' mask defining which information to return. Defaults to all  
information. Values are +1 for head/eye tracking, +2 for hand controller  
tracking, +4 for eye gaze tracking, +8 for articulated hand and finger tracking.  
  
'state' is a struct with fields reporting the following values:  
'Time' = Time in seconds of returned tracking state.  
'Status' = Tracking status flags:  
+1 = Orientation tracked for all eyes,  
+2 = Position tracked for all eyes,  
+4 = At least part of the pose is somewhat valid, even if not tracked, but just  
inferred,  
+128 = device display is connected, available and actually on users head,  
displaying our content.  
  
'SessionState' = VR session status flags, added together:  
+1  = Our rendering goes to the device, ie. we have control over it. If some  
other app would be in control, this flag would be missing.  
+2  = device is present and active.  
+4  = device is strapped onto users head. E.g., a Rift CV1 would switch  
off/blank if not on the head.  
+8  = [DisplayLost](DisplayLost) condition! Some hardware/software malfunction, need to  
completely quit to recover.  
+16 = [ShouldQuit](ShouldQuit) The user interface asks us to voluntarily terminate this  
session.  
  
'CalibratedOrigin' = The pose of the world coordinate system origin during last  
recalibration, relative to its previous pose, as a vector [x,y,z,rx,ry,rz,rw].  
  
'EyePoseLeft' = Vector with position and orientation of left eye / left eye  
virtual camera.  
'EyePoseRight' = Vector with position and orientation of right eye / right eye  
virtual camera.  
The vectors are of form [tx, ty, tz, rx, ry, rz, rw] - A 3 component 3D  
position, followed by a 4 component rotation quaternion.  
  
   
Touch controller position and orientation:  
   
The return argument 'touch' is a struct array with 2 structs. touch(1) contains  
info about the tracking state and tracked pose of the left hand (= left touch  
controller) of the user, touch(2) contains info about the right hand (= right  
touch controller) of the user.  
The structs have very similar structure to the head (= device) tracking data  
returned by 'state':  
  
'Time' = Time in seconds of returned hand/controller tracking state.  
'Status' = Tracking status flags:  
 0 = No tracking info for hand/controller, ie. no [OpenXR](OpenXR) touch sensor connected.  
+1 = Hand orientation tracked,  
+2 = Hand position tracked,  
+4 = Hand linear velocity available,  
+8 = Hand angular velocity available,  
'HandPose' = Position and orientation of the hand, in usual [x,y,z,rx,ry,rz,rw]  
vector form.  
'HandLinearSpeed' = Hand linear velocity [vx,vy,vz] in meters/sec.  
'HandAngularSpeed' = Hand angular velocity [rx,ry,rz] in radians/sec.  
   
Eye gaze tracking on supported hardware:  
   
The return argument 'gaze' is a struct array with up to 2 structs. On a system  
with binocular eye tracking support, gaze(1) contains info about the tracking  
state and tracked gaze of the left eye of the user. On a system with only  
monocular eye tracking, it contains the only gaze information available, often  
the synthesized gaze of a "cyclops eye". On a system with binocular eye  
tracking, gaze(2) contains info about the gaze of the right eye.  
Each gaze struct contains the following fields:  
  
'Time' = Time in seconds of returned gaze tracking sample. This can be the  
actual acquisition time of the gaze sample closest in time to the requested  
'predictionTime', but it can also be a time for which the users gaze location  
was interpolated or extrapolated, given 'predictionTime'. The behaviour wrt.  
sample acquisition time, returned vs. requested time, and gaze inter- /  
extrapolation is system dependent and may vary from device to device, runtime to  
runtime and across operating systems. If the gaze sample time can not be  
determined by the given system, a value of zero is returned.  
'Status' = Tracking status flags:  
 0 = No gaze tracking info available.  
+1 = Some gaze info available, but not based on measurements. Consider this not  
trustworthy at all!  
+2 = Tracked gaze position available. This is possibly subject to interpolation  
or extrapolation.  
'GazePose' = Position and orientation of the eye, expressing a gaze vector in  
its usual [x,y,z,rx,ry,rz,rw] form.  
   
Articulated hand tracking on supported hardware:  
   
The return argument 'hands' is a struct array with 2 structs, one for each hand.  
hands(1) returns information about the left hand, hands(2) returns information  
about the right hand.  
Each struct has the following fields:  
'Tracked' The tracking status of the hand. 0 if the hand was not tracked and all  
further info is invalid, or 1 if at least part of the hand was tracked and some  
of the per-joint tracking info is valid.  
'Joints' A 9 rows by 26 column double matrix, where the rows of each column  
encode tracked info about one joint. Specific column indices correspond to  
specific named joints on the hand. The indices are standardized in the [OpenXR](OpenXR)  
specification for the XR\_EXT\_hand\_tracking extension, which specifies 26  
separate joints per hand. See section 12.30.6 "Conventions of hand joints" of  
the [OpenXR](OpenXR) extension spec for joint names, indices and reference.  
   
Row 1 of the matrix encodes tracking status: 0 = No info about this joint, 1 =  
Some inter-/extrapolated info, 3 = Fully tracked.  
Row 2 encodes the radius in meters of this joint - The estimated distance from  
joint axis to skin of the hand.  
Rows 3-5 encode the 3D [x; y; z] position in meters of the joint in the tracking  
reference space.  
Rows 6-9 define the [rx; ry; rz; rw] quaternion, encoding the relative  
orientation of the joint with respect to the tracking reference space.  
'JointPosesMatrix' A [OpenGL](OpenGL) style RHS transformation matrix which encodes all  
joints poses: 4-by-4-by-26 matrix, ie. one 4x4 matrix per joint.  
  
  


###See also:
Start Stop [GetTrackersState](PsychOpenXRCore-GetTrackersState) [GetInputState](PsychOpenXRCore-GetInputState)
