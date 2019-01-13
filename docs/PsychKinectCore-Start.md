# [PsychKinectCore('Start')](PsychKinectCore-Start) 
##### [Psychtoolbox](Psychtoolbox)>[PsychKinectCore](PsychKinectCore).{mex*} subfunction

[starttime, fps, cwidth, cheight, dwidth, dheight] = PsychKinect('Start', kinectPtr [, dropframes=0]);

Start video and depth capture operation of box 'kinectPtr'.  
  
Starts the capture operation into the internal bufferqueue. Color- and depths  
frames can be polled/waited for/dequeued from the queue via a call to  
[PsychKinect](PsychKinect)('GrabFrame',...); and then retrieved via the 'GetXXX' functions.  
Data is stored in an internal ringbuffer, whose size is set in the 'Open'  
function. The optional 'dropframes' flag decides if the oldest frames should be  
dropped if the buffer is full (=1) or if the most recent frame should be dropped  
if the buffer is full (=0).   
  
The function returns the start time of capture and the nominal framerate 'fps',  
color image width 'cwidth' and height 'cheight', and depth image 'dwidth' and  
'dheight'.  
  
  


###See also:

