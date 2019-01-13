# [Eyelink('ReceiveFile')](Eyelink-ReceiveFile) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction

[status =] Eyelink('ReceiveFile',['filename'], ['dest'], ['dest_is_path'])

 If <src\> is omitted, tracker will send last opened data file.  
 If <dest\> is omitted, creates local file with source file name.  
 Else, creates file using <dest\> as name.  If <dest\_is\_path\> is supplied and  
non-zero  
 uses source file name but adds <dest\> as directory path.  
 returns: file size if OK, 0 if file transfer was cancelled, negative =  error  
code  


###See also:

