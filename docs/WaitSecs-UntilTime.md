# [WaitSecs('UntilTime')](WaitSecs-UntilTime) 
##### [Psychtoolbox](Psychtoolbox)>[WaitSecs](WaitSecs).{mex*} subfunction


Wait until at least system time "whenSecs" has been reached. Optionally, return  
the real wakeup time "realWakeupTimeSecs".  
This allows conveniently waiting until an absolute point in time has been  
reached, or to allow drift-free waiting for a well defined interval, more  
accurate than the standard [WaitSecs](WaitSecs)() call.  
Example:  
Wait until 0.6 secs after last stimulus onset, if vbl=[Screen](Screen)('[Flip](Flip)', window);  
was the onset timestamp vbl from a previous flip:  
realwakeup = [WaitSecs](WaitSecs)('UntilTime', vbl + 0.6);  
  
In a perfect world, realwakeup == vbl + 0.6, in reality it will be  
realwakeup == vbl + 0.6 + randomjitter; with randomjitter being the hopefully  
small scheduling delay of your operating system. If the delay is high or varies  
a lot between trials then your system has noisy timing or real timing problems.  
  


###See also:

