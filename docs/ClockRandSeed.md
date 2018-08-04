# [ClockRandSeed](ClockRandSeed)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

[seed,whichGen] = [ClockRandSeed](ClockRandSeed)([seed],[whichGen])  
[ClockRandSeed](ClockRandSeed) seeds the random number from the time-of-day clock or another  
"random enough" random source, e.g., high resolution time, or a true  
random number source. If 'seed' is passed this is used instead of a  
random source or clock time.  
  
'whichGen' optionally allows selection of the random number generator.  
If omitted, the recommended Mersenne-Twister will be used on both  
Matlab and Octave.  
  
If supported, the rng() function will be used, with rng('shuffle') if  
'seed' is omitted. Otherwise the old rand()/randn() setup method is  
used, with 'reset' on Octave for truly random init from /dev/urandom  
or high resolution clock time. On Matlab the old seed = fix(1e6\*sum(clock))  
will be used.  
  
NOTE: There is a page in the 2017 Matlab docs describing the issues around  
random number generator selection and seeding. Type "help rand" and then  
follow to the note on "[Replace](Replace) Discouraged Syntaxes of rand and randn" that  
is at the end of the Description section.  
  
### For reseeding on old Matlab versions, note the following:  
  
The multiplier 1e6 in fix(1e6\*sum(clock)) is bigger than the 100  
suggested by Mathworks (see help RAND). They suggest 100\*sum(clock), but  
this would only change the seed once every 1/100 sec, which might  
correspond to many iterations of a loop. With the bigger multiplier it's  
pretty sure (depending only on clock grain) that two successive calls  
will generate different seeds.  
  
Also unlike the Mathworks suggestion (see help RAND), we call FIX. This  
has no effect on RAND and RANDN, but makes it easier to correctly print  
the seed to a file. When a random seed generates an interesting result  
one would like to be able to recreate the conditions that generated the  
run. If the seed 1e6\*sum(clock) is printed to a file, '%.0f' will often  
round it differently than RAND would.  
  
See also: rng, rand, randn.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/ClockRandSeed.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/ClockRandSeed.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/ClockRandSeed.m</code>
</div>

