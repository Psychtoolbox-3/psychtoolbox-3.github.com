# [Datapixx('WritePropixxTScopePages')](Datapixx-WritePropixxTScopePages) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('WritePropixxTScopePages', pageIndex, pageData);

Download 1 or more T-Scope images to [PROPixx](PROPixx) RAM.  
T-Scope images are 1920 \* 1080 bits = 2,073,600 bits = 259,200 bytes.  
T-Scope images are stored little-endian, so bit 0 of byte 0 controls the  
top-left pixel.  
The maximum number of pages available to T-Scope movies depends on how much RAM  
is available in the [PROPixx](PROPixx).  
Currently the [PROPixx](PROPixx) contains 2GB of RAM.  The top 32MB is reserved, leaving  
2016 MB for the T-Scope.  
T-Scope pages are stored within the [PROPixx](PROPixx) on 256kB boundaries, so a maximum of  
8064 T-Scope pages are available.  
-"pageIndex" indicates the location (in the range 1-8064) where the write should  
start.  
-"pageData" is an unsigned character array with the data to write.  
The size of pageData should be an integer multiple of 259,200 bytes, and  
determines the number of pages to write.  
See [Propixx10kHzTScopeDemo](Propixx10kHzTScopeDemo).m for an example.  
  


###See also:
[EnablePropixxTScope](Datapixx-EnablePropixxTScope), [EnablePropixxTScopePrepRequest](Datapixx-EnablePropixxTScopePrepRequest), [SetPropixxTScopeSchedule](Datapixx-SetPropixxTScopeSchedule), [StartPropixxTScopeSchedule](Datapixx-StartPropixxTScopeSchedule)
