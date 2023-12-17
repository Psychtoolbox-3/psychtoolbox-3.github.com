---
layout: post
title: End of year 2023 announcements.
categories: news
author: kleinerm
---

* I am now on vacation throughout December and much of January 2024, as my employer wants me to use up some good chunk of the unused vacation days I have left over from the years 2022 and 2023 to reduce liability to the business. After that I'll be busy with catching up on important (=as in actually paid for, or critical) work that will fall behind due to the vacation.
**Therefore all paid user support from support memberships for new support requests after this point in time is suspended until sometimes in the first half of February 2024.**

* GitHub announced that they will permanently disable the Subversion (SVN) frontend to their services at 8th January 2024. Our installer `DownloadPsychtoolbox` and updater `UpdatePsychtoolbox` depend on that SVN frontend.
**This means `DownloadPsychtoolbox` and `UpdatePsychtoolbox` will cease to function at or after 8th January 2024.** The current installer and updater as of PTB 3.0.19.7 will simply abort with a hopefully helpful error message, older versions will error-out with less helpful error messages. Multiple brownouts of the service have been scheduled by GitHub throughout December as a heads-up, so temporary hour-long or day-long failure of the installer and updater leading to 8th January are expected. If that happens, just retry a few hours or a day later. Due to the lack of financial funding by the vast majority of our users, I couldn't afford the time to work on a suitable replacement or alternative solution at the moment, so these scripts will stay dysfunctional for the time being.

  * Linux users can continue to use the conveniently installable packages from NeuroDebian (reasonably up to date), or the Debian/Ubuntu/RaspberryPi OS distributions (usually outdated).

  * People knowledgeable in the use of Git can obviously use Git to access our repository on Github.

  * For everybody else there is the less convenient and child proof alternative download via zip file, as described in the downloads section of our website.

  Of course you still have to follow the operating system specific setup steps as you had to do with the automatic downloader and installer.

* This year we won't do a discounted sale of paid support memberships, as that was an utter failure, nor will we beg you into buying such memberships, as we consider the paid support memberships to be yet another business failure. After trying this for over 3 years now, with various tweaks to make it as attractive and easy as possible for our users, we conclude that this will not ever be the way to have a sustainable funding model around Psychtoolbox. In fact, we think nothing that is based on any kind of even partially voluntary financial contributions, not even in exchange for paid support - an actual practical benefit for our users, be it out of decency, or be it due to an actual mid- to long-term thinking ability in our users, will ever work. Carrots do work elsewhere, but they don't work with the vast majority of brain scientists. The income generated through the last year pays for less than ~ 2 months of current operating costs, despite me working absurdly long hours at an unsustainable low salary. It would not even pay for 1 month at a half-way appropriate and long-term sustainable salary. The same story applied for the two years before. Not surprising, given that estimated way less than 1% of all labs contribute. Anyhow, after the carrots come the sticks, but that's something for next year.

Merry christmas and a happy new year! - I'd say it can only get better next year, but ofc. that would be way too optimistic, given how the world evolves.

-mario
