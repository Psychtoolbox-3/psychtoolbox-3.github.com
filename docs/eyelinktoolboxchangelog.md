# [eyelinktoolboxchangelog](eyelinktoolboxchangelog)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)

    [EyelinkToolbox](EyelinkToolbox).  
    History and list of changes  
  
   February 2024  
   Various improvements and fixes all over the place  
   Updates to [EyelinkBasic](EyelinkBasic)  
       Support for  
           - Static calibration target images from file  
           - Animated calibration targets from media file  
           - Stereomodes supported by [Screen](Screen)()  
   Updates to [EyelinkDemos](EyelinkDemos)/SR-[ResearchDemos](ResearchDemos)/  
       - Deprecated old examples  
       - Added improved examples:  
           - [GazeContingent](GazeContingent)/[FixWindowBufferedSamples](FixWindowBufferedSamples)  
           - [GazeContingent](GazeContingent)/[FixWindowFastSamples](FixWindowFastSamples)  
           - [GazeContingent](GazeContingent)/[GCBufferedEvents](GCBufferedEvents)  
           - [GazeContingent](GazeContingent)/[GCFastSamples](GCFastSamples)  
           - MRI\_BlockRecord  
           - [PursuitTarget](PursuitTarget)  
           - [SimplePicture](SimplePicture)  
           - [SimpleVideo](SimpleVideo)  
  
   July 2010  
   Enabled use of callbacks by default  
   Revampled demos, made to work with new callback version  
   General cleanup  
  
   March 2009  
   Completed access to raw sample structs  
   Added support for LOST\_DATA\_EVENT  
   Added [GetQueuedData](GetQueuedData)  
   Added experimental camera image capture  
  
   Version 2, October 2006  
   Updated Beta version for [OpenGL](OpenGL) Toolbox  
  
   Version 2, June 2006  
   Beta version for [OpenGL](OpenGL) Toolbox  
  
    Version 1.4.5 xx-xx-2003  
  
    fixed small error in setting usemaxwait in geteyelinktime  
  
    Version 1.4.4 27-11-2002  
  
    fixed dummy mode bug in eyelink.dll (was due to an eyelink software incompatability  
    eyelinkeventexample now works on both mac and pc  
    new function in eyelinkoneliners: dummymodedlg  
    is now used in some of the examples to ask to run in dummy mode when no eyelink is connected  
  
    Version 1.4.3 26-11-2002  
  
    Includes eyelink.dll PC beta version  
    PC support added to Eyelink Demo experiment  
    added function dodriftcorrection which implements driftcorrection loop  
   getkeyforeyelink made PC compatible  
    getkeyforeyelinktest, slightly adapted  
  
    known bugs: on PC, there's no communication between operator PC and subject PC during image-mode display  
    eyelinkeventexample does not work on PC  
    On PC no builtin drift correction and trackersetup functions are implemented  
    PC version requires modified getchar.dll!  
    Sounds are not original eyelink sounds.....  
  
    Version 1.4.2 10-11-2002 (local release only)  
    Version 1.4.1 18-10-2002 (local release only)  
  
    dotrackersetup.m: now allows one to go directly into a particular tracker mode  
    this option is not fully tested. Just leave out the 'sendkey' parameter and it will work as it used to.  
    added call to 'getnextdata' in addition to 'getnextdatatype' to conform to the c-routine call  
    button [,time] = Eyelink('lastbuttonpress') now will properly report time if requested  
                                                (previous versions had an erroneous  
                                                time parameter on the right hand side)  
    removed superfluous (non-error) messages from initialization and openfile functions  
    added event types to initeyelinkdefaults (for use with getnextdata)  
    tested with [PsychToolbox](PsychToolbox) 2.5.2 and pre-release screen 2.5.3  
  
    New naming scheme for folder and subfolders, a la [PsychToolbox](PsychToolbox)  
   [EyelinkToolbox](EyelinkToolbox)  
        [EyelinkTests](EyelinkTests)  
        [EyelinkSounds](EyelinkSounds)  
        [EyelinkBasic](EyelinkBasic)  
        [EyelinkDemos](EyelinkDemos)  
        [EyelinkOneLiners](EyelinkOneLiners)  
  
    new functions:  
    time = Eyelink('requesttime')  
    time = Eyelink('readtime')  
  
    result = Eyelink('buttonstates')  
    [result = ]Eyelink('flushkeybuttons'[, enablebuttons = 0])  
    utility function windowsize  
  
    new tests:   
        [EXGetEyeLinkTime](EXGetEyeLinkTime).m  
        testbutton.m  
    changes to demos:  
        eyelinkexample is now identical to the one in the BRMIC paper  
        adapted eyelinkdemo experiment slightly.  
  
    Software used to produce/test the code.    
    Mac OS 9.2.2  
    C-compiler: [CodeWarrior](CodeWarrior) 6.1.  
    Matlab 5.2.1  
    Operator PC: [EyeLink](EyeLink) 2.04  
    [PsychToolbox](PsychToolbox) 2.5.2  
  
  
    Version 1.3.0         25-07-02  
        limited release  
    Version 1.2.0         28-06-01  
  
    Software used to produce/test the code.    
    Mac OS 9.1.  
    C-compiler: [CodeWarrior](CodeWarrior) 6.1.  
    Matlab 5.2.1  
    Operator PC: [EyeLink](EyeLink) 2.04  
    [PsychToolbox](PsychToolbox) 2.44  
%   updated on-line documentation  
    added a few test programs provided by John Palmer  
    added [SimpleStepExperiment](SimpleStepExperiment) by John Palmer to the demo's  
    Reorganised demo-experiments  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/eyelinktoolboxchangelog.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/eyelinktoolboxchangelog.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/eyelinktoolboxchangelog.m</code>
</div>

