# [MachAbsoluteTimeClockFrequency](MachAbsoluteTimeClockFrequency)
##### [Psychtoolbox](Psychtoolbox)>[MachAbsoluteTimeClockFrequency](MachAbsoluteTimeClockFrequency)

  

  timebaseFrequencyHz = [MachAbsoluteTimeClockFrequency](MachAbsoluteTimeClockFrequency)  
   
  OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
   
  Return the frequency of the Mach Kernel "absolute timebase clock".  The  
  frequency depends your  hardware, both the model of CPU and a system  
  hardware clock.  
    
  Mach Kernel functions which assign real-time "Time constraint priority"  
  status to threads give parameters in Mach time base units. The counter which  
  clocks time allocated to your thread counts time in these units.  Use the  
  absolute timebase clock frequency returned by [MachAbsoluteTimeClockFrequency](MachAbsoluteTimeClockFrequency) to convert  
  seconds into absolute timebase units which you pass to functions which  
  set which set priority:  
    
    time\_interval\_in\_mach\_units=   
         time\_interval\_in\_seconds \* timebaseFrequencyHz;  
   
  For more information on the Mach absolute time clock see Apple Technical  
  Q&A 1398:  
   
   http://developer.apple.com/qa/qa2004/qa1398.html  
   
  OS 9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
   
  [MachAbsoluteTimeClockFrequency](MachAbsoluteTimeClockFrequency) is not provided on OS 9 because the Mach  
  time base is a feature of only the OS X Mach Kernel.    
   
   
  WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
    
  [MachAbsoluteTimeClockFrequency](MachAbsoluteTimeClockFrequency) is not provided on Windows because the  
  Mach time base is a feature of only the OS X Mach Kernel.     
  \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
   
  see also: [Priority](Priority)  
  


