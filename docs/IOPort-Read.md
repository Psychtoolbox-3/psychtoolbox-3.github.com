# [IOPort('Read')](IOPort-Read) 
##### [Psychtoolbox](Psychtoolbox)>[IOPort](IOPort).{mex*} subfunction

[data, when, errmsg] = IOPort('Read', handle [, blocking=0] [, amount]);

Read data from device, specified by 'handle'.  
Returned 'data' will be a row vector of read data bytes. 'when' will be a  
receive timestamp of when the data read was complete. 'errmsg' will be a human  
readable char string with an error message if any error occured, otherwise an  
empty string. The optional flag 'blocking' if set to 0 will ask the read  
function to not block, but return immediately: The read function will return  
whatever amount of data is currently available in the internal input queue, but  
at most 'amount' bytes if 'amount' is specified. If no data is available, it  
will return an empty matrix. This is the default.  
If 'blocking' is set to 1, you must specify the 'amount' of bytes to receive and  
the function will wait until that exact amount of data is available, then return  
it.Even in blocking mode, the function will return if no data becomes available  
within the time period specified by the configuration setting 'ReadTimeout' (see  
help for 'OpenSerialPort' for description). In some situations, the read  
function may return less data than requested, e.g., in specific error cases,  
where a read could only get partially satisfied.  


###See also:
'Write', 'OpenSerialPort', 'ConfigureSerialPort'
