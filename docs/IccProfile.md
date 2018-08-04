# [IccProfile](IccProfile)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

icc=[IccProfile](IccProfile)(command,file,icc)  
  
  
  
UNIMPLEMENTED! This function is not yet available in Psychtoolbox-3.  
Porting it from the old Psychtoolbox-2 should be doable for somebody  
with basic C programming skills. If you feel like contributing this  
function, please do so!  
  
  
  
[IccProfile](IccProfile).mex will read any ICC or [ColorSync](ColorSync) profile. The  
International Color Consortium (ICC) published a standard file  
format for saving color calibration data for imaging devices. This  
includes digital cameras, scanners, printers, and monitors. Users  
of the Psychophysics Toolbox will be primarily interested in the  
use of an ICC Profile to characterize their CRT monitor or LCD  
display. The idea is that the file contains all the necessary  
information to transform the specification of a color in a standard   
perceptual space (e.g. CIE X,Y,Z) into the numbers necessary to   
display that color.  
web http://www.color.org/profiles.html ;  
  
### USAGE:  
  
icc=[IccProfile](IccProfile)('Read',file)                      % Gets data into Matlab.  
folder=[IccProfile](IccProfile)('Folder')                      % [ColorSync](ColorSync) Profiles folder  
file=[IccProfile](IccProfile)('Filename',screenNumber,newfile) % Get/set screen's profile.  
[IccProfile](IccProfile)('ShortDump',file,[tag])               % For exploring.  
[IccProfile](IccProfile)('Dump',file,[tag])                    % ""  
[IccProfile](IccProfile)('LongDump',file,[tag])                % ""  
  
"file"      is a filename, a partial or complete path, for an ICC   
            Profile file. The default folder is the [ColorSync](ColorSync) Profiles   
            folder (in the System Folder).  
"icc"       is a Matlab struct.  
"folder"    path string gives location of [ColorSync](ColorSync) Profiles folder.  
"tag"       is a four-character string identifying a chunk of   
            information in the icc profile, e.g. 'rTRC' for the red   
            Tone Reproduction Curve (i.e. gamma curve for red phosphor)    
            or 'gXYZ' for the the X,Y,Z color coordinates of the green   
            phosphor.  
'Read'      returns a Matlab struct with one field for each tag in the  
            profile. The field will still be present, but empty, if the   
            tag is of an unknown type, or if an error was encountered in  
            reading the tag. (Use 'Dump' to diagnose.) 'Read' recognizes   
            most of the tag types relevant to monitor calibration.  
'Folder'    returns the path (a string) for the [ColorSync](ColorSync) Profiles folder.  
            Use DIR[(IccProfile]((IccProfile)('Folder')) to get a list of files there.  
'Filename'  get and/or set the filename of the profile associated with your  
                        screen. Or use the Monitors control panel (go to color) to choose.  
            Note that setting the file has the side effect of loading  
            the video card's gamma table from the 'vcgt', if present in  
            your profile.   
'Dump'      describes every tag in the profile. Or just one tag.  
'ShortDump' describes every tag in the profile, with less detail.  
'LongDump'  describes every tag in the profile, with more detail.  
  
### EXAMPLE:  
  
file=iccprofile('filename',0)  
icc=iccprofile('read',file)  
  
This will read all the information in the profile associated with  
screen 0 (the main screen) and provide it to you as a handy Matlab struct  
"icc" that you can use in your software. For explanation of the contents,  
consult the official ICC documentation, plus Apple's documentation of  
their custom tags: 'vcgt' and 'mmod'.  
web http://www.color.org/profiles.html ;  
web http://developer.apple.com/techpubs/macos8/[MultimediaGraphics](MultimediaGraphics)/[ColorSyncManager](ColorSyncManager)/[ManagingColorWithColorSync](ManagingColorWithColorSync)/[ColorSync](ColorSync).7b.html  
  
### EXPLANATION OF TAG TYPE:  
  
Most of the information in a profile is stored as chunks of data,  
called elements. Each element has a unique 4-character tag name and  
a 4-character tag type. [IccProfile](IccProfile) accepts every tag name, and  
installs a corresponding field in your icc struct, with the same  
name (e.g. 'desc'). However, [IccProfile](IccProfile) will be able to transfer the  
content of the profile element to your struct only if [IccProfile](IccProfile)  
recognizes the type. At present, [IccProfile](IccProfile) can read the following  
tag types:  
  
NAME                        TYPE      TAGS THAT USE IT.  
Profile description         'desc'    'desc'                                
Tone reproduction curve     'curv'    'rTRC','gTRC','bTRC','kTRC'               
X,Y,Z of a color            'XYZ '    'rXYZ','gXYX','bXYZ','wtpt','bkpt','lumi'  
Text string                 'text'    'cprt'  
Date and time               'dtim'    'calt'  
Viewing conditions          'view'    'view'  
Measurement type            'meas'    'meas'  
Data (unformatted)          'data'  
Unsigned 8-bit int array    'ui08'  
Unsigned 16-bit int array   'ui16'  
Unsigned 32-bit int array   'ui32'  
Unsigned 64-bit int array   'ui64'  
Unsigned 32-bit fixed array 'uf32'  
Signed 32-bit fixed array   'sf32'  
Video card gamma            'vcgt'    'vcgt'  
Make and model              'mmod'    'mmod'  
  
### TAG  
'desc'    profile description, a human readable text string  
'rTRC'    red tone reproduction curve  
'gTRC'    green tone reproduction curve  
'bTRC'    blue tone reproduction curve  
'kTRC'    gray tone reproduction curve  
'rXYZ'    red phosphor color  
'gXYZ'    green phosphor color  
'bXYZ'    blue phosphor color  
'wtpt'    white point  
'bkpt'    black point  
'lumi'    luminance in cd/m^2  
'cprt'    copyright  
'calt'    calibration date and time  
'view'    viewing conditions  
'meas'    measurement type  
'vcgt'    custom Apple tag for video card gamma table  
'mmod'    custom Apple tag for make and model of the device  
  
NOTE: [IccProfile](IccProfile) may report errors in an apparently good profile.  
This is because icclib enforces the ICC standard more strictly than  
[ColorSync](ColorSync) does, so it picks up errors that were previously missed.  
(On 7/31/00 we reported to Apple two such errors, affecting most of their   
[ColorSync](ColorSync) Profiles, and added a work-around to [IccProfile](IccProfile).)  
You can try running Apple's "Profile First Aid", which detects and  
fixs some common profile errors, though it too is less strict than  
icclib. "Profile First Aid" 3.0.1 is installed in the Apple  
Extras:[ColorSync](ColorSync) Extras folder when you install [ColorSync](ColorSync) 3.0.1  
web http://asu.info.apple.com/swupdates.nsf/artnum/n11674 ;  
  
### CALIBRATION:  
  
You can buy a calibration package consisting of a program (e.g.  
[ColorBlind](ColorBlind) [ProveIt](ProveIt)! or Monaco [EZColor)](EZColor)) and a simple colorimeter to  
easily create an ICC profile for your monitor. Using [IccProfile](IccProfile).mex,  
it should be easy to use that calibration data to do your color  
corrections, but we haven't actually tried that yet. Here are a few  
calibrators that seems to be good, from what we've read. We've  
included links to the manufacturer (if available) and to Jon Cone's  
inkjetmall web site because he knows a lot about digital  
printing and has good advice about choosing among these products.  
  
[ColorBlind](ColorBlind) [ProveIt](ProveIt)! software $50  
Does not include colorimeter. Can be used alone, using perceptual  
matching, or with the Sequel Chroma 4 colorimeter, below.  
web http://www.color.com/Products/proveit.html ;  
web http://www.inkjetmall.com/store/prove-it.html ;  
  
Sequel Chroma 4 CRT & LCD monitor colorimeter $249  
Requires software, which is not included. Compatible with [ColorBlind](ColorBlind)  
and Monaco.  
web http://www.inkjetmall.com/store/measuring-devices.html\#monitors ;  
  
Monaco [EZColor](EZColor) software $299  
[MonacoSENSOR](MonacoSENSOR) colorimeter $249 (or both together for $499)  
web http://www.monacosys.com/monacoezcolor.html ;  
  
The [ColorBlind](ColorBlind)+Sequel package, for $299, is cheaper than the $499  
Monaco package, and the [ColorBlind](ColorBlind) software seems to be at least as  
highly regarded as Monaco's by Jon Cone and others using it to  
calibrate their monitors for critical digital color printing.  
  
Denis Pelli  
  
ACKNOWLEDGEMENT: [IccProfile](IccProfile).mex is largely a Matlab interface to   
the excellent free icclib created in C by Graeme Gill, for which we   
are very grateful.  
web http://web.access.net.au/argyll/color.html ;  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/IccProfile.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/IccProfile.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/IccProfile.m</code>
</div>

