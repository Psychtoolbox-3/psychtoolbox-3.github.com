# [DrawHighQualityUnicodeTextDemo](DrawHighQualityUnicodeTextDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[DrawHighQualityUnicodeTextDemo](DrawHighQualityUnicodeTextDemo)  
  
This demo shows how to draw high-quality, anti-aliased text, and some  
japanese text encoded in Unicode.  
  
[MacOS](MacOS)/X has text fonts with support for japanese characters preinstalled,  
so this should just work out of the box. Have a look at the code of the  
demo on how to select a suitable font, and how to read unicode text from  
the filesystem. The (commented out) reading code for SHIFT\_JIS -\> Unicode  
conversion would only work on recent Matlab releases. Older releases need  
different approaches - also different wrt. [PowerPC](PowerPC) vs. [IntelMac](IntelMac). That's  
why we hard-coded the text in this demo -- Want to have it working even  
on old Matlab 6...  
  
On MS-Windows you will need to install the special east-asian font  
support kit in order to be able to draw japanese text.  
How to do this? See...  
  
http://www.coscom.co.jp/japanesefont/index.html  
  
with some more info here:  
http://www.alanwood.net/unicode/fonts\_windows.html\#japanese  
  
After that, text drawing seems to "just work" with our "Courier New"  
font. If you don't install the font pack, you'll just see funny little  
squares instead of nice japanese characters...  
  
On [MacOS](MacOS)/X you have the choice between three different text  
rendering/layouting methods, as selectable by the [Screen](Screen) preference  
setting 'TextRenderer': The default is 1, which selects Apple's ATSU text  
renderer. A setting of 0 would also select ATSU but would use a different  
method for layout of text. Each method has its own weaknesses in that it  
will have trouble drawing text in some special fonts correctly, so you  
may have to choose the method based on the font to get best results.  
Typical standard fonts are handled correctly by both methods. A setting  
of 2 will use the Linux text rendering plugin (see "help [DrawTextPlugin](DrawTextPlugin)")  
which in our experience handles all fonts well and is of superior  
performance to the OSX ATSU renderer. However, given that historically  
ATSU was used on OSX for many years and each layout and rendering method  
will give slightly different text appearance, for reason of consistency  
we leave the default setting for OSX on 1, instead of using the superior  
setting 2.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DrawHighQualityUnicodeTextDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DrawHighQualityUnicodeTextDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DrawHighQualityUnicodeTextDemo.m</code>
</div>

