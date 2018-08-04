# [PsychBasic](PsychBasic)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

  
Psychtoolbox:[PsychBasic](PsychBasic)  
Psychtoolbox:[PsychBeta](PsychBeta):[PsychBasic](PsychBasic)  
  
  
  [Beeper](Beeper)               - Play a nice beep tone of selectable duration, frequency and volume.  
  [CharAvail](CharAvail)            - Is a keypress available for [GetChar](GetChar)?         
  [DisableKeysForKbCheck](DisableKeysForKbCheck) - Tell [KbCheck](KbCheck) and [KbWait](KbWait) to ignore specific keys.  
  [DoNothing](DoNothing)            - Does nothing. Used to time Matlab's overhead.  
  [DrawFormattedText](DrawFormattedText)    - Drawing of formatted text into windows.  
  [DrawFormattedText2](DrawFormattedText2)   - Drawing of formatted text into windows, with more formatting options.  
  [FlushEvents](FlushEvents)          - Flush any unprocessed events.   
  [FontInfo](FontInfo)             - Return a struct array describing installed fonts.  
  [Gestalt](Gestalt)              - Query system configuration on OS 9 and OS X.   
  [GetBusTicks](GetBusTicks)          - Number of system bus ticks since startup.  
  [GetBusTicksTick](GetBusTicksTick)      - Duration of one tick of the [GetBusTicks](GetBusTicks) clock.  
  [GetChar](GetChar)              - Wait for keyboard character and return it.  
  [GetPID](GetPID)               - Get the process ID of the MATLAB process.  
  [GetMouse](GetMouse)             - Get mouse position.   
  [GetMouseWheel](GetMouseWheel)        - Get mouse wheel position delta on a wheel mouse.  
  [GetSecs](GetSecs)              - Time since startup with high precision.   
  [GetSecsTick](GetSecsTick)          - Duration of one tick of the [GetSecs](GetSecs) clock.  
  [GetTicks](GetTicks)             - Number of 60.15 Hz ticks since startup.   
  [GetTicksTick](GetTicksTick)         - Duration of one tick of the [GetTicks](GetTicks) clock.  
  [HideCursor](HideCursor)           - Hide cursor.  
  [IOPort](IOPort)               - A I/O driver for access to serial ports.  
  [KbCheck](KbCheck)              - Get instantaneous keyboard state.  
  [KbEventAvail](KbEventAvail)         - Return number of pending keyboard events in ringbuffer.  
  [KbEventFlush](KbEventFlush)         - Remove all pending keyboard events in ringbuffer.  
  [KbEventGet](KbEventGet)           - Get oldest pending keyboard event in ringbuffer.  
  [KbKeysAction](KbKeysAction)         - Return an incremented or decremented value, depending on keys pressed.  
  [KbName](KbName)               - Convert keycode to key name and vice versa.  
  [KbPressWait](KbPressWait)          - Wait for key press, make sure no keys pressed before.  
  [KbQueueCreate](KbQueueCreate)        - Create keyboard queue.  
  [KbQueueRelease](KbQueueRelease)       - Destroy keyboard queue.  
  [KbQueueFlush](KbQueueFlush)         - Empty keyboard queue.  
  [KbQueueStart](KbQueueStart)         - Start recording of key presses into queue.  
  [KbQueueStop](KbQueueStop)          - Stop recording of key presses into queue.  
  [KbQueueCheck](KbQueueCheck)         - Check keyboard queue for key presses/releases.  
  [KbReleaseWait](KbReleaseWait)        - Wait until all keys on keyboard are released.  
  [KbStrokeWait](KbStrokeWait)         - Wait for single, isolated key stroke.  
  [KbTriggerWait](KbTriggerWait)        - Wait for trigger keys on keyboard.  
  [KbWait](KbWait)               - Wait until at least one key is pressed and return its time.  
  [ListenChar](ListenChar)           - Start [GetChar](GetChar) queue.  
  [LoadPsychHID](LoadPsychHID)         - Helper function for loading [PsychHID](PsychHID) on MS-Windows.  
  [MachAbsoluteTimeClockFrequency](MachAbsoluteTimeClockFrequency) - Mach Kernel time measurement.    
  [PredictVisualOnsetForTime](PredictVisualOnsetForTime) - Predict stimulus onset for given [Screen](Screen)('[Flip](Flip)') 'when' timespec.  
  [psychassert](psychassert)          - Drop in replacement for Matlabs assert().  
  [psychlasterror](psychlasterror)       - Drop in replacement for Matlabs lasterror().  
  [psychrethrow](psychrethrow)         - Drop in replacement for Matlabs rethrow().  
  [PsychCV](PsychCV)              - Miscellaneous C routines for computer vision and related stuff.  
  [PsychDrawSprites2D](PsychDrawSprites2D)   - Fast drawing of many 2D sprite textures.  
  [PsychKinect](PsychKinect)          - Psychtoolbox driver for the Microsoft XBOX-360 Kinect.  
  [PsychtoolboxDate](PsychtoolboxDate)     - Current version date, e.g. '1 August 1998'  
  [PsychtoolboxVersion](PsychtoolboxVersion)  - Current version number, e.g. 2.32  
  [PsychWatchDog](PsychWatchDog)        - Watchdog mechanism and error handler for Psychtoolbox.  
  [PsychTweak](PsychTweak)           - Tweak Psychtoolbox low-level operating parameters.  
  [RemapMouse](RemapMouse)           - Map mouse position to stimulus position.  
  [RestrictKeysForKbCheck](RestrictKeysForKbCheck) - Restrict operation of [KbCheck](KbCheck) et al. to a subset of keys on the keyboard.  
  [Screen](Screen)               - Control the video display. \*\* Type "[Screen](Screen)" for a list. \*\*   
  [SetMouse](SetMouse)             - Set mouse position.  
  [ShowCursor](ShowCursor)           - Show the cursor, and set cursor type.  
  [Snd](Snd)                  - Play sounds.  
  [TouchEventAvail](TouchEventAvail)      - Return count of available (queued) touch events in a touch queue.  
  [TouchEventFlush](TouchEventFlush)      - Delete all queued events from a touch queue.  
  [TouchEventGet](TouchEventGet)        - Retrieve oldest touch event from a touch queue.  
  [TouchQueueCreate](TouchQueueCreate)     - Create an event queue for reception of touch input.  
  [TouchQueueRelease](TouchQueueRelease)    - Release an event queue for touch input, once no longer needed.  
  [TouchQueueStart](TouchQueueStart)      - Start touch recording on a touch queue.  
  [TouchQueueStop](TouchQueueStop)       - Stop touch recording on a touch queue.  
  [VideoRefreshFromMeasurement](VideoRefreshFromMeasurement) - Alternative calibration procedure to find exact video refresh interval.  
  [WaitSecs](WaitSecs)             - Wait specified time.  
  [WaitTicks](WaitTicks)            - Wait specified number of 60.15 Hz ticks.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/Contents.m</code>
</div>

{{category}}