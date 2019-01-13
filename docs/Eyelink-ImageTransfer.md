# [Eyelink('ImageTransfer')](Eyelink-ImageTransfer) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction

[status] = Eyelink('ImageTransfer', imagePath [, xPosition=0][, yPosition=0][, width=0][, height=0][, trackerXPosition=0][, trackerYPosition=0][, xferoptions=0]);

This function transfers a 24-bit or 32-bit bitmap to the tracker PC as backdrop  
for gaze cursors.  
'width' and 'height' define image size. If set to zero will use bitmap height  
and width.  
'xferoptions' Transfer options set with bitwise OR of the following constants,  
determines how bitmap is processed:  
 0 Averaging combined pixels  
 1 Choosing darkest and keep thin dark lines  
 2 Choosing darkest and keep thin white lines and control how bitmap size is  
reduced to fit tracker display  
 4 Maximizes contrast for clearest image  
 8 Disables the dithering of the image  
 16 Converts the image to grayscale (grayscale works best for  
[EyeLinkI](EyeLinkI),text,etc.)  
  


###See also:

