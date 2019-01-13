# [Screen('Computer')](Screen-Computer) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

comp=Screen('Computer')

Get information about the computer. The result is a struct holding information  
about your computer. Top-level flags in the returned struct are available on all  
operating systems and identify the operating system: 'macintosh', 'windows',  
'osx', 'linux'. 'system' contains info about the operating system version.  
'gstreamer' tells if [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) support is compiled into [Screen](Screen)(). 'supported'  
tells if the given operating system was supported by the given Psychtoolbox at  
the time of the Psychtoolbox release, ie., if the given system was tested and  
shown to work with the given Psychtoolbox, so there can be some expectation of  
Psychtoolbox working with this system. This doesn't mean that you will get  
support in case of problems though, as support for your system may have ended if  
it isn't a recent enough system. 'MACAddress' may contain the MAC address of  
your ethernet adapter.  
All other fields or additional sub-structures are platform-dependent, so their  
presence can not be relied on.  
SCREEN 'Computer' not longer supports the  obsolete usage:  
[model,owner,system,processor,cache,fpu,hz,busHz,vm,pci,emulating]=SCREEN('Computer')  
  


###See also:

