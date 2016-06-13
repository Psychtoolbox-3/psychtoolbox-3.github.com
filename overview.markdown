---
layout: page
title: Overview
categories: getting-started
---

The attraction of using computer displays for visual psychophysics is that they
allow software specification of the stimulus. Programs to run experiments are
often written in a low-level language (e.g., C or Pascal) to achieve full
control of the hardware for precise stimulus display. Although these low-level
languages provide power and flexibility, they are not conducive to rapid program
development.  Interpreted languages (e.g., BASIC, LISP, Mathematica, and Matlab)
abstract hardware details and provide friendlier development environments, but
don't provide the hardware control needed for precise stimulus display. The
Psychophysics Toolbox is a software package that adds this capability to the
Matlab and Octave application on Macintosh, Linux and Windows computers (we will
only mention Matlab for the remainder of this text, but statements mostly apply
to Octave as well).

Matlab is a high-level interpreted language with extensive support for numerical
calculations. The Psychophysics Toolbox interfaces between Matlab and the
computer hardware. The routines at the core of Psychtoolbox provide access to
the display frame buffer and color lookup table, allow synchronization with the
vertical retrace, support sub-millisecond timing, expose raw OpenGL commands,
support video playback and capture as well as low-latency audio or hardware
triggers, and facilitate the collection of observer responses through regular
and specialized input devices. Ancillary routines support common needs like
color space transformations and the QUEST threshold seeking algorithm.

The Matlab & Psychtoolbox environment is flexible yet relatively easy to learn.
Canned experimental programs fail because they usually can't do a really new
experiment. For that you need the expressive scope of a full-fledged computer
language, such as C or Matlab. Matlab is a particularly good language for
running laboratory experiments. Even for experienced programmers, three features
of Matlab greatly speed the development cycle over other languages. Matlab has a
rich library of high-level functions available to do math and plotting. It
operates on arrays and images as named variables. And it is interactive, so that
one can type `1 + 1` and immediately see the answer `2`, which is invaluable
when developing laboratory software to run experiments.

Brand-new users who have never programmed before will find that they're learning
three things when they start using the toolbox: Matlab itself, how to create
stimuli and measure responses, and how to organize an experiment. There is
almost no overlap between those three topics. The included demos illustrate how
many common tasks may be accomplished (see [PsychDemos][docs-demos] or type `>>
help PsychDemos` in Matlab after installation). For learning the language, many
people say they liked the Matlab manual. Others skipped the manual and learned
by trial and error.  Everyone uses Matlab's help feature frequently. It's one of
Matlab's better features and we have tried to follow their conventions with the
toolbox routines.

The Psychtoolbox is popular. As of October 2006, Psychtoolbox-2 has been
downloaded thirty thousand times: 24,324 Windows and 8,743 Mac OS 9.
Psychtoolbox-3 for Mac OSX was downloaded 1,832 times before 22 September 2006.

The current count, since 22 September 2006, of registered unique installations
of Psychtoolbox-3 appears below. The Psychtoolbox [forum][forum] has over 2500
members and about 4 messages a day. Principal investigators and their
collaborators have identified at least 127 [#grant-supported projects](../grants)
that use it. According to Google scholar, over 13500 articles [cite](../citations) it.

The following link is a PDF file with the slides of a presentation held at ECVP
2007 in Arezzo by Mario Kleiner. These slides will give you a quick overview
about the new features of Psychtoolbox-3 and differences to the old
Psychtoolbox-2:

- [Psychtoolbox presentation, given at ECVP 2007 Arezzo][arezzo]


Good luck programming.

Mario Kleiner, David Brainard, Denis Pelli, Chris Broussard, Tobias Wolf, Diederick Niehorster

[The Developers](developers)

* * *

    PTB registration stats here

 [docs-demos]: http://docs.psychtoolbox.org/PsychDemos
 [arezzo]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychDocumentation/Psychtoolbox3-Slides.pdf
 [forum]: /forum

 *[C or Pascal]: Presumably, this blurb was written 15 years ago
 *[BASIC]: make that 20
 *[forum]: Actually a mailing list
