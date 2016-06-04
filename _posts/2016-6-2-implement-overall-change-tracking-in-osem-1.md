---
layout: single
title: Implement overall change tracking system in OSEM
tags: [gsoc, fosdem, openSUSE, osem, rails, summer]
author_profile: true
comments: true
---
\\
\\
\\
![Summer of Code](https://www.gnome.org/wp-content/uploads/2016/03/GSoC2016Logo.jpg)  
\\
\\
\\
\\
Hi, I'm Nishanth Vijayan.I'm an undergraduate student at the [Indian Institute of Technology Ropar](http://www.iitrpr.ac.in), India, where I study Computer Science and Engineering.I'm currently in my 4th and final year.You can find me on GitHub @[nishanthvijayan](http://www.github.com/nishanthvijayan) and my IRC nick is the same.I'm an avid tech enthusiast and love all things Geek.

I code mostly in Python, C++ and Ruby and I regularly participate in coding competitions (not so much now). I'm the proud maintainer of [Coder's Calendar](https://github.com/nishanthvijayan/CoderCalendar), an Android app and browser plugins for people interested in competitive programming.Although I've been coding for more than 4 years, I had  never contributed to any open source project other than my own.So when I came to know about Google Summer of Code, the most prestigious open source program for students, I decided to jump in.

At the time, when the list of accepted organizations were released by Google I was learning and building stuff using Ruby on Rails, so I decided to look for interesting projects that uses Rails.And that's how I came across [OSEM](http://osem.io/).Two organizations, FOSDEM and openSUSE, both had cool project ideas on OSEM.
\\
\\
\\
![OSEM](https://camo.githubusercontent.com/a58785e43799dfbdb63f58fbda4336060eb98088/68747470733a2f2f63646e2e6272616e64697374792e636f6d2f696d673f69643d35373066366463333963393932623662363730303030306126666f726d61743d706e6726773d33303026683d3839)
\\
\\
\\
\\
OSEM is an event management app tailored to free software conferences, used by [openSUSE](https://events.opensuse.org/), [ownCloud](https://conference.owncloud.org/) and many other organizations.
\\
The main reasons why I decided to work on OSEM are:  
<ul>
<li>Clean Code that follows conventions (enforced by RuboCop code analyser)  </li>
<li>Simple and straightforward documentation for setting up Dev env </li>
<li>Friendly and helpful community</li>
</ul>
\\
After going through the project idea lists of both FOSDEM and openSUSE, I sent a proposal on FOSDEM's project titled 'Implement overall change tracking system' and it was accepted.
\\
\\
[FOSDEM](http://fosdem.org/) is a free event for software developers to meet, share ideas and collaborate.It is a two-day event organised by volunteers to promote the widespread use of free and open source software.Taking place in the beautiful city of Brussels (Belgium), FOSDEM is widely recognised as the best such conference in Europe.
My mentors [Stella Rouzi (differentreality)](https://github.com/differentreality) and [Richard Hartmann (RichiH)](https://github.com/RichiH) are both part of the FOSDEM team.Stella had participated in GSOC 2014, where she worked on OSEM. 
\\
\\
In simple terms, my project is to track changes various aspects of a conference (events, schedule, call for papers etc), display changes made to these objects and also to take actions related to such changes.
A major part of the project is to implement an interface which displays the previously mentioned changes with options to revert and view the specifcs of each change.This would allow conference organizers and admins to be aware of all changes made and thus have better control over the organization of their conference.
\\
\\
I had worked on a college coursework related project ( also using Rails), where I had implemented a similar changelog page.This experience came in handy as this made me familiar with gems required to implement such a system and this helped me set up a basic version of  such a page easily.
\\
\\
During the past 2 months,I've learned a lot.My Ruby and Rails skills have improved considerably.I learned about tools like Vagrant, Travis, RuboCop and concepts like Code coverage.So I'm looking forward to an awesome summer experience.
\\
\\
I've implemented a basic version of a Changelog/ Revision History page and the code is [under review](https://github.com/openSUSE/osem/pull/1019). This has turned out to be much more complicated that I had imagined when I started coding (my college project had just 5 models that needed to be tracked, OSEM has 40+ :) ).But more on that later..