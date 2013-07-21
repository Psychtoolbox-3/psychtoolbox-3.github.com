---
layout: page
title: Using PTB on Linux
categories: getting-started
---

**GNU/Linux is the recommended operating system of choice for demanding
experimental setups and experimental paradigms.**

Due to it being a free and open-source operating system, Linux provides us and
you with a couple of advantages:

-   Thanks to its open source nature and constant community development and
    peer review of its code-base, it generally exhibits less bugs as well as
    higher performance and robustness in areas of functionality that matter
    especially for demanding experimental paradigms, e.g., precision and
    robustness of timing, resource usage and efficiency. The system is also
    much more flexible and tweakable, should performance tuning and
    customization be neccessary for special experimental setups.

-   The open access to its source code allows us to review the implementation
    of important low-level details. This allows us to understand how and why
    the system behaves a certain way and allows us to implement a better
    integration between Psychtoolbox and the operating system.  Apple's OS X
    and Microsoft's Windows are mostly black boxes for us, leaving us with
    guess-work about many implementation details, which leads to suboptimal
    integration with Psychtoolbox.

-   The open development process allows us to participate in the design,
    implementation, improvement and bug-fixing of crucial operating system
    components ourselves. We can help to fix and improve the underlying
    infrastructure and plumbing instead of having to resort to ugly and
    suboptimal hacks in Psychtoolbox itself to work around the unfixable flaws
    of a black box.

### Installation via script

The installation works the same as on Windows or OS X, so follow the instructions
on the main [download][1] page. However, Psychtoolbox requires a few software
libraries to be installed on your Linux system. The installer will tell you
what kind of libraries you need to install, should some of them be missing. For
the most simple way of installation, read on.

### Neuro Debian installation

The most convenient way of installation if you have Debian or a Debian
derivative, e.g., Ubuntu Linux, is the [NeuroDebian repository of
neuroscience software][2]. It provides a large number of popular
neuroscience related software packages, optimally configured for use on Debian
and Ubuntu, with a convenient installation via the package management system of
your Linux distribution.


If you install the package `octave-psychtoolbox-3`,
your system will be automatically configured and tuned for use with
Psychtoolbox under GNU/Octave.

    sudo apt-get install octave-psychtoolbox-3 

If you prefer to run Psychtoolbox with Matlab, you can can run the function
[DownloadAdditionsForNeuroDebian][3] from within a Matlab running under Linux.
It will install a few additional files needed to run Psychtoolbox with Matlab
on Linux.

Alternately install this meta-package

    sudo apt-get install matlab-psychtoolbox-3 

### Debian-7/testing/unstable, Ubuntu 12.10 and later installation

Psychtoolbox-3 for octave is part of current Debian unstable / testing /
experimental, as well as the official Debian-7.0 and Ubuntu 12.10
distributions. Everything said in the "Neuro Debian" section applies, except
you don't need to add the Neuro Debian ppa to your software sources.  Simply
use your favorite package manager to install the psychtoolbox-3 package and
you're done. E.g., in a terminal window on Ubuntu 12.10:

    sudo apt-get install psychtoolbox-3

### Choice of Distribution

The Linux specific code in PTB is currently being developed and tested using
[Ubuntu Linux][4]. We recommend this distribution because
it is beginner friendly and constantly tested with Psychtoolbox. However, there
is nothing wrong with other Linux distributions, so feel free to use them, but
keep in mind we can only provide you with support for Ubuntu at the moment. See
[[UsingPsychtoolboxOnUbuntu]] for more details and instructions on Ubuntu Linux.

### Conflicts of libraries shipped with Matlab and system libraries

With some Matlab versions execution of `Screen()` may lead to MEX file errors.

Commonly these errors arise from outdated versions of libraries like Zlib
(`libz*`) that come included with Matlab and which override the system
libraries.

To work around these problems, it is often sufficient to delete or move all
`lib*.so*` files in your `Matlab/bin/glnx86` or `Matlab/bin/glnxa64` folder
that showed up in the MEX file loading errors.


[1]: {{ site.url }}/download#linux
[2]: http://neuro.debian.net
[3]: http://docs.psychtoolbox.org/DownloadAdditionsForNeuroDebian
[4]: http://www.ubuntu.com/
