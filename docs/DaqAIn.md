# [DaqAIn](DaqAIn)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

v=[DaqAIn](DaqAIn)[(DeviceIndex]((DeviceIndex),channel,range,[[DoNotCalibrate](DoNotCalibrate)])  
Analog input.  
USB-1208FS:  
"v" is the measured voltage, in Volts, or [NaN](NaN) if no data were received.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
    device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
    of the desired Daq device.  
"channel" (0 to 15) selects any of various single-ended or differential  
    measurements.  
    "channel" Measurement  
     0        0-1 (differential)  
     1        2-3 (differential)  
     2        4-5 (differential)  
     3        6-7 (differential)  
     4        1-0 (differential)  
     5        3-2 (differential)  
     6        5-4 (differential)  
     7        7-6 (differential)  
     8          0 (single-ended)  
     9          1 (single-ended)  
    10          2 (single-ended)  
    11          3 (single-ended)  
    12          4 (single-ended)  
    13          5 (single-ended)  
    14          6 (single-ended)  
    15          7 (single-ended)  
"range" (0 to 7) sets the gain (hence voltage range):  
    for single-ended measurements (channels 8-15), range is always +/- 10 V,  
    and attempts to set ranges other than 0 usually result in saturation, so  
    setting range in this function does not do anything.  For differential  
    measurements (channels 0-7), the map between range as input to this  
    function and the output generated is:  
    0 for Gain 1x (+/-20 V),   1 for Gain 2x (+/-10 V),  
    2 for Gain 4x (+/-5 V),    3 for Gain 5x (+/-4 V),  
    4 for Gain 8x (+/-2.5 V),  5 for Gain 10x (+/-2 V),  
    6 for Gain 16x (+/-1.25 V),  7 for Gain 20x (+/-1 V).  
"[DoNotCalibrate](DoNotCalibrate)" for 1208FS has no effect  
  
USB-1608FS:  
only single-ended inputs are defined, so "channel" is restricted to integers  
from 0 to 7.  Ignore the manual which claims that gains are restricted to only  
four possible values.  Thank the linux people for discovering:  
     0 for Gain 1x (+/- 10 V),      1 for Gain 2x (+/-5 V),  
     2 for Gain 4x (+/- 2.5 V),     3 for Gain 5x (+/- 2 V),  
     4 for Gain 8x (+/- 1.25 V),    5 for Gain 10x (+/- 1V),  
     6 for Gain 16x (+/- 0.625 V),  7 for Gain 32x (+/- 0.3125 V)  
  
"[DoNotCalibrate](DoNotCalibrate)" (0 or 1) if non-zero, function does not use information  
acquired from calibration measurements (see [DaqCalibrateAIn)](DaqCalibrateAIn)).  This should  
probably always be 0 when function is called by a user (hence it defaults to  
0).  Flag was created for the purpose of acquiring calibration data.  
Otherwise subsequent calibration measurements would be fits of fits.  
  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest),  
[DaqDeviceIndex](DaqDeviceIndex), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut), [DaqAIn](DaqAIn), [DaqAOut](DaqAOut), [DaqAInScan](DaqAInScan),[DaqAOutScan](DaqAOutScan).  
  
4/15/05 dgp Wrote it.  
1/21/07 asg changed normalization value from 2^16 to 2^15 to account for 16th bit as a sign bit (not data bit)  
            and modified the "range" value help.  
6/17/07 mk  Add proper sign handling for negative voltages.  
12/2x/07-1/x/08  mpr   modified to work with USB-1608FS and changed some  
                          terminology; particularly did away with "sign" name  
                          conflict ("sign" is a Matlab function)  
6/07/13 mk  Try to make it more robust: Retry on no-date received, proper  
            error handling with error abort on error instead of silent  
            failure returning [NaN](NaN). Cleanup.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqAIn.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqAIn.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqAIn.m</code>
</div>

