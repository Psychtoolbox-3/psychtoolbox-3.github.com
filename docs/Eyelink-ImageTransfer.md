# [Eyelink('ImageTransfer')](Eyelink-ImageTransfer) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction

[status] = Eyelink('ImageTransfer', imagePathOrImageMatrix [, xPosition=0][, yPosition=0][, width=0][, height=0][, trackerXPosition=0][, trackerYPosition=0][, xferoptions=0]);

This function transfers a 8 bpc image to the tracker computer for use as a  
backdrop for gaze cursors.  
'imagePathOrImageMatrix' can be the filename of an uncompressed 8 bpc Microsoft  
BMP bitmap image file with 3 (RGB) or 4 (RGBA) color channels. It also can be a  
uint8() image matrix with either 1 layer grayscale image, or a 3 layer RGB color  
image, or a 4 layer RGBA color image with alpha channel. You can generate the  
matrix in Octave/Matlab, via Psychtoolbox functions like [Screen](Screen)('GetImage'), or  
you can load an image file of a supported image file format via the imread()  
function. This allows for way more flexibility than bmp files.  
'width' and 'height' define output image size for display on the tracker  
computer. If set to zero, full input image height and width will be used.  
Otherwise you could use 'xPosition' and 'yPosition' to define a source region in  
the input image that should be displayed on the tracker computer, and  
'trackerXPosition' and 'trackerYPosition' would define the start position of  
that subimage on the display of the tracker computer.  
'xferoptions' Transfer options set with bitwise OR of the following constants,  
determines how the image is processed before display on the tracker computers  
operator display:  
 0 Averaging combined pixels - the default  
 1 Choosing darkest and keep thin dark lines  
 2 Choosing darkest and keep thin white lines and control how image size is  
reduced to fit tracker display  
 4 Maximizes contrast for clearest image  
 8 Disables the dithering of the image  
 16 Converts the image to grayscale (grayscale works best for [EyeLink](EyeLink)-I, text,  
etc.)  
  


###See also:

