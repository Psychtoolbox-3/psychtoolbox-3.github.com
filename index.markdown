---
layout: default
---

Overview
--------

Psychtoolbox interfaces between Matlab or Octave and the computer hardware. The
PTB core routines provide high performance 2D and 3D graphics with the highest
color and luminance precision, timing precision and control. This both on standard
displays, as well as with special visual stimulators, and with High Dynamic Range
displays, and with a wide variety of Virtual/Augmented Reality devices. They expose
raw OpenGL commands, support video playback and capture, as well as low-latency
precisely timed audio playback and capture. They facilitate the collection of observer
responses with high timing precision via various input modalities like keyboard, mouse,
game controllers, multi-touch touch screens, response boxes, gaze trackers, and digital /
analog i/o equipment. Ancillary helper routines support common needs like color space
transformations, calibration, and psychometric procedures like, e.g., the QUEST threshold
seeking algorithm and others.

Various 3rd party frameworks and higher level toolboxes are built on top of Psychtoolbox
to make implementation of research data collection especially easy in specific sub-domains
of neuroscience. For beginners or certain domains there also exist user friendly 3rd party
graphical user interfaces, e.g., [PsyBuilder](https://www.psybuilder.com).

You can also run some of your Psychtoolbox studies online, via VPixx Labmaestro service under
[https://vpixx.com/products/labmaestro-packngo.](https://vpixx.com/products/labmaestro-packngo)

Psychtoolbox has many active users, an active [forum](forum), and is widely
[cited](citations). The current version supports at least Matlab R2024b on Linux, Windows
and macOS, and Octave 5 and later on Linux, and Octave 7.3 on Windows, and Octave 9 on macOS.

Psychtoolbox News
-----------------

{% for post in site.posts limit: 3 %}
<article class="post">
    <header>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>
        <a href="http://github.com/{{ post.author }}" class="author">{{ post.author }}</a>
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: '%B %d, %Y' }}</time>
      </p>
    </header>

    {{ post.content }}

</article>
{% endfor %}

      
### [News Archive](news)
{: .abbrev}

---

{% for post in site.posts offset: 4 %}
<article class="post abbrev">
    <header>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>
        <a href="http://github.com/{{ post.author }}" class="author">{{ post.author }}</a>
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: '%B %d, %Y' }}</time>
      </p>
    </header>

</article>
{% endfor %}
