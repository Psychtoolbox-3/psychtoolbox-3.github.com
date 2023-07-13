# [DaqAInScan](DaqAInScan)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

[data,params]=[DaqAInScan](DaqAInScan)[(DeviceIndex]((DeviceIndex),options)  
  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
\*                                                                          \*  
\* For USB-1608FS, make sure you look at the bottom of this help as there   \*  
\* are significant differences between the function of that device and of   \*  
\* the USB-1208FS.  "channel" means something a bit different, and the      \*  
\* recommendation for that device is oppostite of that for the USB-1208FS   \*  
\* with respect to using options.[FIrstchannel](FIrstchannel) and options.Lastchannel.  The \*  
\* differences indicating need for that change in recommendation are        \*  
\* unfortunate as the two different methods for choosing which channels to  \*  
\* scan were the most confusing things in this function.  But the           \*  
\* USB-1208FS can be told to select particular channels by utilizing the    \*  
\* gain queue, and the USB-1608FS does not allow that behavior.  See the    \*  
\* help for [DaqALoadQueue](DaqALoadQueue) for more insight.  -- mpr                         \*  
\*                                                                          \*  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
  
USB-1208FS: Analog input scan. Clocked analog to digital conversion. This  
command samples several analog input channels at a specified rate and  
sends the readings to the host. Use [DaqAInScan](DaqAInScan) when you want to complete  
the whole operation in one call, tying up the computer until the sampling  
is done. Use [DaqAInScanBegin](DaqAInScanBegin), [DaqAInScanContinue](DaqAInScanContinue), and [DaqAInScanEnd](DaqAInScanEnd),  
instead, when you want to use the computer during sampling.  
  
USE CHANNEL AND RANGE: You can specify the channels to be scanned in two  
different ways, "[FirstChannel](FirstChannel)" and "[LastChannel](LastChannel)", or as an arbitrary  
"channel" list. We recommend the latter because it's much more general.  
With "channel" you also provide a corresponding list of the desired gain  
"range". If you use [FirstChannel](FirstChannel) and [LastChannel](LastChannel), then the sampling will  
use the existing gains that were last set on those channels (by [AIn](AIn) or  
[ALoadQueue)](ALoadQueue)). However, [DaqAInScan](DaqAInScan) doesn't know what that gain range was,  
so it arbitrarily assumes a gain range of 3 in computing the scale factor  
to convert your readings into voltages. Thus every reason recommends that  
you supply channel and range when you call [DaqAInScan](DaqAInScan).  
  
"data" is an [NxM](NxM) matrix, with one column per channel. Each reading is a  
    double, based on a 16-bit value in the report. In the USB-1208FS  
    only the upper 12 of those 16 bits are significant.  
"params.fActual" is the actual sampling frequency, sample/channel/s. It  
    is as close as possible to the requested sampling frequency  
    options.f.  
"params.times" is the times [(GetSecs)]((GetSecs)) of receipt by [PsychHID](PsychHID) of the  
    reports in data.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
    device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
    of the desired USB-1208FS box.  
"options.channel" is a vector of length 1 to 8. Each value (0 to 15)  
    selects any of various single-ended or differential measurements  
    using the eight digitizers. By default, [DaqAInScan](DaqAInScan) sends this for you  
    to the device by calling [DaqALoadQueue](DaqALoadQueue) before issuing the [AInScan](AInScan)  
    command.  
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
  
"options.range" is a vector of the same length as options.channel, with  
    values of 0 to 7, specifying the desired gain (and voltage range) for  
    the corresponding channel. By default, [DaqAInScan](DaqAInScan) sends this for you  
    to the device by calling [DaqALoadQueue](DaqALoadQueue) before issuing the [AInScan](AInScan)  
    command. When options.range is not specified [DaqAInScan](DaqAInScan) assumes a  
    value of 3 in computing the scale factor applied to the results to  
    convert them into volts unless you are making a single-ended measurement.  
    For single-ended measures, the range is always +/- 10 V, so if you pass a  
    channel higher than 7, any range values you pass for that channel will be  
    ignored.  
  
    0 for Gain 1x (+-20 V),     1 for Gain 2x (+-10 V),  
    2 for Gain 4x (+-5 V),      3 for Gain 5x (+-4 V),  
    4 for Gain 8x (+-2.5 V),    5 for Gain 10x (+-2 V),  
    6 for Gain 16x (+-1.25 V),  7 for Gain 20x (+-1 V).  
  
"options.[FirstChannel](FirstChannel)" (0 to 15) is the first channel of the scan. NOT  
    RECOMMENDED; use options.channel instead. If you specify [FirstChannel](FirstChannel)  
    and [LastChannel](LastChannel) then don't specify channel and range, above.  (formerly  
    "options.lowChannel" -- that terminology is deprecated.)  
"options.[LastChannel](LastChannel)" (0 to 15) is the last channel of the scan. The  
    values [FirstChannel](FirstChannel) and [LastChannel](LastChannel) specify the channel range for the  
    scan. If [FirstChannel](FirstChannel) is greater than [LastChannel](LastChannel), the scan will wrap  
    (i.e. if [FirstChannel](FirstChannel) is 14 and [LastChannel](LastChannel) is 1, the scan will include  
    channels 14, 15, 0, and 1.) NOT RECOMMENDED; use options.channel  
    instead. If you specify [FirstChannel](FirstChannel) and [LastChannel](LastChannel) then don't specify  
    channel and range, above. (formerly "options.highChannel" -- that  
    terminology is deprecated.)  
"options.count" is the desired number of samples per channel, either in  
    the 32-bit range 1 to 4e+09, or INF. The value INF invokes the  
    USB-1208FS's continuous data collection mode, which runs indefinitely.  
"options.[ReleaseTime](ReleaseTime)" effective only when options.continue (see below) is set  
    to 1 and options.count is Inf.  Setting options.[ReleaseTime](ReleaseTime) to some  
    reasonable time in the future and then calling [DaqAInScanContinue](DaqAInScanContinue) will  
    allow data to be offloaded from the device's FIFO.  If you select the  
    option appropriately and call [DaqAInScanContinue](DaqAInScanContinue) frequently enough, you  
    will not lose data.  Otherwise the FIFO fills, and you get jack diddly  
    squat.  
"options.f" is desired sampling frequency, sample/channel/s, in the range  
    0.596/c to 10e6/c Hz, where c is the number of channels being  
    scanned.  
"options.immediate" is 1 = immediate-transfer mode, 0 (default) =  
    block-transfer mode. At low sampling rates, immediate-transfer mode  
    will reduce the delay in receiving the sampled data. In  
    immediate-transfer mode, each 16-bit sample is sent immediately (a  
    2-byte report), rather than waiting for the buffer to fill (62  
    bytes). This mode should not be used if the aggregate sampling rate  
    is greater than 2,000 samples per second in order to avoid data loss.  
    The difference between the two modes will be more apparent if you  
    enable options.print, allowing you to see that you get one-sample  
    reports (2 bytes) in immediate mode, and less-frequent 31-sample  
    reports (62 bytes) in block-transfer mode.  
"options.trigger" is 1 = use external trigger; 0 (default).  
    The external trigger may be used to start data collection  
    synchronously. If the bit is set, the device will wait until the  
    appropriate trigger edge is detected, then begin sampling data at  
    the specified rate.  No messages will be sent until the trigger is  
    detected.  
"options.retrigger" is 1 = retrigger mode, 0 (default) = normal trigger.  
    The retrigger mode option is only used if trigger is used.  This  
    option will cause the trigger to be rearmed after options.count  
    samples are acquired if in continuous mode.  
"options.sendChannelRange is 1 (default) to ask that the options.channel  
    and options.range lists (if provided) be sent to the device by  
    calling [DaqALoadQueue](DaqALoadQueue) before the sending the [AInScan](AInScan) command, or 0 to  
    not send them. Since those lists persist in the device you can save  
    time by skipping this transmission after you've already sent them  
    once (either through [DaqAinScan](DaqAinScan) or by explicitly calling  
    [DaqALoadQueue](DaqALoadQueue) yourself). Even if you set this option to 0 you should  
    still supply the options.channel and options.range arguments to  
    [DaqAInScan](DaqAInScan) because it needs to know how many channels you are using  
    in order to set up the count and frequency parameters in the [AInScan](AInScan)  
    command to the USB-1208FS. This default is 0 if you supply  
    [FirstChannel](FirstChannel) and [LastChannel](LastChannel).  
"options.queue" is 1 = use channel gain queue (i.e. "channel" and  
    "range"), 0 = use options.[FirstChannel](FirstChannel) and options.[LastChannel](LastChannel)  
    arguments. Don't bother setting this. It will be set for you, based  
    on which parameters you provide.  
"options.print" is 1 = enable diagnostic printing of the reports; 0  
    (default) no diagnostics.  
"options.begin" is 1 (default) to begin a new scan.  
"options.continue" is 1 (default) to receive reports (inside [PsychHID)](PsychHID)).  
"options.end" is 1 (default) to wait until done and return the result.  
"options.nodiscard" is an optional field. If 1 (true) then the check for  
     consecutively numbered reports is skipped. No data is discarded.  
  
LIMITATION: The literature from Measurement Computing mentions a speed of  
50 kHz, but that's a theoretical limit. As of 17 April 2005, [DaqAInScan](DaqAInScan)  
achieves 2000/c sample/channel/s, where c is the number of channels being  
sampled.  
  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest),  
[DaqAInScanBegin](DaqAInScanBegin), [DaqAInScanContinue](DaqAInScanContinue), [DaqAInScanEnd](DaqAInScanEnd),  
[DaqDeviceIndex](DaqDeviceIndex), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut), [DaqAIn](DaqAIn), [DaqAOut](DaqAOut), [DaqAInScan](DaqAInScan),[DaqAOutScan](DaqAOutScan).  
  
In some ways the USB-1608FS is less functional than the 1208FS.  For instance,  
where the 1208FS allows you to sample from the different channels in arbitrary  
order, the 1608FS only allows you to sample from sequential channels.  Hence,  
I think the only way to get this function to wrap for the 1608FS would be if  
you sampled from \*all\* channels and threw away the data not requested by the  
user.  Since that would entail a potentially mystifying performance hit, I  
instead opt to tell user that they cannot set [FirstChannel](FirstChannel) higher than  
[LastChannel](LastChannel).  What follows are other differences in options...  If an option  
is not specified below, then it behaves the same for the 1608FS as for the  
1208FS.  
  
"options.channel" will be ignored (though you will get a warning).  Do \*NOT\*  
    even consider using this method with a 1608FS as it would be too confusing  
    to try to set this up... you could not poll an arbitrary sequence, and if  
    you want non-consecutive channels... see previous paragraph.  
  
"options.range" if specified, is either a scalar or a vector that must be of  
    the same length as the vector: options.[FirstChannel](FirstChannel):options.[LastChannel](LastChannel).  
    Values must be in the set 0:7, specifying the desired gain (and hence  
    voltage range) for the corresponding channel as in the 1208FS except that  
    the mapping differs.  For the USB-1608FS, the values mean:  
  
    0 for Gain 1x (+/- 10 V),     1 for Gain 2x (+/- 5 V),  
    2 for Gain 4x (+/- 2.5 V),    3 for Gain 5x (+/- 2 V),  
    4 for Gain 8x (+/- 1.25 V),   5 for Gain 10x (+/- 1 V),  
    6 for Gain 16x (+/- 0.625 V), 7 for Gain 32x (+/- 0.3125 V)  
  
If options.range is passed, this function will call [DaqALoadQueue](DaqALoadQueue) for you.  If  
it is not, then it is assumed you do not wish to change the gains, and that  
function is not called.  Since we cannot read the gains, a preferences file  
will be created or edited for you when you call [DaqALoadQueue](DaqALoadQueue).  
  
"options.[FirstChannel](FirstChannel)" (0 to 7) is the first channel of the scan.  If you do not  
    pass this option, it is assumed to be 0.  
"options.[LastChannel](LastChannel)" (options.Firstchannel to 7) is the last channel of the  
    scan.  If you do not specify this option, it is assumed you want only to  
    sample from options.Firstchannel.  
"options.retrigger" is apparently not an option for the 1608FS.  I could be  
    wrong about whether it \*could\* be an option: there is a potential option  
    called "external sync", and that might be the same as retrigger.  However,  
    even if that is correct, I have not implemented it.  (see note below on  
    numerical definitions of options)  
"options.queue" again, not an option.  Don't try to use it.  
  
These options do not exist (as such) for the 1208FS.  They all default to 0.  
  
"options.burst" if 1, acquire data in burst mode.  It is not clear to me what  
    differences are entailed by setting this to 1 compared to just setting  
    "options.immediate" to 1, but if nothing else, data from multiple channels  
    can be acquired faster; I've not tested it, but it may be that in burst  
    mode the device acquires data until its FIFO is full and may ignore  
    efforts to communicate with it until that occurs.  
"options.[ExternSync](ExternSync)" if 1, use external sync signal.  I believe this is mainly  
    for using to daqs to acquire data simultaneously.  Connect the sync  
    terminals of the two devices, configure one to output a sync signal and  
    set this option to 1 so that this device listens for that sync signal and  
    times its data acquisition accordingly.  
"options.debug" I have no idea what this does... "debug" doesn't even appear  
    in the user manual for the device.  
  
To use this function, you don't need the following information.  However, if  
you want to modify it, this information may prove useful to you.  The options  
that are passed through [PsychHID](PsychHID) are combined into a single 8-bit number.  The  
settings for the bits (that I know of) for the 1208FS are:  
   1 (0x1) Execution Mode (1=counted, 0=continuous)  
   2 (0x2) Transfer mode (1=immediate, 0=blocked)  
   3 (0x4) Trigger mode (1=external, 0=internal)  
   5 (0x10) Gain Queue mode (1=use stored queue, 0=use channels passed)  
   6 (0x20) Retrigger mode (1=reset trigger, 0=don't)  
  
and for the 1608FS:  
   1 (0x1) Execution Mode (1=counted, 0=continuous)  
   2 (0x2) Burst Mode (1=burst I/O, 0=normal I/O)  
   3 (0x4) Transfer mode (1=immediate, 0=blocked)  
   4 (0x8) Trigger mode (1=external, 0=internal)  
   5 (0x10) External sync (1=use external, 0=don't); as noted above, this may  
             be the same as retrigger mode  
   6 (0x20) Debug mode (1=debug, 0=non-debug) (I don't know what this does)  
  
4/15/05 dgp Wrote it.  
4/15/05 dgp Merged several of the arguments into the "options" struct.  
4/25/05 dgp Added options.channel, options.range, and options.sendChannelRange.  
4/27/05 dgp Fixed immediate-transfer mode once I realized that the report  
            contains only one sample, not one sample per channel.  
8/26/05 dgp Fixed bug in extraction of serial number, as suggested by Steve  
            Van Hooser, vanhooser@neuro.duke.edu  
8/26/05 dgp Incorporated bug fix for compatibility with Mac OS X Tiger  
            suggested by Maria Mckinley <parody@u.washington.edu\>. The reported  
            number of outputs of the USB-1208FS has changed in Tiger.  
            http://groups.yahoo.com/group/psychtoolbox/message/3614  
1/02/07 mk  Add 'persistent dinc' to line 245. This apparently fixes some  
            bug, bugfix proposed by Florian Stendel.  
1/x/08  mpr modified for use of USB-1608FS, added options.[ReleaseTime](ReleaseTime); changed  
              low and high Channels to First and Last because previous  
              terminology seemed too easily confused with high and low bytes  
              or high and low channels in 1208FS pin out diagrams.  
3/14/08 mpr added warning when data are discarded  
3/15/09 mk  timer\_preload calculation changed according to bug report and bugfix  
            suggested by Peter Meilstrup in forum message 9221. There was an  
            off-by-one bug present...  
3/24/12 mk  Add handling for options.livedata -- retrieval of data while  
            DAQ is running.  
6/21/15 mk  Implement options.sendChannelRange for the 1608-FS to allow skipping  
            of [DaqALoadQueue](DaqALoadQueue), which is likely pretty expensive.  
  
12/6/15 mk  Try to select interfaces ascending by interfaceID for assignment to  
            [IndexRange](IndexRange), instead of hard-coding ranges. This should not change  
            anything on Linux or Windows, but maybe it helps the brain-dead OSX.  
  
9/24/16 js  Remembers the serial number of the Daq device when options.begin is true,  
            then only uses device [IDs](IDs) with the same serial number; this allows multiple  
            devices to be attached to the same system. Adds optional field options.nodiscard  
            to keep all data, regardless of the consecutivity of reports.  
  
9/26/16 mk  Runs on Matlab R2013a and later, replacing the deprecated bitcmp function  
            for handling of 12 bit differential channels on non-USB 1608FS. Untested.  
  
5/17/23 mk  Try to fix issue with data loss / data misalignment if used in livedata  
            mode with [DaqAInScanContinue](DaqAInScanContinue) and more than 1 input channel, cfe.  
            https://psychtoolbox.discourse.group/t/sampling-frequency-of-analogue-input/4780/10  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqAInScan.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqAInScan.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqAInScan.m</code>
</div>

