# [PsychHID('GetReport')](PsychHID-GetReport) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Get a report from the connected USB HID device.  
"deviceNumber" specifies which device. "reportType" is 1=input, 3=feature (0 to  
just echo arguments).  
"reportID" is either zero or an integer (1 to 255) specifying the topic, e.g.  
read analog, read digital, write analog, etc.  
"reportBytes" is maximum size of report to retrieve in bytes.  
"report" is a uint8 vector with the data of the retrieved report. If your device  
uses reportID for this report then the first byte of the report is the reportID,  
otherwise the first byte will be already the first byte of the retrieved report.  
The returned value "err.n" is zero upon success and a nonzero error code upon  
failure, as spelled out by "err.name" and "err.description". When nothing has  
been received, "report" will be an empty matrix. However, some devices may send  
a zero-length report, which will also result in "report" being an empty matrix.  
Resolving this ambiguity, "err.reportLength" is -1 when no report was received,  
and the report length in bytes when a report was received.  
 Each time that you use a new deviceNumber, [PsychHID](PsychHID):[GetReport](GetReport) enables callbacks  
for the incoming reports from that device. If you use many devices, all their  
reports will cause callbacks, as documented in the diagnostic printout. You can  
disable a callback that you no longer want by calling [ReceiveReportsStop](ReceiveReportsStop). This  
saves computation time.   


###See also:
[SetReport](PsychHID-SetReport), [ReceiveReports](PsychHID-ReceiveReports), [ReceiveReportsStop](PsychHID-ReceiveReportsStop), [GiveMeReports](PsychHID-GiveMeReports).
