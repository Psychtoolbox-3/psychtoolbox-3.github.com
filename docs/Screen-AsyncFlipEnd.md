# [Screen('AsyncFlipEnd')](Screen-AsyncFlipEnd) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Wait for completion of a previously scheduled asynchronous flip operation (see  
[Screen](Screen) [AsyncFlipBegin](AsyncFlipBegin)? for help).  
This command will wait for completion on onscreen window "windowPtr", then  
return the result of the operation, ie. all the stimulus onset timestamps and  
other diagnostic information. See help for [Screen](Screen) [Flip](Flip)? for explanation of the  
returned info. If you call this function without having called 'AsyncFlipBegin'  
before, it will return immediately with the results of the last completed flip,  
regardless if it was a synchronous [Screen](Screen)('[Flip](Flip)') or an asynchronous flip long  
finished ago.  
[Screen](Screen)('AsyncFlipCheckEnd') provides a non-blocking, polling version of this  
command -- one that doesn't pause if the referenced operation hasn't completed  
yet.  


###See also:
[DrawingFinished](Screen-DrawingFinished) [WaitUntilAsyncFlipCertain](Screen-WaitUntilAsyncFlipCertain) [AsyncFlipBegin](Screen-AsyncFlipBegin) [AsyncFlipCheckEnd](Screen-AsyncFlipCheckEnd) [AsyncFlipEnd](Screen-AsyncFlipEnd) Flip
