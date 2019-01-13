# [PsychKinectCore('GrabFrame')](PsychKinectCore-GrabFrame) 
##### [Psychtoolbox](Psychtoolbox)>[PsychKinectCore](PsychKinectCore).{mex*} subfunction

[result, cts, age] = PsychKinect('GrabFrame', kinectPtr [, waitMode=1][, mostrecent=0]);

Poll or wait for arrival of new captured frames, release old ones.  
  
This function checks box 'kinectPtr' for the availability of frames. If  
'waitMode' is 1, the function waits/blocks until data is available if no new  
frames are available at time of call. Otherwise it just polls in a non-blocking  
fashion.  
If 'mostrecent' is 1, then the most recent frame is returned and old frames are  
discarded - this for low-latency live capture.  
  
  
'result' returns the status: 0 = No frame returned, 1 = Frame returned, 2 =  
Error.  
'cts' returns a capture time stamp of when the frame was captured.  
'age' returns the age of the frame -- the number of pending frames in the buffer  
queue.  
  
  
  


###See also:

