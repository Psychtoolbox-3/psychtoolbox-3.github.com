---
layout: default
---

Overview
--------

Psychtoolbox interfaces between Matlab or Octave and the computer hardware. The PTB core routines provide access to the
display frame buffer and color lookup table, reliably synchronize with the vertical screen retrace, support sub-millisecond
timing, expose raw OpenGL commands, support video playback and capture as well as low-latency audio, and facilitate the collection of observer responses. Ancillary routines support common needs like color space
transformations and the QUEST threshold seeking algorithm.

Psychtoolbox has many active users, an active [forum](forum), and is widely [cited](citations). PTB-3 is based on the
deprecated Psychophysics Toolbox Version 2 with its Matlab C extensions rewritten to be more modular and to use OpenGL
on the back end. The current version supports Matlab 7.x and Octave 3.2.x on Mac OSX, Linux and Windows.

Psychtoolbox News
-----------------

{% for post in site.posts %}
<article class="post">
    <header>
      <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
      <p>
        <a href="http://github.com/{{ post.author }}" class="author">{{ post.author }}</a>
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: '%B %d, %Y' }}</time>
      </p>
    </header>

{{ post.content }}

</article>
{% endfor %}
