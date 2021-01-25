Grid Certificates
=====================

A grid certificate is a piece of information that will allow you to access the GRID for certain tasks, 
like downloading files or submitting jobs to their computing resources. These Grid certificates expeire on a yearly basis and you should 
renew them when you get the reminder from the CERN secretariate to renew. You are allowed to keep more than
one grid certificate without them interfering. Just go to this website and type in your credentials.
https://ca.cern.ch/ca/

and click on "New Grid User Certificate", this should forward you to a page where you will be asked to log in, after which you must enter your password
to either create a new grid certifiate, or renew an old one. Createing a new one, and renewing an old one basically do the same job.

You should then install this certificate to your browser. For Google Chrome go to settings and then search "Manage Certificates" and 
import the Grid Certificate that should be named "myCertificate.p12" and import that.

Once you have this certificate in your downloads folder, scp that p12 file to the cluster which you will be using to dowload files with, or submit jobs from.

once scped to the cluster of your choice log into that cluster, and you should see the myCertificate.p12 file in your home directory. Type these coomands in
to use the grid certificate.

'''
openssl pkcs12 -in [your-cert-file] -clcerts -nokeys -out ~/.globus/usercert.pem
openssl pkcs12 -in [your-cert-file] -nocerts -out ~/.globus/userkey.pem
'''
followed by

'''
chmod 0600 ~/.globus/usercert.pem
chmod 0400 ~/.globus/userkey.pem
'''

The same, but more detailed version of the process above is outlined here.

https://www.racf.bnl.gov/docs/howto/grid/installcert

Once you have run the lines of code above, you can test out if the certificate is working by typing

lsetup rucio
and then setting up a proxy as instructed by lsetup.

