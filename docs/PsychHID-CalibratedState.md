# [PsychHID('CalibratedState')](PsychHID-CalibratedState) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Return the calibrated immediate state of the specified element on the specified  
device. Elements states have both a nominal and an actual range.  For joysticks  
and other rotary elements the actual range of reported state values is smaller  
than than the nominal range.  The HID driver stores the most extreme values  
reported by the element in the calMin and calMax fields of the element structure  
returned by [PsychHID](PsychHID)('Elements'); The actual state as returned by 'RawState' is  
scalled using calMin and calMax and returned by 'CalibratedState'. Insure that  
calMin and calMax hold true max and min values by swinging the device element to  
its poles before calling 'CalibratedState'.  


###See also:

