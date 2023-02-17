# [PsychHID('USBControlTransfer')](PsychHID-USBControlTransfer) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction

[recData, count] = PsychHID('USBControlTransfer', usbHandle, bmRequestType, bRequest, wValue, wIndex, wLength [, outData][, timeOutMSecs=10000])

Communicates with a USB device via the control endpoint, also known as a control  
transfer.  
The results of in-transfers are returned in the 1st return argument 'recData' as  
a uint8() row vector of length 'wLength'. The amount of actually received data  
can be less than 'wLength' and is returned in the 2nd return argument 'count'.  
Therefore, in case of shortened in-transfers, 'count' can be less than 'wLength'  
(which is also the length of 'recData' (iow. length(recData)).  
In case of an out-transfer, 'recData' does not exist, and 'count' will instead  
be the 1st and only return argument, reporting the amount of actual data sent to  
the device. 'outData' must be a uint8() vector of at least 'wLength' bytes for  
out-transfers, but all bytes beyond the first 'wLength' bytes will be ignored.  
The actual number of bytes transfered in any direction is returned in return  
argument 'count'.  
Please note that for control transfers where an endpoint (2) or interface (1) is  
the recipient, ie. where ismember(bitand(bmRequestType, 0x1f), [1, 2]), the  
interface (or associated interface of the endpoint) must be explicitely claimed  
via [PsychHID](PsychHID)('USBClaimInterface', usbHandle, interface); before calling the  
control transfer. Interface number (1) or endpoint address (2) are specified in  
'wIndex'. The only exception from this rule is endpoint 0, or control transfers  
to other targets, e.g., the device itself.  
'usbHandle' is the handle of the USB device to control.  
'bmRequestType' is the type of request, an 8 bit bit-mask: If bit 7 is set, this  
defines an in-transfer from device to host and 'recData' will be filled with at  
most 'wLength' bytes received from the device. Otherwise it defines a transfer  
from host to device and at most 'wLength' bytes will be transferred from  
'outData' to the device.  
'bRequest' is the 8 bit range request id.  
'wValue' and 'wIndex' are device- and request specific values in the 16 bit  
range 0 - 65535.  
'wLength' is the amount of data to return at most on an in-transfer, or the  
amount of data to send at most for an out-transfer in the optional uint8 vector  
'outData'. 'outData' must have at least as many elements as the value of  
'wLength'!  
'timeOutMSecs' is an optional timeout for the operation, in milliseconds.  
Default is 10000 msecs. A value of zero means to never time out, but wait  
indefinitely.  
  


###See also:
[OpenUSBDevice](PsychHID-OpenUSBDevice) [USBClaimInterface](PsychHID-USBClaimInterface) [USBBulkTransfer](PsychHID-USBBulkTransfer) [USBInterruptTransfer](PsychHID-USBInterruptTransfer)
