# [Eyelink('SendFile')](Eyelink-SendFile) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction

[status =] Eyelink('SendFile', src, dest, dest_is_path)

This function sends a file to the Eyelink tracker. Source destination file name  
should be given. Using this function, an image or video can be uploaded from the  
display PC to the host Tracker PC.  
  
<src\> Name of local file (including extension).  
<dest\> Name of eye tracker file to write to (including extension).  
<dest\_is\_path\> If nonzero, appends file name to <dest\> as a directory path.  
  
Returns:  
 size of file if transferred file size is equal to the real file size.  
 -1 if fail to connect tracker ftpd.  
 -2 if fail to open file.  
 -4 if fail to receive reply from tracker ftpd.  
 -5 if transferred file size is unequal to the real file size.  


###See also:

