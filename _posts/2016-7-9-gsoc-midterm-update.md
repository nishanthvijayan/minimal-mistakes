---
layout: single
title: GSOC Midterm Update
tags: [gsoc, fosdem, openSUSE, osem, rails, summer]
author_profile: true
comments: true
read_time: true
share: true
---
\\
\\
\\
![Summer of Code](https://www.gnome.org/wp-content/uploads/2016/03/GSoC2016Logo.jpg)  
\\
\\
<!-- ![OSEM](https://camo.githubusercontent.com/a58785e43799dfbdb63f58fbda4336060eb98088/68747470733a2f2f63646e2e6272616e64697374792e636f6d2f696d673f69643d35373066366463333963393932623662363730303030306126666f726d61743d706e6726773d33303026683d3839) -->
\\
\\
\\
( Hi, I'm Nishanth Vijayan.I'm an undergraduate student at the [Indian Institute of Technology Ropar](http://www.iitrpr.ac.in), India, where I study Computer Science and Engineering.I'm currently in my 4th and final year.You can find me on GitHub @[nishanthvijayan](http://www.github.com/nishanthvijayan) and my IRC nick is the same.I'm an avid tech enthusiast and love all things Geek. )


The Midterm Evaluation of my GSOC project is over, and I passed.
Like I mentioned in my previous post, a major part of my project is to implement a Revision History page in OSEM, which will grant organizers and admins access to the history of changes that were made to a conference, users and their associated resources.

### Why have such a page?
A conference has many associated aspects registrations, events, rooms, tickets, commercials, sponsors etc, all of which can be managed using OSEM. A conference usually has many organizers. The idea here is that one organizers may change some details associated with any of the before mentioned objects and the others have no means of knowing this. Similarly, event submitters may change details (like title, abstract, other needs etc) of their events and there is no means for organizers to be know about these changes other than by manually going over each event in case he wants to know something.
\\
\\
This is where the Revision History page comes to play. A revision history typically displays a list of all such changes with details like who orchestrated the change, when the change occurred etc. This is a common feature found in many  popular apps  (Example: Google Docs ).


<img src="/images/google_docs.png" alt="Google Docs Revision History" style="height: 350px;display: block;margin: 0 auto;"/>
  
### Status
The aim of the first half of the project was to implement a Revision History/Changelog page with the following features:
  <ul>
  <li>Track as many models as possible (OSEM has 40+ :O)</li>
  <li>Display timestamp showing when the change was made</li>
  <li>Changes should be described in a straightforward fashion (as close to proper English as possible)</li>
  <li>Changes should be revertible i.e for each change, the user should be able to restore its associated object to its form before that change.</li>
  </ul>

I've implemented all of the above and have open a pull request. The PR is still undergoing review and will hopefully be merged soon. 
This is the current state of the Revision History page I've implemented.


<img src="/images/revision_history.png" alt="OSEM Revision History" style="display: block;margin: 0 auto;"/>


  - Change tracking has been added to 28 models. Few models have not been tracked as they are expected to be reworked soon
  
  - Organizers can inspect each change to see which attributes of an object have changed and can see the previous value and updated value.
  \\
  \\
    <img src="/images/what_changed.png" alt="OSEM Revision History" style="display: block;margin: 0 auto;"/>
  - Organizers can revert an entire change or  even revert change to a single attribute.
  \\
  For example:In the above image, an organizer (or admin) can revert all 3 of those in one go or revert change to only title (or subtitle or max-attendees).
  \\
  \\
  <img src="/images/revert.png" alt="OSEM Revision History" style="display: block;margin: 0 auto;"/>

### Challenges
Previously, I had implemented a simple version of a Changelog page in a college project using the same gem (paper_trail) that I was planning to use in OSEM.
So when I initially started coding, I was confident that I would be able to complete the feature in a fortnight.Boy, was I wrong!

A large part of the difficulty that I had to face was in trying to describe changes. 28 types of objects meant a lot of cases.

Some objects had title attribute, others had name, some others had neither.
Eg: Event had title, room has name, registration had neither.

Some objects were associated to another type(s) of object.
Eg: A Comment is associated with an event and a user.So is Vote. But a Users_Role object is associated to a user and a role

And then there were objects with polymorphic associations.
Eg: A Commercial object can be a venue's commercial, an event's commercial or the entire conference's commercial

The object under consideration could be a deleted object.Or maybe, it's association could be deleted.
\\
\\
<img src="/images/edge_cases.jpg" alt="Edge Cases" style="display: block;margin: 0 auto;"/>
\\
When describing changes, all these had to be taken into consideration.There was no way to solve this other than by listing out a [lot of specific conditions](https://github.com/nishanthvijayan/osem/blob/0f67ad2df1f0e2d571f98e25dce60c5b8e1f3d7d/app/views/admin/versions/_object_desc_and_link.html.haml) and in some cases grouping object with similar properties together.
For example: [Vote, Event and EventRegistration](https://github.com/nishanthvijayan/osem/blob/0f67ad2df1f0e2d571f98e25dce60c5b8e1f3d7d/app/views/admin/versions/_object_desc_and_link.html.haml#L42) are all similar in that there is an associated user and an event.So, all 3 could be grouped together in code.
TDD is what kept me sane, when adding new models.Every time I start tracking a new model, I would sit and think how I want to describe each type of change to that an object of that class, then write a feature test for it.This finally made me a true believer of TDD. 

### So far, so good
During the course of the first half of the project, I learned many little quirks of Ruby and Rails (mostly Rails). 
Many times during the project I had to go through the source code of paper_trail, the gem I used for tracking changes.I had to do this understand how certain things are implemented under the hood. I remember doing the same when working with paper_trail as part of my college project. But at that time, I was not able to make much sense of it.But this time was different. This was a refreshing experience as it made me realize how my ruby and rails skills have improved over the course of this project.

One big mistake that I made was not making opening a PR early on.Doing so would have helped me to identify style issues and other problems early on. 

During the initial few weeks I used to write tests after implementing some feature and not before.Of course I was familiar with the concept of TDD but was not a firm believer.The last few weeks have been an eye opener in this regard. 



### Next Up
In the next half of the project, I have to implement a set of small features.
Since there are a few features to implement, the challenge now would be to identify and allocate time properly.
It's a difficult job considering how I initially expected to finish my first task in 2 weeks :( .
I've completed the first one and have open a pull request.
It deals with handling canceled events in a conference's schedule.I'll write more about it in my next post.
