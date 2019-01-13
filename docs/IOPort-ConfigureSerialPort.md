# [IOPort('ConfigureSerialPort')](IOPort-ConfigureSerialPort) 
##### [Psychtoolbox](Psychtoolbox)>[IOPort](IOPort).{mex*} subfunction

IOPort('ConfigureSerialPort', handle, configString);

(Re-)Configure a serial port device, specified by 'handle'.  
The string 'configString' is a string with pairs of paramName=paramValue tokens,  
separated by a delimiter, e.g., a space. It allows to specify specific values  
'paramValue' to specific serial port parameters 'paramName'. Not all parameters  
are supported by all operating systems, and all settings have reasonable  
defaults. Settings unknown to a specific operating system are ignored.  
  
See the help of 'OpenSerialPort' for possible settings.  


###See also:
'OpenSerialPort'
