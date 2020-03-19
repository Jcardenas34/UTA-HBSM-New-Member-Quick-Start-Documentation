# Getting Started with Github

![github logo](img/github-logo.png)

Git hub, is a place for you to store your code on a free online cloud server, as well as provides a way for multiple people
to work on the same piece of code simultaneously, similar to a google doc if youve ever used one. 

Lots of groups in ATLAS use Github because they have lots of members that need to work towards completing a single large project. Lets say that there is a big project that needs to be worked on, such as creating a software that will use neural networks to distinguish between physics objects and plot thier performance. Here we can see 2 major tasks, we need someone to design these neural networks and another to create the software to plot how well they are doing.

It would be very difficuly for person or a single team of people to work on both aspects, given that they are both sufficiently complicated. So it would be useful to separate the project into pieces, so that one group works on creating and optimizing the neural networks and the other focuses on creating the software to plot the performance of these networks once they are up and running.

In the end though, all components of the project have to be merged together to give you a final working product that does calculation and produces plots all at once. This is where github becomes useful, as it provides the ability for multiple users to copy the initial master branch of code, make thier changes and contributions, and then push it back to the "master branch" to be reviewed by team mates and finally merged with the final product. 

Each person in a team would create a copy of the code they will work on (called a fork) and put it on thier computer. They would then work on thier dedicated aspect locally and when significant changes have been made, they "push" thier code back to the github website for review by thier teammates. If thier teammates like the changes/ contributions, the team lead can choose to merge the contribution to the master project called the master branch.

Backups
================

Another great aspect of Git hub is that it can work as a place to store a backup of your code, so that if a project that you
are working on is stored on a cluster that goes down (becomes unusable for a period of time), which they very often do, you still have access to your code and can copy or (git clone) your work to another computer or cluster to continue working.

I cannot tell you how many times either the tier3 or GPU cluster went down and I was forced to rewrite major pieces of my code or wait until the cluster went back online, which sometimes can be weeks, depending on what caused the issue.



So thats it for an introduction, I think this video series is pretty good at explaining what Git and Github is 
and how to use it. [Learn Git/Github here](https://www.youtube.com/watch?v=3RjQznt-8kE&list=PL4cUxeGkcC9goXbgTDQ0n_4TBzOO0ocPR)

GitLab
============
There also exists another more comprehensive version of GitHub called GitLab, that is used to larger collaborations
and besides having a cooler logo, it has expanded functionality that comes in handy when working with larger groups of people. ATLAS and other collaborations in the LCH use GitLab instead of Git hub because of its features, while we as a smaller group at UTA would more than likely use a github page to store all our code and collaborate, it is important to know of the existance of GitLab for when you eventually have to use it as part of a collaboration wide project.



