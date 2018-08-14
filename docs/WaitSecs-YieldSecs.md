# [WaitSecs('YieldSecs')](WaitSecs-YieldSecs) 
##### [Psychtoolbox](Psychtoolbox)>[WaitSecs](WaitSecs).{mex*} subfunction


Wait for at least "waitPeriodSecs", don't care if it takes a few milliseconds  
longer. Optionally, return the real wakeup time "realWakeupTimeSecs".  
This call is useful if you want your code to release the cpu for a few  
milliseconds, e.g., to avoid overloading the cpu in a spinning loop, and you  
don't care if the wait takes a few msecs longer than specified. If you do care,  
use one of the other [WaitSecs](WaitSecs)() variants! The other variants emphasize accuracy  
of timed waits, even if this causes a high load on the processor.  
  


###See also:

