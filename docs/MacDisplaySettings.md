# [MacDisplaySettings](MacDisplaySettings)
##### >[Psychtoolbox](Psychtoolbox)>[PsychContributed](PsychContributed)>[MacDisplaySettings](MacDisplaySettings)

 [oldSettings,errorMsg] = [MacDisplaySettings](MacDisplaySettings)([screenNumber,][newSettings])  
  
% [MacDisplaySettings](MacDisplaySettings) allows you to peek and poke seven settings in the  
 System Preferences:Displays panel by using the corresponding fields in  
 its newSettings and oldSettings input-output arguments. This allows you  
 to temporarily override any macOS user customization of your  
 display, to allow calibration and user testing with stable display  
 settings. (To be clear, we help you handle the macOS built-in System  
 Preferences; we do nothing about the zillion third-party apps that your  
 users might install.)  All the parameters refer only to the screen  
 selected by screenNumber. However, Apple has very limited support for  
 non-Apple displays, so you probably won't have Brightness, True Tone, or  
 Night Shift on your external display unless it's made by Apple. The Color  
 Profile options seems to always be available for all displays.  
  
% DISPLAY  
 brightness            the Brightness slider  
 automatically         the "Automatically adjust brightness" checkbox  
 trueTone              the "True Tone" checkbox  
% COLOR  
 showProfilesForThisDisplayOnly the checkbox  
 profile               name of selection in Color Profile menu  
 profileRow            row \# of selection in Color Profile menu  
% NIGHT SHIFT  
 nightShiftSchedule    the Night Shift Schedule pop up menu  
 nightShiftManual      the Night Shift Manual checkbox  
  
% INPUT ARGS. Both arguments are optional: the integer screenNumber  
 and the struct newSettings. You can provide either, neither, or both.  
 It's ok to provide just "newSettings", omitting the "screenNumber"  
 (default is 0, the main screen). The struct "newSettings" can include  
 any number, from none to all, of the eight allowed fields:  
  
 "brightness" (in the range 0.0 to 1.0)  
 "automatically" (true or false)  
 "trueTone" (true or false)  
 "nightShiftSchedule" ('Off','Custom', or 'Sunset to Sunrise')  
 "nighShiftManual" (true or false)  
 "showProfilesForThisDisplayOnly" (true or false)  
 "profile" (text name)  
 "profileRow" (integer)  
  
 If newSettings.profileRow is specified then newSettings.profile is  
 ignored. True Tone is not available on Macs manufactured before 2018.  
  
% OUTPUT ARGS: The struct oldSettings uses the fields listed above to  
 report the prior state of all available parameters. errorMsg is a second,  
 optional, output argument. If everything worked then errorMsg is an empty  
 string. Otherwise it will describe one failure, even if there were  
 several. In peeking, the fields corresponding to a parameter that could  
 not be read will be empty [], and that is not considered an error. In  
 poking, if you got an error (nonempty errorMsg), you might call  
 [MacDisplaySettings](MacDisplaySettings) again to compare the new peek with what you poked.  
  
% EXAMPLES. Typical uses of [MacDisplaySettings](MacDisplaySettings) include just typing the  
 function name to learn the current settings:  
  
 [MacDisplaySettings](MacDisplaySettings)  
  
 ans =  
  
###    struct with fields:  
  
                         brightness: 0.8700  
                      automatically: 0  
                           trueTone: []  
                 nightShiftSchedule: 'Off'  
                   nightShiftManual: 0  
     showProfilesForThisDisplayOnly: 0  
                            profile: 'Color LCD'  
                         profileRow: 1  
  
 % In one call to [MacDisplaySettings](MacDisplaySettings) you can both peek the old settings  
 % and poke new settings.  
  
 newSettings.brightness=0.87;  
 newSettings.automatically=false;  
 newSettings.trueTone=false;  
 newSettings.nightShiftSchedule='Off';  
 newSettings.nightShiftManual=false;  
 newSettings.showProfilesForThisDisplayOnly=false;  
 newSettings.profile='Display P3'; % Select Profile by name.  
 newSettings.profileRow=1; % Specify Profile row, and ignore "profile" field.  
  
 [oldSettings,errorMsg]=[MacDisplaySettings](MacDisplaySettings)(screen,newSettings)  
  
 % Now use the display, and then restore the old settings as you found  
 % them. You can omit "screen" if you're working on the main screen (0).  
  
 [MacDisplaySettings](MacDisplaySettings)(screen,oldSettings);  
  
% PRESERVING THE DISPLAY STATE. Apple invites Macintosh users to adjust  
 many parameters in the System Preferences Displays panel to customize  
 their display color and brightness including the enabling of dynamic  
 adjustments of all displayed images in response to personal preference,  
 ambient lighting, and time of day. Many users enjoy this, but, unless  
 reliably overriden, those adjustments defeat our efforts to calibrate the  
 display one day and, at a later date, use our calibrations to reliably  
 present an accurately specified stimulus. [MacDisplaySettings](MacDisplaySettings) aims to  
 satisfy everyone, by allowing your calibration and test programs to use  
 the computer in a fixed state, unaffected by individual user whims,  
 ambient lighting, and time of day, while saving and later restoring  
 whatever custom states the users have selected. [MacDisplaySettings](MacDisplaySettings)  
 reports and controls seven settings. It allows you to read their current  
 state, set them to standard values for your critical work, and, when  
 you're done, restore them to their original values.  
  
% ERROR REPORTING. If everything worked the optional output argument  
 errorMsg is an empty string. Otherwise errorMsg will contain an error  
 message string, just one even if there are mutiple faults.  
  
% ERROR CHECKING. Most of the controls are straightforward, you are just  
 peeking and poking a Boolean (0 or 1) or a small integer with a known  
 range. Brightness and Profile are more subtle, so [MacDisplaySettings](MacDisplaySettings)  
 always checks by peeking immediately after poking Brightness or Profile  
 (whether by name or by row). A discrepancy will be flagged by a nonempty  
 string in errorMsg. Note that you provide a float to Brightness but  
 within the macOS it's quantized to roughly 18-bit precision. In my  
 testing on a [MacBook](MacBook) and a [MacBook](MacBook) Pro, poking random numbers between 0.0  
 and 1.0, the discrepancy between peek and poke is uniformly distributed  
 over the range -5e-6 to +5e-6, provided you wait at least 0.1 s after the  
 latest poke. (When you move the slider, the macOS does a slow fade to the  
 new value.) For MacDisplaySettings's built-in peek-after-poke test,  
 [MacDisplaySettings](MacDisplaySettings) accepts the peek of Brightness if it is within 0.001  
 of what we poked, otherwise it waits 0.1 s and peeks again, and if the  
 second peek is still out of range, then reports the discrepancy in  
 errorMsg.  
  
% RELIABLE. [MacDisplaySettings](MacDisplaySettings) is reliable, unlike my  
 previous efforts [(AutoBrightness]((AutoBrightness).m, Brightness.m, [ScreenProfile](ScreenProfile).m). The  
 improvement results from discovering, first, that the applescript  
 operations proceed MUCH more quickly while System Preferences is  
 frontmost (so we now bring it to the front), and, second, we now follow  
 the example of pros and have wait loops in the applescript to make sure  
 each object is available before accessing it. Since those enhancements,  
 it now reliably takes 2 s on [MacBook](MacBook) Pro and 8 s on [MacBook](MacBook), instead of  
 the long 60 s delays, and occasional timeout errors, that afflicted the  
 old routines.  
  
% INPUT ARGUMENT RANGE. newSettings.brightness has range 0.0 to 1.0;  
 automatically, trueTone, nightShiftManual, and  
 showProfilesForThisDisplayOnly are boolean (true or false);  
 nightShiftSchedule is a text field corresponding to any of the items in  
 the Displays pop up menu ('Off', 'Custom', 'Sunset to Sunrise').  
 (nightShiftSchedule is compatible with international systems, provided  
 you use the English field names when calling [MacDisplaySettings](MacDisplaySettings).m.)  
 profile (text) specifies the desired Color Profile by name, and  
 profileRow (integer) specifies it by row. The row number will work  
 internationally. I suspect the names that you read and write will be in  
 whatever your macOS takes to be the local language. Thus  
 nightShiftSchedule uses English regardless of locality, whereas profile  
 uses local names. Thus, your program can get consistent international  
 behavior by using row numbers to specify profile and English names to  
 specify nightShiftSchedule.  
  
% Your screen's display profile is a video lookup table, it  
 affects the color and luminance of everything you display. Apple allows  
 programmers to read and write the current color profile, which is in  
 memory, and I think that there are several consumer apps that do that (in  
 much the same spirit as Apple's Night Shift and [TrueTone)](TrueTone)). System  
 Preferences: Displays is unaware of such changes. Clicking on the profile  
 name that is currently in use has no effect. Clicking on any other  
 profile causes it to be loaded, fresh from the disk master. So, when you  
 ask [MacDisplaySettings](MacDisplaySettings) to activate a profile that is already current, it  
 plays safe and first clicks another profile and then clicks on the one  
 you specified, to be sure that it loads fresh from disk.  
  
% ERROR REPORTING is strict. Out-of-range or unrecognized arguments  
 produce fatal errors if detected by [MacDisplaySettings](MacDisplaySettings).m. When such  
 errors are detected in [MacDisplaySettings](MacDisplaySettings).applescript they are merely  
 flagged by a message in the optional output argument errorMsg. When  
 throwing a fatal error, if Psychtoolbox is present on the MATLAB path,  
 then [MacDisplaySettings](MacDisplaySettings) first closes any open windows (by calling  
 Psychtoolbox "[sca](sca)"), so the error message won't be hidden behind your  
 window.  
  
% REQUIREMENTS: macOS and MATLAB. (If it detects Psychtoolbox, then it  
 will use the "[sca](sca)" command to close windows before throwing a fatal  
 error.) In its current form, [MacDisplaySettings](MacDisplaySettings) has only been tested on  
 macOS Mojave (10.14) localized for USA. Earlier versions of this code  
 supported macOS 10.9 to 10.14. It's designed to work internationally, but  
 that hasn't been tested yet. It was tested on MATLAB 2019a, and very  
 likely works on any version of MATLAB new enough to include structs. I  
 think, but haven't checked, that the MATLAB code is pure basic MATLAB (no  
 toolboxes) with one negligible exception. Before throwing an error, we  
 check for the presence of the Psychtoolbox, if present then we call the  
 Psychtoolbox routine "[sca](sca)" ([Screen](Screen) [Close](Close) All) to close any open windows,  
 so the error won't be hidden behind your window.  
 [MacDisplaySettings](MacDisplaySettings).applescript needs only the macOS. It works on any  
 screen, including an external monitor, but testing with external monitors  
 has been very limited.  
  
% DEVELOPERS. To write Applescript like this, I strongly recommend that  
 you buy the Script Debugger app from Late Night Software.  
 https://latenightsw.com/  
 and the UI Browser app from UI Browser by [PFiddlesoft](PFiddlesoft).  
 https://pfiddlesoft.com/uibrowser/  
 The Script Debugger is a the best Applescript editor and debugger. The UI  
 Browser allows you to discover the user interface targets in System  
 Preferences that your script will read and set. With it you can do in an  
 hour what would otherwise take days of trial and error.  
  
% APPLE PRIVACY. Unless MATLAB has the needed user-granted   
 permissions to control the computer, attempts by [MacDisplaySettings](MacDisplaySettings) to  
 change settings will be blocked by the macOS. The needed permissions  
 include Accessibility, Full Disk Access, and Automation, all in System  
 Preferences: Security & Privacy: Privacy. Here are Apple pages on  
 privacy in general, and accessibility in particular:  
 https://support.apple.com/guide/mac-help/change-privacy-preferences-on-mac-mh32356/mac  
 https://support.apple.com/guide/mac-help/allow-accessibility-apps-to-access-your-mac-mh43185/mac  
 New versions of macOS may demand more permissions. In some cases  
 [MacDisplaySettings](MacDisplaySettings) will detect the missing permission, open the  
 appropriate System [Preference](Preference) panel, and provide an  
 error dialog window asking the user to provide the permission. In other  
 cases [MacDisplaySettings](MacDisplaySettings) merely prints the macOS error message. The  
 granting of permission needs to be done only once for your specific  
 MATLAB app. When you upgrade MATLAB it typically has a new name, and will  
 be treated by macOS as a new app, requiring new granting of permissions.  
 Only users with administator privileges can grant permission. When you  
 grant permission, sometimes the macOS doesn't seem to notice right away,  
 and keeps claiming MATLAB lacks permission. It may help to restart MATLAB  
 or reboot.  
  
% PROFILE ROW NUMBERING. Note that when you look at the list of profiles  
 in System Preferences:Displays:Color there is a line separating the top  
 and bottom sections of the list. Apple assigns a row number to that line,  
 but trying to select that row has no effect and returns an error in  
 errorMsg.  
  
% WHAT "BRIGHTNESS" CONTROLS: Adjusting the "brightness" setting in an LCD  
 controls the luminance of the fluorescent light that is behind the liquid  
 crystal display. I believe that the "brightness" slider controls only the  
 luminance of the source, and does not affect the liquid crystal itsef,  
 which is driven by the GPU output. The luminance at the viewer's eye is  
 presumably the product of the two factors: luminance of the source and  
 transmission of the liquid crystal, at each wavelength.  
  
% INSTALLATION. Just put both the [MacDisplaySettings](MacDisplaySettings).m and  
 [MacDisplaySettings](MacDisplaySettings).applescript files anywhere in MATLAB's path.  
  
% MULTIPLE SCREENS: Seems to be working, not yet thoroughly tested.  
 Color Profiles work for all monitors and provides access to all the  
 controls you see in the windows of System Preferences: Displays. However,  
 Apple provides fewer Display options for external monitors, especially  
 non-Apple monitors.  
  
% HISTORY  
 June 25, 2017. denis.pelli@nyu.edu wrote "Brightness" for the  
 Psychtoolbox, and later "[AutoBrightness](AutoBrightness)".  
  
 July 16,2019 Improved by looking at code here:  
 https://apple.stackexchange.com/questions/272531/dim-screen-brightness-of-mbp-using-applescript-and-while-using-a-secondary-mon/285907  
  
 April 2020. Wrote [MacDisplaySettings](MacDisplaySettings), based on Brightness, but enhanced  
 to also support Automatically, True Tone, Night Shift, and Profile.  
  
 April 14, 2020. Added wait loops (in the applescript) to wait for "tab  
 group 1" before accessing it. This has nearly eliminated the occasional  
 time out failures, in which [MacDisplaySettings](MacDisplaySettings).m returns [] for  
 brightness and automatic, but returns correct values for night shift.  
  
 May 3, 2020. In the Applescript, I now "activate" System Preferences at  
 the beginning (and reactivate the former app when we exit), and this runs  
 much faster. Formerly, delays of 60 s were common, with occasional time  
 outs. Now it reliably takes 2 s on [MacBook](MacBook) Pro and 8 s on [MacBook](MacBook).  
  
 May 7, 2020. Shortened the help text, reducing redundancy. Check for  
 unrecognized fields in newSettings. Improved error reporting.  
  
 May 8, 2020. Enhanced to support arbitrary screenNumber, i.e. external  
 monitors.  
  
 May 9, 2020. Improved speed (by 30%) by replacing fixed delays in  
 applescript with wait loops. Enhanced the built-in peek of brightness  
 afer poking. Now if the peek differs by more than 0.001,  
 [MacDisplaySettings](MacDisplaySettings) waits 100 ms and tries again, to let the value settle,  
 as the visual effect is a slow fade. Then it reports in errorMsg if the  
 new peek differs by more than 0.001. In limited testing, waiting for a  
 good answer works: the peek-poke difference rarely exceeds +/-5e-6 and  
 never exceeds 0.001. It's my impression that if we always waited 100 ms,  
 then the discrepancy would always be less than +/-5e-6.  
  
 May 9, 2020. APPLESCRIPT: Improved speed by replacing fixed delays in  
 applescript with wait loops. Enhanced the peek of brightness afer poking.  
 Now if the peek differs by more than 0.001, [MacDisplaySettings](MacDisplaySettings) waits 100  
 ms and tries again, to let the value settle, as the visual effect is a  
 slow fade. Then it reports in errorMsg if the new peek differs by more  
 than 0.001. In limited testing, waiting for a good answer works: the  
 peek-poke difference rarely exceeds +/-5e-6 and never exceeds 0.001. It's  
 my impression that if we always waited 100 ms, then the discrepancy would  
 always be less than +/-5e-6.  
  
 May 14, 2020. Added to Psychtoolbox.  
  
 May 15, 2020. Now also pass a flag from [MacDisplaySettings](MacDisplaySettings).m to  
 [MacDisplaySettings](MacDisplaySettings).applescript indicating whether Psychtoolbox has a  
 window on the main screen. In that case, [AppleScript](AppleScript) will not try to  
 show a dialog. Added a loop in [AppleScript](AppleScript) to wait for System Preferences  
 window to open; this fixes a rare error.  
  
 May 15, 2020. APPLESCRIPT: Added a loop in [AppleScript](AppleScript) to wait for System  
 Preferences window to open; this fixes a rare error. Replaced every error  
 code with a message in errorMsg.  
  
 May 17, 2020. Improved handling of empty args, which are now replaced by  
 default values, just like missing args.  
  
 May 20, 2020. APPLESCRIPT: [MacDisplaySettings](MacDisplaySettings) hung up on my student Benji  
 Luo with the Night Shift panel showing. I suspect it was in an endless  
 loop waiting for the menu to pop up after a click. I rewrote the loop to  
 throw an error if the menu doesn't appear after three attempts of  
 clicking and waiting up to 500 ms each time.  
  
% ACKNOWLEGEMENTS. Thanks to Mario Kleiner for explaining how macOS  
 "brightness" works. Thanks to nick.peatfield@gmail.com for sharing his  
 applescript code for dimmer.scpt and brighter.scpt. And to Hormet Yiltiz  
 for noting that we need to control Night Shift.  
  
% SEE ALSO:  
 https://support.apple.com/en-us/HT208909 % True Tone  
 https://support.apple.com/en-us/HT207513 % Night Shift  
 [Screen](Screen) [ConfigureDisplay](ConfigureDisplay)? % In Psychtoolbox  
 http://www.manpagez.com/man/1/osascript/  
 https://developer.apple.com/library/mac/documentation/[AppleScript](AppleScript)/Conceptual/[AppleScriptLangGuide](AppleScriptLangGuide)/reference/ASLR\_cmds.html  
 https://discussions.apple.com/thread/6418291  
 [ScriptDebugger](ScriptDebugger) app from Late Night Software.  
 https://latenightsw.com/  
 [UIBrowser](UIBrowser) app from [PFiddlesoft](PFiddlesoft).  
 https://pfiddlesoft.com/uibrowser/  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychContributed/MacDisplaySettings/MacDisplaySettings.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychContributed/MacDisplaySettings/MacDisplaySettings.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychContributed/MacDisplaySettings/MacDisplaySettings.m</code>
</div>

