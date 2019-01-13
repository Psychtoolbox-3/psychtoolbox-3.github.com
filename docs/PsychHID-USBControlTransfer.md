# [PsychHID('USBControlTransfer')](PsychHID-USBControlTransfer) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Communicates with a USB device via the control endpoint, aka control transfer.  
The results of out-transfers are returned in return argument 'outData' as a  
uint8 array.  
'usbHandle' is the handle of the USB device to control. 'bmRequestType' is the  
type of reqest: If bit 7 is set, this defines a transfer from device to host and  
'outData' will be filled with at most 'wLength' bytes received from the device.  
Otherwise it defines a transfer from host to device and at most 'wLength' bytes  
will be transfered from 'inData' to the device.  
'bRequest' is the request id.  
'wValue' and 'wIndex' are device- and request specific values. 'wLength' is the  
amount of data to return at most on a out-transfer, or the amount of data  
provided for an in-transfer in the optional uint8 vector 'inData'. 'inData' must  
have at least as many elements as the value of 'wLength'!   


###See also:

