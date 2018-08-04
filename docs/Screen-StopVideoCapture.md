# [Screen('StopVideoCapture')](Screen-StopVideoCapture) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Stop video capture device specified by 'capturePtr'. The function returns the  
number of captured frames it had to drop from its internal buffers in order to  
keep synchronization with realtime or because it ran out of internal buffer  
space.  
If the optional 'discardFrames' flag is set to zero, then captured but not yet  
fetched video images will not get deleted. Instead they are retained until next  
time 'StartVideoCapture' is called. This allows to fetch them after capture has  
been stopped. By default, all pending frames are deleted at stop of capture  
(discardFrames == 1).  
  


###See also:
[CloseVideoCapture](Screen-CloseVideoCapture) [StartVideoCapture](Screen-StartVideoCapture) [StopVideoCapture](Screen-StopVideoCapture) [GetCapturedImage](Screen-GetCapturedImage)
