
ATLAS Releases
===============

The ATLAS experiment releases a complete set ofsoftware packages that allow you to conduct research using variaous tools that they provide, that is called a "Release". These Releases are preiodically updated by variaous collaborators making improvements to the packages in the software, these releases are numbered, with the latest stable release being Release 22. Before this came Release 21, which is still widely used by researchers as of May 3rd 2021, since many of the analysis tools are still valid. As time goes on, each group slowly transitions to using the latest release, as they contain the most up to date ATLAS reccomendations for particle objects as well as particle variables that should be used.

Before you conduct any sort of research, you must setup one of these releases on an ATLAS enabled machine or computer cluster. lxplus or the tier2 should work. After you setup this release, you should be able to run simple scripts that will allow you to loop over the data in an AOD (Analysis Object Data) using either a pything script or a c++ script. Bwlos is a good ATLAS resource that helps you setup a release, a version of Release 21 to be specific.

[Setting up a Release](https://atlassoftwaredocs.web.cern.ch/ABtutorial/release_setup/)

You can ignore anything in "Building your own release (optional & advanced)" and after. it is unnecessary to our introduction.




Athena
===============

Athena is one of the main software packages in the Release and is what allows most of the research to be done.
The website below gives a good introduction to what you need to know about it.

[A Guide to Athena](https://atlassoftwaredocs.web.cern.ch/athena/)