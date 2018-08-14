# [IOPort](IOPort)
##### [Psychtoolbox](Psychtoolbox)>[IOPort](IOPort)

IOPort - A Psychtoolbox driver for general port I/O:  
  
  
General information:  
  
version = IOPort('[Version](IOPort-Version)');  
oldlevel = IOPort('[Verbosity](IOPort-Verbosity)' [,level]);  
  
General commands for all types of input/output ports:  
  
IOPort('[Close](IOPort-Close)', handle);  
IOPort('[CloseAll](IOPort-CloseAll)');  
[nwritten, when, errmsg, prewritetime, postwritetime, lastchecktime] = IOPort('[Write](IOPort-Write)', handle, data [, blocking=1]);  
IOPort('[Flush](IOPort-Flush)', handle);  
[data, when, errmsg] = IOPort('[Read](IOPort-Read)', handle [, blocking=0] [, amount]);  
navailable = IOPort('[BytesAvailable](IOPort-BytesAvailable)', handle);  
IOPort('[Purge](IOPort-Purge)', handle);  
  
Commands specific to serial ports:  
  
[handle, errmsg] = IOPort('[OpenSerialPort](IOPort-OpenSerialPort)', port [, configString]);  
IOPort('[ConfigureSerialPort](IOPort-ConfigureSerialPort)', handle, configString);  
  

  [IOPort](IOPort) is a MEX file for precise control of input/output hardware, e.g.,  
  Serial ports (or emulated serial ports like Serial-over-USB etc.),  
  parallel ports, network ports, and special digital I/O boxes.  
   
  Goal: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
   
  It provides a unified cross-platform interface to such devices and tries  
  to bundle functionality in one MEX file that is common to all those  
  devices, but implemented differently on each of them. An example would be  
  sending of trigger signals: The step to send a trigger signal is always  
  the same. Your code wants to send a trigger signal immediately (with  
  lowest possible delay), at a scheduled point in time, or automatically in  
  response to some event like stimulus onset. However, the mechanism to  
  send triggers is different for different devices. [IOPort](IOPort) tries to provide  
  a unified interface for such cases, so you need to code only once and  
  [IOPort](IOPort) takes care of the nitty gritty differences between different  
  devices in how they send trigger signals.  
   
  So far the theory. The current implementation of [IOPort](IOPort) only provides  
  unified support for accessing the serial ports of your computer. All  
  other functions and device classes will be added in future releases of  
  the driver.  
   
  Usage: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
   
  [IOPort](IOPort) has many functions; type "[IOPort](IOPort)" for a list:  
    [IOPort](IOPort)  
   
  For explanation of any particular [IOPort](IOPort) function, just add a question  
  mark "?". E.g. for 'OpenSerialPort', try either of these equivalent forms:  
    [IOPort](IOPort)('OpenSerialPort?')  
    [IOPort](IOPort) [OpenSerialPort](OpenSerialPort)?  
   
  


