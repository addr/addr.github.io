---
layout: page
title: Projects
permalink: /projects/
---
### [Touch Level Model](https://en.wikipedia.org/wiki/Keystroke-level_model#Adaptions)
So when I was working on my Software Engineering Master's degree, my focus and primary interest was (and still is) Human Computer Interaction (HCI). There is an area of HCI research that focuses on quantitative aspects of HCI... think things like how long it takes someone to complete a task, how many discrete actions she has to perform within an interface, and so on. And within HCI research there is a classic book called *The Psychology of Human Computer Interaction* which had some pretty groundbreaking stuff, but for quantitative HCI people, it introduced the [Keystroke Level Model](https://en.wikipedia.org/wiki/Keystroke-level_model).

KLM is probably the most well known 'practical' quantitative modeling and evaluation tool, as it was intended as a tool for UX professionals that would allow them to estimate the total time it would take users to complete a given task within an interface. It works like this:

1. A designer would list out **discrete, atomic** actions the user would take to accomplish a task in an interface, usually as part of the design phase. Example, if we were creating a model to open a new word processing document: move mouse to icon on desktop, click icon on desktop to open program, move mouse to file menu, click file menu, move mouse to 'New File', click 'New File'. You'll notice there are a certain set of discrete actions in that task, specifically: moving and clicking. (This is a bit oversimplified for the example, but this is the gist)
2. The designer could then look to the benchmarks in the KLM model that the authors dervied from observing users, and apply a time estimate for each one of those discrete actions in the model. Then, by adding up the total time for every single discrete, atomic action, a designer could get a pretty accurate estimate for how long it would take a user to accomplish a task in the interface. 

But, KLM was introduced in the 80's, just as the personal computer was taking off. All of the benchmarks assumed a traditional PC interface with keyboard and mouse. With the explosion of mobile touchscreen devices, a new interaction paradigm emerged that the authors of the original KLM couldn't anticipate. So my contribution was: why not take the original KLM model and update it with new benchmarks for mobile touchscreens? So I did exactly that. [The first paper](https://dl.acm.org/citation.cfm?id=2638532) introduced this concept.

Since then, I've performed a user study with 36 subjects to actually measure these benchmarks. We haven't published the full results yet (paper writing is in process), but these are forthcoming, hopefully by Summer 2016. For a bit more background on quantitative modeling for touchscreens, [check out this UX stack exchange question](https://ux.stackexchange.com/questions/85760/what-is-tlm-touch-level-model).

### [100 Mobile Apps in 100 Days](https://github.com/addr/100apps)
I'm in the process of creating 100 mobile apps in 100 days, including requirements (user stories), UI design (hand drawn mockups), and development. Why? Up to now, all my mobile development has been in cross-platform tools (I've used both PhoneGap and Appcelerator). While those are great tools for certain use cases, I found myself constantly hitting a wall with each of those tools' limitations, and I wondered: why not just learn native? So that's what I'm doing. The plan is for all of these to be written in Swift, but I may try some [React Native](https://facebook.github.io/react-native/) down the line.

Secondly, I've tried learning this stuff the old-fashioned way (read a book, try and digest the concepts, type in some code they give you, ???, profit), but it just doesn't work for me. I learn way better when I have a problem I'm trying to solve. And if I restrict myself to a single app a day I avoid taking on too much complexity all at once, and I allow myself to room to wrestle with problems and find the solutions.

### [UGA Mobile App](http://eits.uga.edu/web_and_applications/mobileapps/)
My day job is working for the University of Georgia making cool stuff that helps (mostly) students. Right now, I'm working on a complete UX redesign of the official UGA mobile app, starting from the very beginning. The app had evolved through the years from a toy project, going through many hands, none of which had any experience designing usable mobile experiences. So I'm helping the team go through the entire design process, starting with user research, prototyping, and iterative design with testing. The old app was based on a cross-platform mobile development tool called Appcelerator, but we're going fully native for iOS and Android.

### [andydrice.com](https://github.com/addr/addr.github.io)
This site is a simple static site generated with Jekyll, styling with SASS and hosted with Github Pages. I'm mainly focused on writing more, exploring any ideas I have, and tweaking this theme to explore UX ideas.





