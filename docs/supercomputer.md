# The GPU Cluster

There exists another cluster on campus that is different from the tier3. It is a GPU super computer 
managed by Dr.Farbin here at UTA. This cluster is similar to the tier3, but instead of having compute nodes that
have many CPUs the nodes on the super computer host multiple GPUs (Graphical Processing units) that are capable of 
executing many tasks in parallel. The general purpose for a GPU cluster is to do work in training machine learning algorithms
such as the ones found in Neural networks. With Dr. Farbin's permission, and if you begin to do work with neural networks,
you will find this cluster to be extremely useful. 

You will need to email Dr.Farbin at 
```
afarbin@uta.edu
```
for him to give you an account on the supercomputer, but once you have all 
the login information you should be able to access the computer by ssh-ing into it with the command below

```
ssh -X <user_name>@orodruin.uta.edu
```

The Head node
==================
The head node, just like the head node on the tier3, is where you will be doing most of your work.
Similar to ther tier3, the head node on the super computer does have some GPU resources, it has
4 GeForce GTX 1080 GPUs that can be used to test short scripts, although it is discouraged to run very
large and computing intensive pieces of code on it, since it will interfere with others trying to login in
or test thier scripts. It is best practice to submit your code via the the PBS batch schedueler like on the tier3
or log into the compute node directly and submit your code ro be run.


GPU compute nodes
===================== 

The super computer has 4 GPU compute nodes and 1 ordinary CPU node, which can be accessed once you have
logged into the main node as indicated above. Thier names are

The Count, which has 10 TITAN X (Pascal) GPUs for use
```
ssh thecount
```

Thing One, has 4 GeForce GTX 1080 GPUs and together are just as powerful as the 10 GPUs on the count.
```
ssh thingone
```

Thing Two, which also has 4 GeForce GTX 1080 GPUs
```
ssh thingtwo
```






