---
layout: page
title: Psychtoolbox Forum
category: getting-help
---

The Psychtoolbox user community is quite active. The forum has ca. 2,000
subscribers and around 4 messages are posted a day. 

![Histogram of forum postings](http://chart.apis.google.com/chart?chxr=0,0,2000%7C1,2000,2012&chbh=a&chco=A2C180&chd=t:327,398,988,539,771,1084,1498,1911,1439,1524,1219,1614,808&chds=0,2000&chs=500x100&cht=bvg&chts=676767,13.5&chtt=Forum+posts+per+year&chxs=1,676767,10,0,lt,676767&chxt=y,x)

*Please help other PTB users on the forum*. 

### How to use the forum - A quick primer

Read below how you can assist us in helping you effectively ...

> If you need an example on how to achieve specific tasks, please take a look
> at our demos in the [`Psychtoolbox/PsychDemos`][docs-demos] folder. If you
> are a new to Psychtoolbox, make sure to read the introductory PDF file in the
> [`Psychtoolbox/PsychDocumentation`][docs-documentation] folder. 
> 
> Also see [docs.psychtoolbox.org](http://docs.psychtoolbox.org) or type `>>
> help Psychtoolbox` to read our online help.
> 
> Please try to find out if similar questions have been asked before.
> 
> **If you still have a question**, try posting it on the forum.  Bug reports and
> feature requests can be posted on the forum. When you post a question, try to
> include all relevant information 
> 
> - Output of `>> PsychtoolboxVersion`
> - Which platform (Mac OS X, Windows XP/Vista/7, Linux, ...) 
> - A minimal code snippet that exhibits the bug you found
> - Warnings and Errors that were printed to the console (please read them carefully)
> - Hardware setup and relevant driver versions
> 
> We appreciate it when you **sign with your name and affiliation**.
> 
> The document [»How To Report Bugs Effectively«](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html) is a great
> guide on how to report a potential bug in an effective way. **Please read it!**
> 
> The document [»How To Ask Questions The Smart Way«](http://www.catb.org/~esr/faqs/smart-questions.html) also contains
> lots of good tips on how to behave on community-run support channels. 
> 
> **If you notice a particularly helpful answer on the forum**, we will all be
> grateful if you would copy it to the [FAQ section](faq) on our Wiki to preserve it for posterity.  You may want to
> edit it down to the relevant bits. With time we will incorporate and cross-reference these texts elsewhere in the
> project.
{: #notice style="display:none"}

<p style="display:inline;">
<span id="readmore" role="button" onclick="toggleDiv();">
   Expand this notice »
</span>
</p>

  [docs-demos]: http://docs.psychtoolbox.org/PsychDemos
  [docs-documentation]: http://docs.psychtoolbox.org/PsychDocumentation


<!-- Google Groups iframe -->
<iframe id="forum_embed"
  src="javascript:void(0)"
  scrolling="no"
  frameborder="0"
  width="900"
  height="700">
</iframe>
<script type="text/javascript">
  document.getElementById('forum_embed').src =
     'https://groups.google.com/forum/embed/?place=forum/psychtoolbox-discuss'
     + '&showsearch=true&showpopout=true&showtabs=false'
     + '&parenturl=' + encodeURIComponent(window.location.href);
</script>
<script>
function toggleDiv(){
    if (document.getElementById('notice').style.display == 'none') {
        document.getElementById('notice').style.display = 'block';
        document.getElementById('readmore').style.display = 'inline';
        document.getElementById('readmore').innerText = 'Collapse this notice «';
    } else {
        document.getElementById('notice').style.display = 'none';
        document.getElementById('readmore').style.display = 'inline';
        document.getElementById('readmore').innerText = 'Expand this notice »';
    }
}
</script>
