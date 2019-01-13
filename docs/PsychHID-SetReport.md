# [PsychHID('SetReport')](PsychHID-SetReport) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Send a report to the connected USB HID device.  
"deviceNumber" specifies which device.  
"reportType" is 2=output, 3=feature (0 to just echo arguments).  
"reportID" is either zero or an integer (1 to 255) specifying the topic, e.g.  
read analog, read digital, write analog, etc. If you provide a non-zero  
reportID, the first byte of your "report" will be overwritten with this  
reportID. You have to take this into account, ie., leave a leading byte of space  
for the reportID to avoid corrupting your actual report data. If reportID is  
zero, then your "report" will be sent as-is, without any special treatment of  
the first byte.  
"report" must be an array of char or integer (8-, 16-, 32-, or 64-bit, signed or  
unsigned) holding the correct total number of bytes.  
The returned value "err.n" is zero upon success and a nonzero error code upon  
failure, as spelled out by "err.name" and "err.description".  
  


###See also:
[GetReport](PsychHID-GetReport)
