# [MOAL](MOAL)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSound](PsychSound)>[MOAL](MOAL)

Psychtoolbox:[PsychSound](PsychSound):MOAL Contents of MOAL Matlab-[OpenAL](OpenAL) toolbox  
  
Moal is a collection of M-File wrappers and a MEX file that allow to call  
all [OpenAL](OpenAL) commands from Matlab as one is used to from the C programming  
language.  
  
### Directory structure is as follows:   
  
    moaldemo.m          -- demonstration of how to use the toolbox  
  
    core/  
  
        (first group:  main toolbox functions)  
  
        moalcore.mexmac -- main MEX interface to [OpenAL](OpenAL) functions  
        oalconst.mat    -- constants used by [OpenAL](OpenAL) routines  
  
    source/  
  
        (first group:  files that generate interface code)  
  
        al\_auto\_init.c  -- file used in generating al\_auto.c;  contains  
                           top portion of file, i.e., \#includes, etc.  
        oalconst.m      -- MATLAB script that searches through [OpenAL](OpenAL) header  
                           files for \#defined constants, and writes them  
                           to oalconst.mat as variables  
  
        (second group:  files that compile to produce moalcore.mexmac)  
  
        al\_auto.c       -- automatically generated interfaces to [OpenAL](OpenAL) functions  
        al\_manual.c     -- manually generated interfaces to [OpenAL](OpenAL) functions  
        alm.c           -- ALM library of ALC like functions.  
        moalcore.c      -- main MEX interface function  
        moaltypes.h     -- useful data types  
        windowshacks.c  -- hacks needed for Windows compatibility.  
  
        (third group:   Makefiles and build scripts.)  
        makefile        -- makefile to compile C files into moalcore.mexmac on PPC.  
        makefile\_intelmac -- makefile for [IntelMac](IntelMac).  
        makefile\_linux    -- makefile for GNU/Linux.  
        makefile\_linuxoctave -- makefile for Linux + Octave.  
        makefile\_windows.m -- makefile for M$-Windows.  
  
    wrap/\*          -- wrapper M-files that check arguments, etc., and  
                       then call to moalcore.mexmac to run [OpenAL](OpenAL) functions  
  
  
The following three commands will completely regenerate moal.  
  
\>\> autocode(1,[],1)     % generate al\_auto.c and wrapper M-files  
\>\> !make                % compile C code to produce MEX files  
\>\> oalconst             % save constants from header files in a .mat file  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSound/MOAL/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSound/MOAL/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSound/MOAL/Contents.m</code>
</div>

{{category}}