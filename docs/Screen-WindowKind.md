# [Screen('WindowKind')](Screen-WindowKind) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

kind=Screen(windowPtr, 'WindowKind');

What kind of windowPtr is this? Returns 0 if it's invalid, -1 an offscreen  
window or a normal texture, 1 our onscreen, 2 Matlab's onscreen, 3 a  
non-redrawable texture, 4 a proxy window. "windowPtr" can be an array of window  
pointers, eg [Screen](Screen)([Screen](Screen)('Windows'),'WindowKind'). To count [Screen](Screen)'s onscreen  
windows, do this: sum(1==[Screen](Screen)([Screen](Screen)('Windows'),'WindowKind')).  
Please note that the current PTB doesn't have textures of type '3', i.e. all  
textures are also useable as offscreen windows and vice versa. Also, it is not  
possible to refer to the Matlab window itself in Psychtoolbox-3 so won't every  
encounter the value '2' - it only exists for backwards compatibility with old  
Psychtoolboxes.   


###See also:

