# [Psychtoolbox](Psychtoolbox)
##### >[Psychtoolbox](Psychtoolbox)

Psychtoolbox.  
Version 3.0.15      8 November 2018  
  
The Psychophysics Toolbox is a collection of Octave and Matlab functions  
that extend the language to give you exquisite control of your computer  
to test observers with research-grade dynamic stimuli.  
  
Every Psychtoolbox function has its own documentation available through  
the Matlab HELP command, and, in the case of MEX files, through the  
function itself. We've tried hard to make these individual bits of  
documentation clear, accurate, and complete. We're grateful to receive  
corrections.  
  
We've mostly followed Mathworks's help-text conventions, but note that in  
our help text we designate optional arguments to function calls by  
embracing them with square brackets. You're not meant to include these  
brackets when you actually call the function. For example, "help [Snd](Snd)"  
will tell you this:  
  
err = [Snd](Snd)(command,[sig],[rate])  
  
meaning that the "command" argument is required and the "sig" and "rate"  
arguments are optional. A typical call to [Snd](Snd) looks like this:  
  
[Snd](Snd)('Play', mysoundsignal)  
  
The most important and generally useful functions, especially [Screen](Screen), are  
in [PsychBasic](PsychBasic). The [PsychDemos](PsychDemos) will show you how to do useful things in  
Matlab with the Psychtoolbox. Try these:  
  
help [PsychDemos](PsychDemos)  
help [PsychBasic](PsychBasic)  
help [Screen](Screen)  
[Screen](Screen) [OpenWindow](OpenWindow)?  
  
The folder [PsychDocumentation](PsychDocumentation) contains bits of documentation about  
technical implementation details, how to solve specific tasks and how to  
troubleshoot common problems.  
  
To read more, look at the "intro" and "docs" pages at the web site. The  
web site also has advice about getting help, the Psychtoolbox forum, and  
the latest information about bugs and new releases:  
  
http://psychtoolbox.org/  
  
Peter Scarfe has written a large set of nice and beginner friendly  
Psychtoolbox tutorial scripts.  
  
You can find them at http://peterscarfe.com/ptbtutorials.html  
  
If you want to acknowledge use of this software when you publish your  
research, you might say something like this, "We wrote our experiments in  
Matlab, using the Psychophysics Toolbox extensions (Kleiner et al, 2007)"  
  
Kleiner M, Brainard D, Pelli D, 2007, "What's new in Psychtoolbox-3?"  
Perception 36 ECVP Abstract Supplement.  
  
  
  
### Folders and their contents:  
  
[PsychAlpha](PsychAlpha)             - Under development. Experimental, risky, undocumented.  
[PsychAlphaBlending](PsychAlphaBlending)     - [OpenGL](OpenGL) alpha-channel blending utilities and constants.    
[PsychBasic](PsychBasic)             - Basic support routines for psychophysics.  
[PsychCal](PsychCal)               - Calibrate your video monitors.  
[PsychCalDemoData](PsychCalDemoData)       - Demo calibration data.  
[PsychColorimetric](PsychColorimetric)      - Colorimetric calculations.  
[PsychColorimetricData](PsychColorimetricData)  - Standard colorimetric data.  
[PsychContributed](PsychContributed)       - Contributed programs.  
[PsychDemos](PsychDemos)             - Show how to use the Psychtoolbox.  
[PsychDocumentation](PsychDocumentation)     - Documentation about specific topics.  
[PsychFiles](PsychFiles)             - Process text files.  
[PsychGamma](PsychGamma)             - Fit monitor gamma functions.  
[PsychGLImageProcessing](PsychGLImageProcessing) - Built-in image processing via graphics hardware.  
[PsychGPGPU](PsychGPGPU)             - General purpose accelerated computing on [GPUs](GPUs).  
[PsychHardware](PsychHardware)          - Interface to plug-in hardware.  
[PsychInitialize](PsychInitialize)        - Initialize and deinitialize MATLAB  
[PsychMatlabTests](PsychMatlabTests)       - Document the few bugs in Matlab 5.2.1.  
[PsychObsolete](PsychObsolete)          - Obsolete routines, still present for compatibility.  
[PsychOpenGL](PsychOpenGL)            - Routines for low-level access to [OpenGL](OpenGL) 3D graphics.  
[Psychometric](Psychometric)           - [Psychometric](Psychometric) function fitting.  
[PsychOneliners](PsychOneliners)         - Trivial, but handy, functions.  
[PsychOptics](PsychOptics)            - Optics calculations, mostly for human optics.  
[PsychPriority](PsychPriority)          - [Priority](Priority) and [Rush](Rush).  (formerly within [PsychBasic)](PsychBasic))  
[PsychProbability](PsychProbability)       - Probability and statistics.  
[PsychRadiometric](PsychRadiometric)       - Radiometric/photometric calculations and conversions.  
[PsychRects](PsychRects)             - Manipulate rectangles for drawing.  
[PsychSignal](PsychSignal)            - Signal processing and math routines.  
[PsychSound](PsychSound)             - Sound input and output routines.  
[PsychStairCase](PsychStairCase)         - Adaptive staircase procedure.  
[PsychTests](PsychTests)             - Evaluate performance of software and hardware.  
[PsychVideoCapture](PsychVideoCapture)      - Functions for realtime video capture.  
Quest                  - Threshold estimation procedure.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Contents.m</code>
</div>

{{category}}