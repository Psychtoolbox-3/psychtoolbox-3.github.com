# [PsychHID('USBClaimInterface')](PsychHID-USBClaimInterface) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction

PsychHID('USBClaimInterface', usbHandle, interfaceId)

Claim a USB interface.  
The function will try to detach kernel drivers potentially attached to the  
interface already. If a data transfer operation on an endpoint is requested  
before a specific interface has been claimed by calling this function, e.g., an  
[USBBulkTransfer](USBBulkTransfer) or [USBInterruptTransfer](USBInterruptTransfer) is attempted, then interface number 0  
will automatically first be claimed by default.  
  
'usbHandle' is the handle of the USB device to claim an interface from.  
'interfaceId' is the bInterfaceNumber of the interface to claim.  
  


###See also:
[OpenUSBDevice](PsychHID-OpenUSBDevice) [USBControlTransfer](PsychHID-USBControlTransfer) [USBBulkTransfer](PsychHID-USBBulkTransfer) [USBInterruptTransfer](PsychHID-USBInterruptTransfer)
