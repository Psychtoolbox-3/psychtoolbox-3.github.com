# [IOPort('OpenSerialPort')](IOPort-OpenSerialPort) 
##### [Psychtoolbox](Psychtoolbox)>[IOPort](IOPort).{mex*} subfunction


Open a serial port device, return a 'handle' to it.  
If a port can't be opened, the function will abort with error, unless the level  
of verbosity is set to zero, in which case the function will silently fail, but  
return an invalid (negative) handle to signal the failure to the calling script.  
The optional return argument 'errmsg' contains a text string which is either  
empty on success, or contains a descriptive error message.   
'port' is usually a name string that defines the serial port device to open. On  
MS-Windows this could be, e.g., 'COM1' or 'COM2' etc. On Apple OS/X, it is the  
path to a BSD device file, e.g., '/dev/cu.usbserial-FT3Z95V5' for a  
serial-over-USB device with unique id FT3Z95V5. On GNU/Linux it could be  
'/dev/ttyS0' for the first real serial port, or '/dev/ttyUSB0' for the first  
serial-over-USB device.  
  
The optional string 'configString' is a string with pairs of  
paramName=paramValue tokens, separated by a delimiter, e.g., a space. It allows  
to specify specific values 'paramValue' to specific serial port parameters  
'paramName'. Not all parameters are supported by all operating systems, and all  
settings have reasonable defaults. Settings unknown to a specific operating  
system are ignored.  
The following is a list of (possibly) supported parameters with their defaults:  
  
Lenient -- If this keyword is present, then the driver will carry on on certain  
error conditions instead of aborting. This is sometimes neccessary for some  
special cases like virtual com ports or other non-standard setups.  
  
[BaudRate](BaudRate)=9600 -- The baud transmission rate of the connection. Standard baud  
rates include 110, 300, 600, 1200, 2400, 4800, 9600, 14400, 19200, 38400, 57600,  
115200, 128000 and 256000 bits per second. Not all values may be supported by  
all operating systems and drivers.  
  
Parity=None   -- Type of parity checking: None, Even, Odd.  
  
[DataBits](DataBits)=8    -- Number of data bits per packet: 5,6,7 or 8, on Windows also 16.  
  
[StopBits](StopBits)=1    -- Number of stop bits per packet: 1 or 2.  
  
[FlowControl](FlowControl)=None  -- Type of flow control: None, Hardware (RTS/CTS lines),  
Software (XON/XOFF characters).  
  
[ReceiverEnable](ReceiverEnable)=1 -- A non-zero setting will enable the serial receiver, a zero  
setting will disable the receiver. This setting may not be supported by all  
operating systems and hardware. In such a case, the receiver will always be  
enabled, irrespective of this setting. On MS-Windows, this setting is not  
available at all.  
  
Terminator=os default  -- Type of terminator, given as ASCII character value,  
e.g., 13 for char(13) aka CR or 10 for LF. Currently only used in async read  
mode (see 'StartBackgroundRead' below) if the 'ReadFilterFlags' are set to  
include value 4, or on OS/X and Linux in 'Cooked' processing mode as line  
delimiter. A setting of -1 will try to disable the line terminator.  
  
DTR=os default    -- Setting for 'Data Terminal Ready' pin: 0 or 1.  
  
RTS=os default    -- Setting for 'Request To Send' pin: 0 or 1.  
  
[BreakBehaviour](BreakBehaviour)=Ignore -- Behaviour if a 'Break Condition' is detected on the  
line: Ignore, Flush, Zero. On Windows, this setting is ignored.  
  
[OutputBufferSize](OutputBufferSize)=4096 -- Size of output buffer in bytes.  
  
[InputBufferSize](InputBufferSize)=4096 -- Size of input buffer in bytes. You can't read more than  
that amount per read command.  
  
[HardwareBufferSizes](HardwareBufferSizes)=input,output -- Set size of the hardware driver internal  
input and output buffers in bytes. E.g., [HardwareBufferSizes](HardwareBufferSizes)=32768,8192 would  
set the input buffer to 32768 bytes and the output buffer to 8192 bytes. This  
function is currently only supported on Windows, ignored on other systems. It is  
only a polite hint to the driver, the serial port driver is free to ignore the  
request and choose any buffer sizes or buffering strategy it finds appropriate.  
By default, this parameter is not set by [IOPort](IOPort) and the hardware driver uses  
some built-in reasonable setting.  
  
The following timeout values are inter-byte timeouts. You specify how much time  
reception or transmission of a single byte is allowed to take. Timeout occurs if  
more than that time elapses between send/reception of two consecutive bytes or  
if the total amount of time exceeds the number of bytes, times the interbyte  
timeout value. A value of zero means not to use any timeout, in which case a  
blocking read or write may take forever. If a timeout occurs, the read or write  
operation will be aborted.   
Granularity of timeout settings is 100 msecs on OS/X and Linux, 1 msec on  
Windows, all values are rounded to the closest value matching that granularity.  
The minimal timeout is 100 msecs on OS/X and Linux, about 6 msecs on Windows.  
  
[SendTimeout](SendTimeout)=1.0 -- Interbyte send timeout in seconds. Only used on Windows.  
  
[ReceiveTimeout](ReceiveTimeout)=1.0 -- Interbyte receive timeout in seconds.  
  
[ReceiveLatency](ReceiveLatency) -- Latency in seconds for processing of new input bytes. Only  
used on OS/X and Linux for some devices.  
  
[PollLatency](PollLatency)=0.0005 (0.001 on Windows) -- Latency between polls in seconds for  
polling in some 'Read' operations.  
  
[ProcessingMode](ProcessingMode)=Raw -- Mode of input/output processing: Raw or Cooked. On  
Windows, only Raw (binary) mode is supported.  
  
[DontFlushOnWrite](DontFlushOnWrite)=0 -- Do not flush the serial port write buffer at device close  
time or during blocking writes. This can be set to 1 to work around broken  
serial port drivers, but it may disrupt any kind of timing sensitive algorithms  
that interact with the serial port! Only use if you really know what you're  
doing!  
  
[StartBackgroundRead](StartBackgroundRead)=readGranularity -- Enable asynchronous background read  
operations on the port. A parallel background thread is started which tries to  
fetch 'readGranularity' bytes of data, polling the port every 'PollLatency'  
seconds for at least 'readGranularity' bytes of data. 'InputBufferSize' must be  
an integral multiple of 'readGranularity' for this to work. Later [IOPort](IOPort)('Read')  
commands will pull collected data from the [InputBuffer](InputBuffer) in quanta of at most  
'readGranularity' bytes per invocation. This function is useful for background  
data collection from devices that stream some data at a constant rate. You set  
up background read, let the parallel thread do all data collection in the  
background and collect the data at the end of a session with a sequence of  
[IOPort](IOPort)('Read') calls. This way, data collection doesn't clutter your main  
experiment script.  
  
[BlockingBackgroundRead](BlockingBackgroundRead)=0 -- Perform blocking background reads instead of polling  
reads, if set to 1.  
  
[StopBackgroundRead](StopBackgroundRead) -- Stop running background read operation, discard all  
pending data.  
  
[ReadFilterFlags](ReadFilterFlags)=0 -- Special flags to specify certain post-processing operations  
on read input data.  
\* A setting of 1 will enable special filtering for serial input data from the  
CMU or PST response button boxes.   Redundant data bytes received will be  
discarded - only bytes that are different from their predecessor are stored.    
All read data has a 4-Byte 32 bit count of total bytes read and a 4-Byte count  
of sampling delta in microseconds attached.   You should set 'readGranularity' =  
9 for best effect with the CMU or PST button boxes or compatible devices.   
\* A setting of 2 will filter out CR and LF character codes 10 and 13 from the  
inputstream.  
\* A setting of 4 will implement simple line-buffering for async reads: Read up  
to 'readGranularity' bytes per iteration,   or until 'Terminator' character  
encountered, whatever comes first. Zero-Pad to full 'readGranularity' bytes in  
any case.   Read timestamps in this line-buffered mode correspond to the  
reception of the first byte of a line, not the last one!  
  
  
  


###See also:
'CloseAll'
