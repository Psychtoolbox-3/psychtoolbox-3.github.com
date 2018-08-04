# [Screen('VideoCaptureDevices')](Screen-VideoCaptureDevices) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Enumerate all available video devices for a given videocapture engine id  
'engineId', or for the default engine, if none is given. Returns a struct array  
with one slot per available device. Entries of each struct in the array are  
specific to the selected capture engine, except for the entry 'DeviceIndex'  
which provides a handle that you could pass to [Screen](Screen)('OpenVideoCapture',  
windowPtr, deviceIndex, ...); as the 'deviceIndex' argument to select the video  
device corresponding to a given slot.  
The function may return an empty array if no video capture devices could be  
detected.  
  


###See also:
[CloseVideoCapture](Screen-CloseVideoCapture) [StartVideoCapture](Screen-StartVideoCapture) [StopVideoCapture](Screen-StopVideoCapture) [GetCapturedImage](Screen-GetCapturedImage)
