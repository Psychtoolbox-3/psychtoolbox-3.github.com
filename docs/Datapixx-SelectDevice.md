# [Datapixx('SelectDevice')](Datapixx-SelectDevice) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

selectedDevice = Datapixx('SelectDevice' [, deviceType=-1] [, deviceName]);

Select a specific [VPixx](VPixx) hardware device for subsequent operations.  
If an experimental system contains multiple [VPixx](VPixx) hardware devices (eg: a  
[PROPixx](PROPixx) and a [PROPixx](PROPixx) Controller,  
then this command can be used to indicate which of the devices should be  
targeted for subsequent operations.  
-"deviceType" can take one of the following values:  
   -1: Library will automatically attempt to operate on the appropriate device  
(default value)  
    1: Operate on a [DATAPixx](DATAPixx) CRT driver  
    2: Operate on a [VIEWPixx](VIEWPixx)  
    3: Operate on a [PROPixx](PROPixx) Controller  
    4: Operate on a [PROPixx](PROPixx) Projector  
    5: Operate on a [DATAPixx2](DATAPixx2)  
    6: Operate on a [TRACKPixx](TRACKPixx)  
In the event that an experimental system contains multiple devices of the same  
type,  
then "deviceName" can be used to target the device which has been given a  
specific name.  
Contact support@vpixx.com for instructions on assigning unique names to  
individual devices.  
  


###See also:
Open
