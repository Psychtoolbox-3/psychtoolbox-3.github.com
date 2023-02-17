# [ColorCal2](ColorCal2)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[ColorCal2](ColorCal2)

varargout = [ColorCal2](ColorCal2)(command, [varargin])  
  
Description:  
Interface function to communicate with the [ColorCal2](ColorCal2) USB device.  
  
  
WINDOWS: On MS-Windows this driver needs to use a virtual COM port method  
to communicate, instead of the more feature-rich USB method on Linux or  
OSX. As a consequence, only a subset of functions is supported, as listed  
below, and device detection may be less reliable if you have other serial  
port devices or virtual COM port devices connected, unless you help the  
driver by telling it the right COM port: The device will show up as an  
additional serial port on the system. This driver will communicate with  
the device by establishing a serial port connection via that serial port.  
The driver will check for the existence of a configuration file named  
[[PsychtoolboxConfigDir](PsychtoolboxConfigDir) 'ColorCal2Config.txt']. If the file exists and is  
readable, then presence of a serial port name in the first line of that  
text configuration file will use the serial port with that name for  
communication, otherwise the driver will try to auto-detect the proper  
serial port for communication. E.g., if the file would contain one line  
with the text COM3 then virtual COM port 3 would be used for serial port  
communication.  
  
  
macOS: macOS 10.12 or later is required for this function to work. For  
older macOS versions, look for instructions on the CRS Ltd. website.  
Access to all [ColorCal2](ColorCal2) functionality needs a 3rd party libusb-1.0.dylib  
installed - seee 'help PsychHID'. Without that, the same serial port  
method is used as on MS-Windows, with a bit more limited functionality.  
  
  
LINUX: If you want to use this function without the need to run Matlab or  
Octave as root user (i.e., without need for root login or the sudo  
command), please run [PsychLinuxConfiguration](PsychLinuxConfiguration) once (this will happen  
automatically if you install, update or setup Psychtoolbox via  
[DownloadPsychtoolbox](DownloadPsychtoolbox), [UpdatePsychtoolbox](UpdatePsychtoolbox) or [SetupPsychtoolbox)](SetupPsychtoolbox)), or  
alternatively copy the file  
Psychtoolbox/[PsychHardware](PsychHardware)/[ColorCal2](ColorCal2)/60-cambridgeresearch-permissions.rules  
into the folder /etc/udev/rules.d/ on your system. This one-time copy  
will require administrator privileges, but after that, any user should be  
able to use the [ColorCal](ColorCal) devices or other CRS Ltd. devices without  
special permissions.  
  
  
Required Input:  
command (string) - Command to send to the [ColorCal2](ColorCal2) device. Commands are  
                   case insensitive.  
  
Optional Input:  
varargin - Argument(s) required for a subset of the [ColorCal2](ColorCal2)  
           commands. Varies depending on the command.  
  
Optional Output:  
varargout - Value(s) returned for a subset of the [ColorCal2](ColorCal2) commands.  
  
### Command List for all operating systems:  
  
'DeviceInfo' - Retrieves the following device information in a struct:  
     firmware version number, 8 digit serial number, and firmware build  
     number. The struct's fields are romVersion, serialNumber,  
     buildNumber.  
  
     Example:  
     devInfo = [ColorCal2](ColorCal2)('DeviceInfo');  
  
'MeasureXYZ' - Measures the tri-stimulus value of the current light.  
     Returns a struct with x, y, and z in floating point format.  These  
     values should be corrected by multiplying them against the calibration  
     matrix typically stored in the 1st calibration matrix in the device.  
  
     Example: Retrieve the xyz values and correct them with the 1st  
              calibration matrix.  
     cMatrix = [ColorCal2](ColorCal2)('ReadColorMatrix');  
     s = [ColorCal2](ColorCal2)('MeasureXYZ');  
     correctedValues = cMatrix(1:3,:) \* [s.x s.y s.z]';  
  
'ReadColorMatrix' or 'ReadColourMatrix' - Retrieves all 3 color  
     calibration matrices from the device and returns them as a 9x3 matrix.  
     Each set of 3 rows represents a single calibration matrix.  All  
     values will be in floating point format.  
  
'ZeroCalibration' - Removes small zero errors in the electronic system of  
     the [ColorCal2](ColorCal2) device.  It reads the current light level and stores  
     the readings in a zero correction array.  All subsequent light  
     readings have this value subtracted from them before being returned.  
     This command is intended to be issued when the [ColorCal2](ColorCal2) is in the  
     dark.  Returns 1 if the command succeeds, 0 if it fails.  This  
     command must be run after every power cycle of the device.  
  
'NeedZeroCalibration' - Returns true if a zero calibration is needed, false  
     otherwise. Devices with firmware build 877 or later do not need this, as  
     they are factory calibrated.  
  
'[Close](Close)' - [Close](Close) connection to device. A 'clear all' or 'clear ColorCal2' or  
     quitting Octave or Matlab will also close the connection, so this is  
     not strictly needed.  
  
All the following commands are not supported on MS-Windows, only on Linux  
and macOS, and on macOS they need a 3rd party installed libusb-1.0.dylib  
(see 'help PsychHID'):  
  
  
'GetRawData' - Returns the raw data for all three light channels, the  
     contents of the zero correction array for all three channels, and  
     the current reading of the trigger ADC.  Returns a single struct  
     containing the following fields: Xdata, Xzero, Ydata, Yzero, Zdata,  
     Zzero, Trigger.  All values are unformatted.  
  
'LEDOn' - Turns the LED on.  
  
'LEDOff' - Turns the LED off.  
  
'SetLEDFunction' - Controls whether the LED is illuminated when the  
     trigger signal is generated.  This state is stored in non-volatile  
     memory and will survive a power cycle.  Takes 1 additional argument:  
     0 or 1.  0 = LED not active when triggered, 1 = LED active when  
     triggered.  
  
'SetTriggerThreshold' - Sets the threshold which must be exceeded by the  
     first derivative of the trigger ADC before a trigger pulse is  
     generated.  It is stored in non-volatile memory and will survive a  
     power cycle.  Takes 1 additional argument which is the trigger  
     threshold value.  
  
'StartBootloader' - Causes the [ColorCal2](ColorCal2) to start its internal bootloader  
     in preparation for a firmware upgrade.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/ColorCal2/ColorCal2.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/ColorCal2/ColorCal2.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/ColorCal2/ColorCal2.m</code>
</div>

