# [GetSecs('AllClocks')](GetSecs-AllClocks) 
##### [Psychtoolbox](Psychtoolbox)>[GetSecs](GetSecs).{mex*} subfunction

[GetSecsTime, WallTime, syncErrorSecs, MonotonicTime] = GetSecs('AllClocks' [, maxError=0.000020]);

Return current time in seconds according to all supported clocks.  
  
'GetSecsTime' is the usual [GetSecs](GetSecs)() clock, as returned by [GetSecs](GetSecs)(), in the  
timebase used by all other Psychtoolbox functions, e.g., [Screen](Screen)('[Flip](Flip)') or  
[PsychPortAudio](PsychPortAudio) timestamps.  
  
'WallTime' is real-world system time in an operating system specific timebase.  
This clock is expected to be subject to time adjustments by the system  
administrator or by automated mechanisms like NTP time adjustments. Useful for  
synchronizing clocks across multiple machines on a local network, as it is  
possible for this clock to get automatically corrected for drift.  
On Linux and OSX, the timebase is gettimeofday(), seconds since 1. January 1970  
00:00:00 UTC, with about 1 microsecond precision.  
On MS-Windows the timebase is also UTC time, with about 1 millisecond  
granularity, measuring elapsed seconds since 1. January 1601 00:00:00 UTC via  
the [GetSystemTimeAsFileTime](GetSystemTimeAsFileTime)() function.  
  
'syncErrorSecs' How tightly together did the returned clock times get queried? A  
measure of confidence as to how much all returned times actually denote the same  
point in physical time.  
  
'MonotonicTime' is system monotonic timebase, not subject to administrator or  
NTP time adjustments, with a zero point at operating system boot time. Identical  
to 'GetSecsTime' on Windows and macOS, identical to Posix clock CLOCK\_MONOTONIC  
on GNU/Linux.  
  
The input argument 'maxError' allows to set an allowable upper bound to  
'syncErrorSecs'. The default value is 20 microseconds. The function will try up  
to 10 times to get a result no worse than 'maxError', and output a warning if it  
doesn't manage, e.g., due to some severely overloaded or deficient system.  


###See also:

