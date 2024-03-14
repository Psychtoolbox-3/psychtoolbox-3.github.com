# [Eyelink('OpenFile')](Eyelink-OpenFile) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction

[status =] Eyelink('OpenFile', filename [, dontOpenExisting=0])

Opens an EDF file 'filename' on the tracker computer, closes any existing file.  
If a file of the name 'filename' already exists, it will be overwritten!  
The optional flag 'dontOpenExisting' only exists for backwards compatibility,  
and to warn users to \*not\* use or rely on this flag in their scripts, as it  
never ever worked as intended! If it is now set to a non-zero value, then  
Eyelink will abort with an error message to that effect, to protect users from  
potential data loss. The intended purpose of setting the flag to a non-zero  
value was that a data file 'filename' would only be opened, and thereby created,  
if it would not already exist. Otherwise the function would abort with an error.  
According to authoritative feedback from SR-Research, this does not and did not  
ever work, and it is currently impossible to implement this  
functionality.Returns 0 if success, else error code  


###See also:

