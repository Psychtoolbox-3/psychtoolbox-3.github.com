# [PsychOpenXRCore('GetInputState')](PsychOpenXRCore-GetInputState) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

input = PsychOpenXRCore('GetInputState', openxrPtr, controllerType);

Return current state of input device 'controllerType' associated with [OpenXR](OpenXR)  
device 'openxrPtr'.  
  
'controllerType' can be one of the following values:  
OVR.[ControllerType](ControllerType)\_LTouch = Left touch controller (Left tracked hand).  
OVR.[ControllerType](ControllerType)\_RTouch = Right touch controller (Right tracked hand).  
OVR.[ControllerType](ControllerType)\_Remote = Connected remote control or similar, e.g., control  
buttons on a HMD.  
OVR.[ControllerType](ControllerType)\_XBox = Microsoft [XBox](XBox) controller or some equivalent gamepad.  
OVR.[ControllerType](ControllerType)\_Active = Whatever controller is connected and active.  
  
'input' is a struct with fields reporting the following status values of the  
controller:  
'Valid' Reports 1 if 'input' contains any valid results, or 0 if input is  
completely unavailable, e.g., because there isn't any input hardware connected  
and active, or Psychtoolbox lost XR input focus.  
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
+32 = 'Thumbstick2' gets input from some real secondary thumbstick, joystick or  
trackpad or similar 2D sensor.  
  
'Time' = Time in seconds when controller state was last updated.  
'Buttons' = Vector with each positions value corresponding to a specifc button  
being pressed (1) or released (0). The OVR.Button\_XXX constants map button names  
to vector indices (like [KbName](KbName)() does for [KbCheck](KbCheck)()).  
'Touches' = Vector with touch values as described by the OVR.Touch\_XXX  
constants. Works like 'Buttons'.  
'Trigger'(1/2) = Left (1) and Right (2) trigger: Value range 0.0 - 1.0.  
'Grip'(1/2) = Left (1) and Right (2) grip button: Value range 0.0 - 1.0.  
'Thumbstick' = 2x2 matrix: Column 1 contains left thumbsticks [x ; y] axis  
values, column 2 contains right sticks [x ; y] axis values. Values are in range  
-1 to +1. Note that some controllers do not have thumbsticks, but trackpads  
instead. These would be exposed as Thumbstick as well, being 2D input.  
'Thumbstick2' = 2x2 matrix: Column 1 contains left thumbsticks [x ; y] axis  
values, column 2 contains right thumbsticks [x ; y] axis values. Values are in  
range -1 to +1. Only a few controllers have a 2nd thumbstick for each hand, and  
it is often a trackpad instead of a thumbstick.  
  
  


###See also:
Start Stop [GetTrackingState](PsychOpenXRCore-GetTrackingState) [GetTrackersState](PsychOpenXRCore-GetTrackersState)
