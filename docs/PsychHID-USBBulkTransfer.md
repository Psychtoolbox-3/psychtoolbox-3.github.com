# [PsychHID('USBBulkTransfer')](PsychHID-USBBulkTransfer) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction

[countOrRecData] = PsychHID('USBBulkTransfer', usbHandle, endPoint, length [, outData][, timeOutMSecs=10000])

Performs a synchronous USB bulk transfer.  
The function will automatically claim interface \#0 to enable this transfer,  
unless you call [PsychHID](PsychHID)('USBClaimInterface', usbHandle, interfaceId) first to  
claim a different interface 'interfaceId' for accessing the wanted endPoint.  
The results of in-transfers are returned in 'countOrRecData' as an uint8() row  
vector. The amount of actually received data can be less than the requested  
'length'. In case of an out-transfer, 'countOrRecData' reports the amount of  
actual data sent.  
'usbHandle' is the handle of the USB device to perform the transfer to or from.  
'endPoint' is the USB end-point address: If its bit 7 is set, this requests an  
in-transfer from device to host and 'countOrRecData' will contain at most  
'length' bytes received from the device. Otherwise it requests an out-transfer  
from host to device and 'outData' will be sent to the device.  
'length' is the amount of data to return on an in-transfer. It is ignored for  
out-transfers.  
'outData' is a uint8() data vector to send. It will be ignored for in-transfers.  
'timeOutMSecs' is an optional timeout for the operation, in milliseconds.  
Default is 10000 msecs. A value of zero means to never time out, but wait  
indefinitely for transfer completion.  
  


###See also:
[OpenUSBDevice](PsychHID-OpenUSBDevice) [USBClaimInterface](PsychHID-USBClaimInterface) [USBControlTransfer](PsychHID-USBControlTransfer) [USBInterruptTransfer](PsychHID-USBInterruptTransfer)
