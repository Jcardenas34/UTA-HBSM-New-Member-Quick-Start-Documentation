# The Tier3: The High Energy Physics (HEP) Cluster

![cluster](img/servers.jpeg)  

  If you stay in the computing world it is more than likely youll run into a situation where youll have to use a computer cluster. These computer clusters are used when you have a piece of code that requires a lot of computing resources such as the need to run on multiple processors or requires much more RAM than one computer can provide. A lot of the time in 
High Energy Physics we create such pieces of code. The computing cluster that we have access to in the High Energy Physics (HEP) department is called the Tier3. It is part of 3 clusters associated with the LHC (Tier1, tier2, and Tier3), and certian universities host them, we are one of them. The tier3 is what does all the computation for analysis, the others have other dedicated processes. There are other computing clusters that CERN uses, such as the GRID and lxplus, but from day to day since the tier3 is located on campus, you will be using this most of the time.  

In general the way that clusters are structured is as such, 

The Head node
========================
  This is the computer that you or any person who wants to access the cluster logs into via "ssh". If you have not logged into the tier3 yet, you will have to contact the cluster manager at UTA, at the time of writing this is 
```
Mark Sosebee:
sosebee@exchange.uta.edu
```
who will create an account for you and give you instructions on how to log in. Here is the basic command that you will use at your command line to login to the tier3
```
ssh -X <user_name>@master.tier3-ATLAS.uta.edu
```
  This Head node, is where you will be doing most of your work, and where you will submit your code to what we call a batch scheduler that will effectively run your code. The Batch schedueler is the program that distributes your job to the rest of the computers connected to the head node, called the compute nodes and tells them to run the script you are writing, there are many types of bactch scheduelers that different clusters use, some popular ones are "Slurm", named after the famous drink in futurama, Condor which is used by the lxplus cluster that CERN uses and PBS (Portable Batch Schedueler) which we use on the tier3. Each one of these batch scheduelers has a set of commands you can type to give you information on the current jobs that are runnning on the cluster as well as commands that will submit your code to the cluster such as "qsub". BUT, In order to make the compute nodes process your code, instead of typing out "qsub script_you_want_to_run.suffix" where suffix can be anything from .py to .cxx, you must create what we call a submission script. This is a script with a siffix of ".sub" that lets the batch schedueler know how many processors you want to use, as well as how much RAM and compute time you need. and also contains all of the commands that you want the compute nodes to execute. There will be an example of how to write a basic submission script as well as links to the documentation on all the possible options in a section below.
  
As of now, the tier-3 cluster is contained in one rack in CPB 115. This is the machine room where the tier-2 system we operate for ATLAS is located. By comparison the tier-2 system occupies 27 racks.

The Compute nodes
========================
The compute nodes are what do all of the computation in your script, and they are all connected to the head node via the batch schedueler, which as I said above determines via a submission script how many compute nodes will process your code and many other computing resources are needed.


The Batch Script
==========================


Reference Documents
==========================

There exists user documentation and a reference guide on how to use the pbs batch system, linked below

[User Guide](https://www.pbsworks.com/pdfs/PBSUserGuide18.2.pdf) for PBS

[Reference guide](https://www.pbsworks.com/pdfs/PBSRefGuide18.2.pdf) for PBS


The user guide is a more comprehensive document that teaches you about most of the aspects of the PBS (Portable batch system),
the reference guide is more of a summary of all possible commands that you can input, both in the PBS script and in the command prompt


How to make a Tier3 not timeout
===================================

So at the time of writing, the tier3 has an annoying feature where it disconnects your login session in the terminal
after a few minutes of inactivity. This is particularly annoying when you have to ssh into multiple clusters, and must
leave the tier3 terminal inactive for a while, but will return to it later. When you return, you see that the termial is now inactive, and you must log in again, and navigate to where you were previously. Luckily, there are a few changes you can make in your ssh_config script that will help you extend the time before timeout.

These instructions work on a *mac*, but if you have some sort of linux based command line terminal installed on your computer, is should work just the same. For windows you can either use "commander" or "git terminal" or "ubuntu bash shell", I will add more on how to install this in the [Accelerating your workflow](docs/cyberduck.md) part of the page later.

When you first open your terminal, you will be logged into the home directory of your personal computer. You will want to open this file with whatever text editor you prefer.

```
/etc/ssh/ssh_config
```

by typing, *either, emacs, sublime, nano, vim, atom* or your preferred text editor name, and then the line above.

This is a file that tells the command prompt how to insteract with any computer that you choose to ssh into, weather that be the tier3 or another cluster somewhere else.

All of the lines in this file should be commented out, except for a small section near the bottom of the page. which should look like this.

```
Host *
	SendEnv LANG LC_*
```
 
 you want to add a few lines to it so that It looks like this
 
 ```
 Host *
	SendEnv LANG LC_*
	ServerAliveInterval 120
	ServerAliveCountMax 720
 ```
and save the changes. The firstaddition we made makes it so a blank message is sent to the server every 120 seconds in order to keep the connection, the second line we added makes it so that it will log you off if this is done 720 times, 
so 720 x 120 seconds = 24 hours, you can adjust this second number to 30 for one hour tuntil timeout, or to 60 for 2 hours of sustained login during 2 hours of inactivity.







