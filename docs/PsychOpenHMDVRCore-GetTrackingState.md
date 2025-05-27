# [PsychOpenHMDVRCore('GetTrackingState')](PsychOpenHMDVRCore-GetTrackingState) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

[state, touch] = PsychOpenHMDVRCore('GetTrackingState', openhmdPtr [, predictionTime=0]);

Return current state of head position and orientation tracking for [OpenHMD](OpenHMD)  
device 'openhmdPtr'.  
Head position and orientation is predicted for target time 'predictionTime' in  
seconds if provided, based on the latest measurements from the tracking  
hardware. If 'predictionTime' is omitted or set to zero, then no prediction is  
performed and the current state based on latest measurements is returned. NOTE:  
Some fields may not get updated, depending on the type of HMD device and version  
of the libopenhmd library. NOTE: predictionTime is not yet implemented and  
silently ignored.  
  
'state' is a struct with fields reporting the following values:  
'Time' = Time in seconds of predicted tracking state.  
'Status' = Tracking status flags. +1 = Head orientation tracked, +2 = Head  
position tracked, +4 = Camera pose tracked +32 = Position tracking hardware  
connected, +128 = HMD display is connected and available.  
'HeadPose' = Head position [x, y, z] in meters and rotation as quaternion [rx,  
ry, rz, rw], all as a vector [x,y,z,rx,ry,rz,rw].  
'HeadLinearSpeed' = Linear velocity [vx,vy,vz] in meters/sec.  
'HeadAngularSpeed' = Angular velocity [rx,ry,rz] in radians/sec.  
'HeadLinearAcceleration' = Linear acceleration [ax,ay,az] in meters/sec^2.  
'HeadAngularAcceleration' = Angular acceleration [rax,ray,raz] in radians/sec^2.  
  
### Touch controller position and orientation:  
  
The return argument 'touch' is a struct array with 2 structs. touch(1) contains  
info about the tracking state and tracked pose of the left hand (= left touch  
controller) of the user, touch(2) contains info about the right hand (= right  
touch controller) of the user.  
The structs have very similar structure to the head (= HMD) tracking data  
returned by 'state':  
  
'Time' = Time in seconds of returned hand/controller tracking state.  
'Status' = Tracking status flags:  
0  = No tracking info for hand/controller, ie. no touch sensor connected.  
+1 = Hand orientation tracked,  
+2 = Hand position tracked,  
'HandPose' = Position and orientation of the hand, in usual [x,y,z,rx,ry,rz,rw]  
vector form as with 'HeadPose'.  
'HandLinearSpeed' = Hand linear velocity [vx,vy,vz] in meters/sec.  
'HandAngularSpeed' = Hand angular velocity [rx,ry,rz] in radians/sec.  
'HandLinearAcceleration' = Hand linear acceleration [ax,ay,az] in meters/sec^2.  
'HandAngularAcceleration' = Hand angular acceleration [rax,ray,raz] in  
radians/sec^2.  
  
  


###See also:
Start Stop [GetInputState](PsychOpenHMDVRCore-GetInputState)
