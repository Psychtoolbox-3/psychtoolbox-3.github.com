# [IOPort('Write')](IOPort-Write) 
##### [Psychtoolbox](Psychtoolbox)>[IOPort](IOPort).{mex*} subfunction


Write data to device, specified by 'handle'.  
'data' must be a vector of data items to write, or a matrix (in which case data  
in the matrix will be transmitted in column-major order, ie., first the first  
column, then the 2nd column etc...), either with data elements of uint8 class or  
a (1 Byte per char) character string. The optional flag 'blocking' if set to 0  
will ask the write function to not block, but return immediately, ie. data is  
sent/written in the background while your code continues to execute - There may  
be an arbitrary delay until data transmission is really finished. The default  
setting is 1, ie. blocking writes - The function waits until data transmission  
is really finished. You can also use blocking == 2 to request a different mode  
for blocking writes, where [IOPort](IOPort) is polling for write-completion instead of a  
more cpu friendly wait. This may decrease latency for certain applications.  
Another even more agressive polling method is implemented via blocking == 3 on  
Linux systems with some limited set of hardware, e.g., real native serial ports.  
On systems without any support for specific polling modes, the 2 or 3 settings  
are treated as a standard blocking write.  
  
Optionally, the function returns the following return arguments:  
'nwritten' Number of bytes written -- Should match amount of data provided on  
success.  
'when' A timestamp of write completion: This is only meaningful in blocking  
mode!  
'errmsg' A system defined error message if something wen't wrong.  
The following three timestamps are for low-level debugging and special purpose:  
'prewritetime' A timestamp taken immediately before submitting the write  
request. 'postwritetime' A timestamp taken immediately after submitting the  
write request. 'lastchecktime' A timestamp taken at the time of last check for  
write completion if applicable.   


###See also:

