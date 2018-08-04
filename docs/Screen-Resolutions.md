# [Screen('Resolutions')](Screen-Resolutions) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Query a list of all supported and valid display settings for screen  
"screenNumber" and display output "outputId". If the optional 'outputId' is  
omitted, the unified settings of the screen are returned. Currently 'outputId'  
is only honored on Linux, ignored on other systems.  
You can set your display to one of the supported combinations of settings via  
the [Screen](Screen)('Resolution') command.  
Returns an array of structs "resolutions", where each element in the array is a  
struct that describes one valid combination of resolution, color depth and  
refresh rate. Fields are self explanatory.  
Please note that unless you have good reason to do so, especially the color  
depth value "newPixelSize" should usually not be changed. Usually it is 32 bpp  
or 24 bpp. A setting of 16 bpp will disable alpha-blending and create  
drastically reduced color resolution of 5 bits per color channel. A setting of 8  
bpp is not supported at all on [MacOS](MacOS)/X and will create artifacts on all other  
systems. Use a size of 32 bpp even for clut animation. This function may not  
work on all MS-Windows setups, your mileage may vary.  
Please note that there are a couple of helper functions in the [PsychOneLiners](PsychOneLiners)  
directory of Psychtoolbox which can simplify the task of switching resolutions.  
That functions are probably more convenient to use than the low-level [Screen](Screen)  
functions for display settings...   


###See also:
Screen('Resolution')
