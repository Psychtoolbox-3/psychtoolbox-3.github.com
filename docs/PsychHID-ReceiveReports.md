# [PsychHID('ReceiveReports')](PsychHID-ReceiveReports) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction

err=PsychHID('ReceiveReports',deviceNumber[,options])

Receive and save, internally, all reports from the specified USB HID device, now  
and forever more (unless stopped).  
Some parameters are persistent. When you don't explicitly supply a value they  
retain whatever value they had last time. They do have an initial default  
(built-in) that is present when [PsychHID](PsychHID) is first called after being [CLEARed](CLEARed).  
Non-persistent parameters have a fixed default that applies every time you call  
[PsychHID](PsychHID).  
The returned value "err.n" is zero upon success and a nonzero error code upon  
failure, as spelled out by "err.name" and "err.description". "deviceNumber"  
specifies which device.  
"options.print" =1 (initial default 0) enables diagnostic printing of a summary  
of each report when our callback routine receives it.  
"options.printCrashers" =1 (initial default 0) enables diagnostic printing of  
the creation of the callback source and its addition to the [CFRunLoop](CFRunLoop).  
"options.consistencyChecks" =1 (initial default 0) enables diagnostic printing  
of the consistency of all report structs. Very time consuming!  
"options.maxReports" (initial default 10000) allocate space for at least this  
many reports for the given device.  
"options.maxReportSize" (initial default 65) allocate this many bytes per  
report. Most HID devices don't send HID reports of more than 64 Bytes, so  
allowing for one extra byte for the reportID, a default of 65 Bytes is usually  
sufficient. If you need more, you can increase this value up to 8192 Bytes. If  
you need even more, contact us, because likely you are doing something wrong.  
Smaller values than 65 may make sense if you are very tight on memory.  
"options.secs" (initial default 0.010 s) is how long to allow the function to  
process reports received from all active HID devices. The operating system  
receives reports all the time after the first call to 'ReceiveReports' or  
'GetReport'. It has a small buffer capacity, discarding the oldest received  
reports if its small buffer is full. When requested by [PsychHID](PsychHID), the OS tranfers  
reports to [PsychHID](PsychHID) (for all devices for which [ReceiveReports](ReceiveReports) is still active).  
Thus reports are received from the OS only during your call to [ReceiveReports](ReceiveReports) or  
[GetReport](GetReport) [(GetReport]((GetReport) implies an automatic call to [ReceiveReports)](ReceiveReports)). You should  
call [ReceiveReports](ReceiveReports) frequently to avoid losing reports. Reports can be received  
from multiple devices during a single call to [ReceiveReports](ReceiveReports). Calling  
[ReceiveReports](ReceiveReports) enables callbacks (forever) for the incoming reports from that  
device; call [ReceiveReportsStop](ReceiveReportsStop) to halt acquisition of further reports for a  
device;  you can resume acquisition for a device by calling [ReceiveReports](ReceiveReports)  
again. Call [GiveMeReports](GiveMeReports) to get all the received reports and empty PsychHID's  
internal store for a device. [PsychHID](PsychHID) can hold up to options.maxReports reports,  
and discards new incoming reports when it has no room to hold them. For  
prolonged data acquisition you may need to call [GiveMeReports](GiveMeReports) periodically,  
emptying PsychHID's store before it becomes full.  
[PsychHID](PsychHID) was enhanced by adding HID commands to send and receive HID reports to  
support the PMD-1208FS. [PsychHID](PsychHID) is likely to work with other HID-compliant USB  
devices as well.  
The device-specific programming for the PMD-1208FS is entirely in the MATLAB M  
files of the Daq Toolbox; what is specific to the different operating systems is  
(hopefully) entirely in [PsychHID](PsychHID). [PsychHID](PsychHID) is entirely generic, following the  
HID standard; none of the internal code is specific to any device, but we tested  
it primarily with the PMD-1208FS, as well as keyboards, mice, and gamepads, so  
working with new devices may be an adventure.   


###See also:
[SetReport](PsychHID-SetReport), [ReceiveReportsStop](PsychHID-ReceiveReportsStop), [GiveMeReports](PsychHID-GiveMeReports)
