# [PsychOpenXRCore('ReferenceSpaceType')](PsychOpenXRCore-ReferenceSpaceType) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

[oldType, spaceSize] = PsychOpenXRCore('ReferenceSpaceType', openxrPtr [, newType]);

Specify the type of reference space for [OpenXR](OpenXR) device 'openxrPtr'.  
This returns the current type of the current reference space in 'oldType'.  
Optionally you can specify a new reference space type as 'newType'. The number  
is one of the reference space types defined by [OpenXR](OpenXR) or one of its extensions.  
See the section "Reference Spaces" in the [OpenXR](OpenXR) spec.  
Common types are as follows, note that only 1 and 2 are supported by all  
runtimes:  
1 = Origin is at eye height and head-locked == XR\_REFERENCE\_SPACE\_TYPE\_VIEW.  
2 = Origin is at runtime defined local tracking space origin ==  
XR\_REFERENCE\_SPACE\_TYPE\_LOCAL.  
3 = Origin is at floor height of a flat rectangular stage tracking space ==  
XR\_REFERENCE\_SPACE\_TYPE\_STAGE.  
1000038000 = Unbounded space for large tracking areas ==  
XR\_REFERENCE\_SPACE\_TYPE\_UNBOUNDED\_MSFT.  
The origin of type 2 and 3 gets defined by the system during [OpenXR](OpenXR) runtime  
specific world and sensor calibration, e.g., in some setup GUI application or  
configuration file, or other procedure.  
  
'spaceSize' is a [width, height] vector with the width and height (in meters) of  
the reference spaces walking area, ie. a rectangle whose sides are aligned with  
the x and y axis, the origin of the space being the center of the rectangle. The  
rectangle defines an area that is clear of obstacles and tracked, therefore  
meaningfully and safely walkable by the subject during the XR session. If this  
information is not available then returns an empty [] 'spaceSize'.  
  


###See also:
[GetTrackingState](PsychOpenXRCore-GetTrackingState) [GetInputState](PsychOpenXRCore-GetInputState)
