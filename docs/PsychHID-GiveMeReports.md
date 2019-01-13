# [PsychHID('GiveMeReports')](PsychHID-GiveMeReports) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Return, as an output argument, all the saved reports from the connected USB HID  
device.  
"deviceNumber" specifies which device.  
If supplied, the optional "reportBytes" argument imposes a maximum length on  
each report; if necessary, reports will be shortened, but not lengthened. (This  
feature allows you to receive a report containing just the data you requested  
when the firmware insists on providing a fixed length report that may be longer  
than the valid data.  
"reports" is a struct array, with a struct for each report. "reports(i).report"  
is a uint8 vector with received report data. If your device uses reportID then  
the first byte of the report is the reportID, the following bytes contain the  
actual received report data. Otherwise (reportID==0), the received data starts  
already in the first byte of reports(i).report.  
"reports(i).device" is the device number of the device.  
"reports(i).time" is the [GetSecs](GetSecs) time at which it was received from the system.  
This is \*not\* the time when the hardware itself received the report, therefore  
this value is of limited use and should be considered unreliable.  
The returned value "err.n" is zero upon success and a nonzero error code upon  
failure, as spelled out by "err.name" and "err.description".   


###See also:
[SetReport](PsychHID-SetReport), [GetReport](PsychHID-GetReport), [ReceiveReports](PsychHID-ReceiveReports), [ReceiveReportsStop](PsychHID-ReceiveReportsStop), [GiveMeReports](PsychHID-GiveMeReports).
