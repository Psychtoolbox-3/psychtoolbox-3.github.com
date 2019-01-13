# [PsychHID('ReceiveReportsStop')](PsychHID-ReceiveReportsStop) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction

err = PsychHID('ReceiveReportsStop', deviceNumber)

Stop receiving and saving reports from the specified USB HID device.  
Calling [ReceiveReports](ReceiveReports) enables callbacks (forever) for the incoming reports from  
that device; call [ReceiveReportsStop](ReceiveReportsStop) to halt acquisition of further reports for  
this device; you can resume acquisition by calling [ReceiveReports](ReceiveReports) again. Call  
[GiveMeReports](GiveMeReports) to get all the received reports and empty PsychHID's internal  
store for that device. "deviceNumber" specifies which device. The returned value  
"err.n" is zero upon success and a nonzero error code upon failure, as spelled  
out by "err.name" and "err.description".   


###See also:
[SetReport](PsychHID-SetReport), [ReceiveReports](PsychHID-ReceiveReports), [GiveMeReports](PsychHID-GiveMeReports)
