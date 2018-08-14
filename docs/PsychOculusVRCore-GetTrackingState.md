# [PsychOculusVRCore('GetTrackingState')](PsychOculusVRCore-GetTrackingState) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOculusVRCore](PsychOculusVRCore).{mex*} subfunction


Return current state of head position and orientation tracking for Oculus device  
'oculusPtr'.  
Head position and orientation is predicted for target time 'predictionTime' in  
seconds if provided, based on the latest measurements from the tracking  
hardware. If 'predictionTime' is omitted or set to zero, then no prediction is  
performed and the current state based on latest measurements is returned.  
  
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
'CameraPose' as vector with position and orientation quaternion, like  
'HeadPose'.  
'LeveledCameraPose' Like 'CameraPose' but aligned to the gravity vector of the  
world.  
'CameraFrustumHVFov' Horizontal and vertical field of view of the tracking  
camera in radians.  
'CameraFrustumNearFarZInMeters' Near and far limit of the camera view frustum in  
meters.  
'LastCameraFrameCounter' Last camera framecounter value of tracking camera.  
'RawSensorAcceleration' = Raw measured accelerometer reading in m/sec^2.  
'RawSensorGyroRate' = Raw gyrometer reading in rad/s.  
'RawMagnetometer' = Raw magnetic field in gauss.  
'SensorTemperature' = Sensor temperature in degrees Celsius.  
'IMUReadoutTime' = Readout time of the last IMU sample in seconds.  
  
  


###See also:
Start Stop
