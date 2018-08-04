# [KbDemo](KbDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

% [KbDemo](KbDemo)  
 Shows how to detect when the user has pressed a key.  
 See [KbCheck](KbCheck), [KbName](KbName), [KbWait](KbWait), [GetChar](GetChar), [CharAvail](CharAvail).  
  
 The [KbXXX](KbXXX) functions are low-level and go after the state of the keyboard.  
 The [GetChar](GetChar)/[CharAvail](CharAvail) interface pulls characters out of the event queue.  
 The advantage of the [KbXXX](KbXXX) functions is that if you can sit and wait on  
 characters in a tight loop, you'll get less of a lag.  But if the key  
 goes up and down in between when your code checks the keyboard state, you'll  
 miss it.  
  
 The advantage of [GetChar](GetChar)/[CharAvail](CharAvail) is that they may be used  
 asychronously - the OS will pick up the character whether your code  
 is looking for it when it comes.  
  
 This demo works fine the with Keyspan Digital Media Remote:  
 http://www.keyspan.com/products/usb/remote/  
 However, the Digital Media Remote is sluggish (max alternating key rate of 2 Hz),    
 suggesting that it may not be well suited for measuring reaction time.  
  
 Normally, characters typed creep through and appear in the command window or  
 file being edited, depending on which has focus. You can prevent Matlab  
 from receiving typed characters by calling [ListenChar](ListenChar)(2); at the  
 beginning of you script and calling [ListenChar](ListenChar)(0); at the end of your  
 script. Caution: Make sure to always call [ListenChar](ListenChar)(0) at normal exit and in all  
 error handling routines, otherwise Matlab will be left with a dead  
 keyboard and you'll be unable to type any commands into the Matlab  
 window! Pressing CTRL+C will reenable the keyboard in such a case.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/KbDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/KbDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/KbDemo.m</code>
</div>

