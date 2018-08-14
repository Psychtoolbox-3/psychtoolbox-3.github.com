# [PsychOculusVRCore('LatencyTester')](PsychOculusVRCore-LatencyTester) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOculusVRCore](PsychOculusVRCore).{mex*} subfunction


Drive or query latency tester for Oculus Rift DK2 device 'oculusPtr'.  
'cmd' is the command code:  
0 = Get next test draw color from 0 - 255 as [r,g,b] vector.  
1 = Get most recent latency test results in seconds as a 5 component vector  
'latency':  
latency[1] = [LatencyRender](LatencyRender):     (seconds) Last time between render IMU sample  
and scanout.  
latency[2] = [LatencyTimewarp](LatencyTimewarp):   (seconds) Last time between timewarp IMU sample  
and scanout.  
latency[3] = [LatencyPostPresent](LatencyPostPresent) (seconds) Average time between Vsync and  
scanout.  
latency[4] = [ErrorRender](ErrorRender)        (seconds) Last error in render predicted scanout  
time.  
latency[5] = [ErrorTimewarp](ErrorTimewarp)      (seconds) Last error in timewarp predicted  
scanout time.  
  
If 'cmd' can't get executed, then an empty result [] is returned.  
  
  


###See also:

