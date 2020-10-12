#Getting started on the tier3

After you are able to log into the tier3 with a username and password that Mark Sosebee, our current cluster technician has provided to you.
It is now time to setup your computing environment so that you can get to work, using root and any other ATLAS related tools.


You want to begin by logging in, and opening up and editing a hidden file in your home directory called ".bash profile" this file will not be immedeately visible 
when using the "ls" command, but will be visible using the "ls -a" command in the terminal. Any file with a period before its name is treated as a "hidden file" by
bash, and will not appear with a simple "ls". Here are the commands that you want to type out.

```
#This command brings you back to the home directory is youre not already in it
cd

emacs .bash_profile
```

Alternatively, If you are already familiar with how to use Cyberduck or Filezilla, you can open this file using those programs
so that it is editable using your preferred text editor but the basic instructions to seutp a release are here
https://atlassoftwaredocs.web.cern.ch/ABtutorial/release_setup/

```
export ATLAS_LOCAL_ROOT_BASE=/cvmfs/atlas.cern.ch/repo/ATLASLocalRootBase
alias setupATLAS='source ${ATLAS_LOCAL_ROOT_BASE}/user/atlasLocalSetup.sh'
setupATLAS
```


follow the instructions on the link unitl you get to here

```
cd build/
asetup 21.2.6,AnalysisBase
cmake ../source/
make
```
you might have noticed that I have changed 125 to a 6, this is because our tier3 cluster does not have asetup 21.2.125 available to it,
and so it is unable to setup it up. once you have changed 125 to 6, everything should run smoothly. And you should be able to 
have root run over DAOD files



