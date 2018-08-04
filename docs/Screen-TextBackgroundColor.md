# [Screen('TextBackgroundColor')](Screen-TextBackgroundColor) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Read/Set the text background color for the specified window.  
The background color defaults to [0,0,0,0], i.e., a fully transparent black.  
This means that the background is invisible. You'll need to assign at least a  
non-zero alpha-value for the background to be drawn. With some text renderers  
you'll also need to enable user-controlled text alpha-blending via a call to  
[Screen](Screen)('[Preference](Preference)', 'TextAlphaBlending', 1); for text background to be drawn,  
e.g., for the Apple OSX legacy text renderer 0. If you want text to be drawn  
with sub-pixel anti-aliasing then some renderers need you to set an opaque text  
background color - with an alpha value of 255, or whatever the maximum value is  
for the selected color mode.  
  


###See also:

