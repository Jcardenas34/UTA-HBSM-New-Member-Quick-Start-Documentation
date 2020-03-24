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
  This Head node, is where you will be doing most of your work, and where you will submit your code to what we call a batch scheduler that will effectively run your code. The Batch schedueler is the program that distributes your job to the rest of the computers connected to the head node, called the compute nodes and tells them to run the script you are writing, there are many types of bactch scheduelers that different clusters use, some popular ones are "Slurm", named after the famous drink in futurama, Condor which is used by the lxplus cluster that CERN uses and PBS (Portable Batch Schedueler) which we use on the tier3. Each one of these batch scheduelers has a set of commands you can type to give you information on the current jobs that are runnning on the cluster as well as commands that will submit your code to the cluster such as "qsub". BUT, In order to make the compute nodes process your code, instead of typing out 
```
qsub script_you_want_to_run.suffix 
```
where suffix can be anything from .py to .cxx, you must create what we call a submission script. This is a script with a siffix of ".sub" that lets the batch schedueler know how many processors you want to use, as well as how much RAM and compute time you need. and also contains all of the commands that you want the compute nodes to execute. There will be an example of how to write a basic submission script as well as links to the documentation on all the possible options in a section below. From here it is important to know, that __any code submittted to the cluster via a batch script is called a Job__
  
As of now, the tier-3 cluster is contained in one rack in CPB 115. This is the machine room where the tier-2 system we operate for ATLAS is located. By comparison the tier-2 system occupies 27 racks.

The Compute nodes
========================
The compute nodes are what do all of the computation in your script, and they are all connected to the head node via the batch schedueler, which as I said above determines via a submission script how many compute nodes will process your code and many other computing resources are needed.


The Batch Script
==========================
We create batch scripts so that we can submit our code to the cluster, this is to allow the head node of the tier3 to run as smoothly as possible with no connection lag to any user on the cluster. Once the script is made, you would submit it to the cluster by typing
```
qsub name_of_batch_script.pbs
```

So lets learn how to make this script, using that basic histogram making file we worked on.


A very basic example looks like this

```
#~!/bin/bash
#PBS -l qos=hep                        
#PBS -M juan.cardenas@mavs.uta.edu
#PBS -m abe
#PBS -e /cluster/home/jcardenas34/qualification_task/HDF_dir/
#PBS -o /cluster/home/jcardenas34/qualification_task/HDF_dir
#PBS -j oe   
#PBS -l walltime=72:00:00

athDerivation
cd /cluster/home/jcardenas34/new_group_member_introduction/
python Intro_root_histogram_maker.py

```

So what do the #PBS lines and the rest mean?

```
#~!/bin/bash                     
#PBS -M juan.cardenas@mavs.uta.edu
#PBS -m abe
#PBS -e /cluster/home/jcardenas34/qualification_task/
#PBS -o /cluster/home/jcardenas34/qualification_task/
#PBS -j oe   
#PBS -l walltime=72:00:00
#PBS -l qos=hep
```
These lines that start with #PBS tell the batch scheuduler certian directions on what to do and so they are called directives. Lets go line by line.

~!/bin/bash
1. Says that we want to run this script in the terminal

PBS -M juan.cardenas@mavs.uta.edu
2. Allows you to be notified via email when your job is completed

PBS -m abe
3. Sets the conditions under which an email should be sent, here abe stand for send an email when the job is (borted,begins,terminates)

PBS -e /cluster/home/jcardenas34/qualification_task/
4. PBS creates an error and an output log file where the output and error messages given by your job are stored, name a path if you want to send this error to a specific place, otherwise it is created after the job is done, in the directory you submitted the job in.

PBS -o /cluster/home/jcardenas34/qualification_task/
5. Same as above, where but where the output file is sent

PBS -j oe
6. __Very important__, each time a job is completed, 2 log files are made, if a lot of job files are submitted, youll get a lot of log files, and it will quickly become a lot to sort through. so the -j option joins the error and output files together. You must also specify that you want to merge them by typing o and e together after -j

PBS -l walltime=72:00:00
7. __Also extremely important__, if not the most important, this is the estimated time you expect your job to finish in
The format is in hrs:min:secs and if your job exceeds the amount of time you entered, your job is immedeately terminated.
There is a current maximum time allowed for a job to run on each queue, on the "hep" queue this is 96:00:00
and you can check the rest using qstat -q

PBS -l qos=hep
8. Tells the batch schedueler which queue you want to run on, the main reason for this is to allow more or less time for your job to run.



Now for what you actually want to run, your code

```
athDerivation
cd /cluster/home/jcardenas34/new_group_member_introduction/
python Intro_root_histogram_maker.py
```

Commands that you want to execute on the compute nodes go right after all the #PBS directive lines. Anything after the #PBS lines will run as if you are running it on a regular terminal, so put any lines here that you would need to type in order to run your script. Youll notice that "athDerivation" is there since it is necessary to run this particular script. But any lines you plan to run should be here, from lines that you can type in the termainal like "cd" and "touch" or running code thats already in a script with python or another language.


These instrucitons imply that you have created a new file "qsub" that you will call, "name_of_script_you_want_to_submit_to_cluster.qsub", by using the "touch" command in the [terminal](coding.md) section, and added similar lines to the ones above with your text editor.



The Queue
================
Lets say that youve submitted a job to the check its running status using "qstat", this is a command for the batch schedueler that lets you view all of the jobs currently running on the cluster. Typing "qstat" should either show nothing, because noone is running anything on the cluster, or it should look something 
like this.

```
Job id                    Name             User            Time Use S Queue
------------------------- ---------------- --------------- -------- - -----
1441291.master             ...1p1n_Test.sub jcardenas34     01:16:05 R hep 

```



You can add modifiers to the qstat command to let it give you more information, like which node your code was sent to, and how long its been running using what we call flag modifiers at the end of qstat like so, there are many others in the reference documents below


```
# This shows a rather lengthy but full description of all jobs that have been sent to the cluster
qstat -f 
```

You can also remove a job from the queue if you made a mistake by typing qdel and the jobid of the job you want to 
remove, for example, lets say I wanted to remove the job above from the queue, id do

```
qdel 1441291
```

There are many more possible commands in teh documentation below.


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

These instructions work on a *mac*, but if you have some sort of linux based command line terminal installed on your computer, is should work just the same. For windows you can either use "commander" or "git terminal" or "ubuntu bash shell", I will add more on how to install this in the [Accelerating your workflow](cyberduck.md) part of the page later.

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







