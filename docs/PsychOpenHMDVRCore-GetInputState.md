# [PsychOpenHMDVRCore('GetInputState')](PsychOpenHMDVRCore-GetInputState) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

input = PsychOpenHMDVRCore('GetInputState', openhmdPtr, controllerType);

Return current state of input device 'controllerType' associated with [OpenHMD](OpenHMD)  
device 'openhmdPtr'.  
  
'controllerType' can be a mask of the follwing values:  
OVR.[ControllerType](ControllerType)\_LTouch = Left touch controller (Left tracked hand).  
OVR.[ControllerType](ControllerType)\_RTouch = Right touch controller (Right tracked hand).  
OVR.[ControllerType](ControllerType)\_Remote = Oculus remote control or other remote controls / HMD  
controls.  
OVR.[ControllerType](ControllerType)\_XBox = [XBox](XBox) controller - Currently not supported.  
OVR.[ControllerType](ControllerType)\_Active = Whatever controller is connected and active.  
  
'input' is a struct with fields reporting the following status values of the  
controller:  
'Valid' = 1 if 'input' contains valid results, 0 if input status is  
invalid/unavailable.  
'ActiveInputs' = Bitmask of which 'input' contains valid results, or 0 if input  
completely unavailable.  
The following flags will be logical or'ed together if the corresponding input  
category is valid, ie. provided with actual input date from some physical input  
source element, controller etc.:  
+1  = 'Buttons' gets input from some real buttons or switches.  
+2  = 'Touches' gets input from some real touch/proximity sensors or gesture  
recognizers.  
+4  = 'Trigger' gets input from some real analog trigger sensor or gesture  
recognizer.  
+8  = 'Grip' gets input from some real analog grip sensor or gesture recognizer.  
+16 = 'Thumbstick' gets input from some real thumbstick, joystick or trackpad or  
similar 2D sensor.  
'Time' = Time in seconds when controller state was last updated.  
'Buttons' = Vector with each positions value corresponding to a specifc button  
being pressed (1) or released (0). The OVR.Button\_XXX constants map button names  
to vector indices (like [KbName](KbName)() does for [KbCheck](KbCheck)()).  
'Touches' = Vector with touch values as described by the OVR.Touch\_XXX  
constants. Works like 'Buttons'.  
'Trigger'(1/2) = Left (1) and Right (2) trigger: Value range 0.0 - 1.0, filtered  
and with dead-zone.  
'TriggerNoDeadzone'(1/2) = Left (1) and Right (2) trigger: Value range 0.0 -  
1.0, filtered.  
'TriggerRaw'(1/2) = Left (1) and Right (2) trigger: Value range 0.0 - 1.0, raw  
values unfiltered.  
'Grip'(1/2) = Left (1) and Right (2) grip button: Value range 0.0 - 1.0,  
filtered and with dead-zone.  
'GripNoDeadzone'(1/2) = Left (1) and Right (2) grip button: Value range 0.0 -  
1.0, filtered.  
'GripRaw'(1/2) = Left (1) and Right (2) grip button: Value range 0.0 - 1.0, raw  
values unfiltered.  
'Thumbstick' = 2x2 matrix: Column 1 contains left thumbsticks [x;y] axis values,  
column 2 contains right sticks [x;y] axis values. Values are in range -1 to +1,  
filtered and with deadzone applied.  
'ThumbstickNoDeadzone' = Like 'Thumbstick', filtered, but without a deadzone  
applied.  
'ThumbstickRaw' = 'Thumbstick' raw date without deadzone or filtering applied.  
  
  


###See also:
Start Stop [GetTrackingState](PsychOpenHMDVRCore-GetTrackingState)
