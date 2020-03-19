# The Tier3: The High Energy Physics (HEP) Cluster

![cluster](/docs/img/Servers.jpeg)  

If you stay in the computing world it is more than likely youll run into a situation where youll have to use a computer cluster. These computer clusters are used when you have a piece of code that requires a lot of computing resources such as the need to run on multiple processors or requires much more RAM than one computer can provide. A lot of the time in 
High Energy Physics we create such pieces of code. The computing cluster that we have access to in the High Energy Physics (HEP) department is called the Tier3. It is part of 3 clusters associated with the LHC (Tier1, tier2, and Tier3), and certian universities host them, we are one of them. The tier3 is what does all the computation for analysis, the others have other dedicated processes. There are other computing clusters that CERN uses, such as the GRID and lxplus, but from day to day since the tier3 is located on campus, you will be using this most of the time.  

In general the way that clusters are structured is as such, 

The Head node
========================
This is the computer that you or any person who wants to access the cluster logs into via "ssh". If you have not logged into the tier3 yet, you will have to contact the cluster manager at UTA who will create an account for you and instructions on
how to log in. Here is the basic command that you will use to login

```
ssh -X <user_name>@master.tier3-ATLAS.uta.edu
```

This node is where you will be doing most of your work, here you will submit your code to be processed using what we call a 
batch scheduler, this is the program that distributes your job to the rest of the computers connected to the head node, called the compute node.

The Compute nodes
========================
and where you will submit your scripts to be processed by the second kind of node, the compute nodes.
