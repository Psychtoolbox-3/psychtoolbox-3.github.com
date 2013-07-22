---
layout: page
title: test matlab code boxes
author: towolf
category: site
---

MATLAB test code box
--------------------

kramdown `~~~ matlab` to google-code-prettify

~~~ matlab
function sca
% sca -- Execute Screen('CloseAll');
% This is just a convenience wrapper that allows you
% to save typing that long, and frequently needed,  command.
% It also unhides the cursor if hidden, and restores graphics card gamma
% tables if they've been altered.
%

% History:
% 4/6/6  Written (MK).
% 5/31/8 Add CLUT restore call (MK).

% Unhide the cursor if it was hidden:
ShowCursor;

for win = Screen('Windows')
    if Screen('WindowKind', win) == 1
        if Screen('GetWindowInfo', win, 4) > 0
            Screen('AsyncFlipEnd', win);
        end
    end
end

% Close all windows, release all Screen() ressources:
Screen('CloseAll');

% Restore (possibly altered) gfx-card gamma tables from backup copies:
RestoreCluts;

return;
~~~

Bash test code box
------------------

kramdown `~~~ bash` to google-code-prettify

~~~ bash
#!/bin/bash
ffmpeg -loglevel verbose \
       -i "$1" \
       -vf 'setpts=PTS/600' \
       -f yuv4mpegpipe \
       - \
  | mergeyuv 30 \
  | ffmpeg \
      -y \
      -r 30 \
      -f yuv4mpegpipe \
      -i - \
      -c:v libx264 -crf 17 -profile:v high -preset medium \
      -r:v 30 \
      "$2"
~~~
