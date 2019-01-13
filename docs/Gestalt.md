# [Gestalt](Gestalt)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

gestaltBits = [Gestalt](Gestalt)(selector)  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[Gestalt](Gestalt) calls the eponymous Macintosh system function [Gestalt](Gestalt), a  
general-purpose function that reports on particular features of your   
computer.  [Gestalt](Gestalt) accepts "selector", a four-character string identifying  
the feature you wish to query and returns "gestaltBits", a 32-element  
logical array holding the result of the query.   
  
### For example:  
  
  gestaltbits = gestalt('sysa')  
  
     gestaltbits(32) will be 1 if run from a 680x0-based Macintosh, while  
     gestaltbits(31) will be 1 if run from a [PowerPC](PowerPC)-based Macintosh.   
  
For a list of four-character selector codes, see the Carbon [Gestalt](Gestalt)  
Manager Reference   
web http://developer.apple.com/ ;  
  
If the call to Carbon [Gestalt](Gestalt) returns an error then MATLAB [Gestalt](Gestalt) returns  
the error code in a double instead of gestaltBits in a logical array.  
[Gestalt](Gestalt) error codes are:  
  
  gestaltUnknownErr       -5550   An unknown error.  
  gestaltUndefSelectorErr -5551   An undefined selector was   
                                    passed to the [Gestalt](Gestalt) Manager.  
  gestaltDupSelectorErr   -5552   You tried to add an entry   
                                    that already existed.  
  gestaltLocationErr      -5553   The gestalt function ptr was not in the  
                                    system heap.  
  
In MATLAB 6.0 and greater the Psychtoolbox supplies [Gestalt](Gestalt). [Gestalt](Gestalt) is a   
work-alike implementation of the identically-named function previously  
provided by MATLAB.  The only differences between Psychtoolbox [Gestalt](Gestalt) and   
MATLAB [Gestalt](Gestalt) are:  
  
  1. Psychtoolbox [Gestalt](Gestalt) returns a struct holding information about  
     itself when passed 'Version', for example:  
    \>\> [Gestalt](Gestalt)('Version')  
  
    ans =   
  
         version: '1.0.3.62269826'  
           major: 1  
           minor: 0  
           point: 3  
           build: 62269826  
            date: 'Dec  7 2004'  
            time: '17:10:26'  
          module: '[Gestalt](Gestalt)'  
         project: 'OpenGL Psychtoolbox'  
              os: 'Apple OS X'  
        language: 'MATLAB'  
         authors: [1x1 struct]  
  
  2. Psychtoolbox [Gestalt](Gestalt) will return the error code in the event of any   
     [Gestalt](Gestalt) error.  MATLAB [Gestalt](Gestalt) will return the error code in the  
     event of error code -5551.  Its behavior for other error codes is  
     unknown.  
  
OS 9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
In MATLAB versions below 6.0 MATLAB supplies [Gestalt](Gestalt).   
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[Gestalt](Gestalt) does not exist in Windows.    
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [Screen](Screen)('Computer?'), [MacModelName](MacModelName), [AppleVersion](AppleVersion)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/Gestalt.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/Gestalt.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/Gestalt.m</code>
</div>

