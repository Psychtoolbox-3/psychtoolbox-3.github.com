# [DaqWriteCode](DaqWriteCode)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

err=[DaqWriteCode](DaqWriteCode)[(DeviceIndex]((DeviceIndex),address,data)  
USB-1208FS: Write program memory. This command writes to the program  
memory in the device.  This command is not accepted unless the device is  
in update mode (see [PrepareDownload)](PrepareDownload)).  The [WriteCode](WriteCode) command will  
normally be used when downloading a new hex file, so it supports the  
memory ranges that may be found in the hex file.  
The address ranges are:  
0x000000 - 0x007AFF: FLASH program memory  
0x200000 - 0x200007: ID memory (serial number is stored here)  
0x300000 - 0x30000F: CONFIG memory (processor configuration data)  
0xF00000 - 0xF03FFF: EEPROM memory  
When writing to FLASH program memory, length(data) must be 32 and the  
device must receive data in successive 32-byte chunks starting on a  
64-byte boundary. When writing to other kinds of memory, length(data) can  
be any number of bytes up to the maximum (32).  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
      of the desired USB-1208FS box.  
"address" is the 24-bit start address for the write.  
"data" is a vector with length up to 32, one element per byte.  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  
  
4/15/05 dgp Wrote it.  
12/2x/07  mpr tested it and found it wanting  
1/11/08   mpr   swept through attempting to improve consistency across  
                  daq functions  
  
I have no current plans to make sure this code works, but on 1/8/08 I  
discovered it might work as is...  According to a comment in the source files  
written by the linux people, this function doesn't actually cause the program  
memory to be written.  It puts an image of the code in external SRAM, and a  
subsequent call to [UpdateCode](UpdateCode) must be made to write the program into the  
device's flash memory.  The command code for the [UpdateCode](UpdateCode) command is 84,  
which Denis did not list for the 1208FS.  I have not looked to see if that is  
a difference between the 1208 and 1608 or if this was just something Denis  
never discovered because he didn't look for it.  Anyways, I have no current  
plans to create a [PsychHID](PsychHID) wrapper for the [UpdateCode](UpdateCode) command, so if this  
functionality is something you want, then that's what you'll probably need to  
do to get things working.  And if you do that, you probably want to invest   
some time in figuring out the [ReadChecksum](ReadChecksum) (command code 82) for verification   
that program memory is correct. -- mpr  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqWriteCode.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqWriteCode.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqWriteCode.m</code>
</div>

