# SSH

Docs on using ssh to access the Appropedia VPS.

We should only allow login using ssh with keys (not passwords).

## To set up an ssh key for someone (eg. a new techie)

1. Get them to send you their SSH public key, which should look vaguely like 
this:

ssh-dss AAAAB3NzaC1kc3MAAACBANbC85TPbHuDjZiQsGw+sWvBmi0nWn8xrbBG1RvqZ0hR1kDvk+FmGLYbQr5IbAHUsX8uN30yJkPJJ9rpsqhA8sQ4uowMLyHiim8y2g6SpBhbrqPTjACyj+IAZHc3awUjKujVtXQJL19W85iIvoZU/g5xV0IJTKcexGga0VopYeO1AAAAFQDGmslBCEvRlcJkGy2WwKygw1s83QAAAIEAiVsH8WTga5MgFWQMDZp+dV3tPqNJcGhbzz8+SfQ7VDUjNmCY2yKJZ756Ie1c3DvwPffJGW2uC/tnIqlTrEy7sHtlqwL7BzeK4wIfE04r2BaX1HWE8V9sD+1F1gl4f4VFn2w5wyylk+NSGYVwPHrzmFKbRs2Ct1IyXxKwHXkpM48AAACAYc9p3chAv+xkSxz3wDIc5Mga9RGczUPTe+A6hgMif0lKc6XfVLs6Hj0RwHAL4YOwnlQgScUZqYqtkY8qdEcv7LSWiuxf/tMWparPdJIWe+sP275CwkjPzvFebKXy2U/jivcGAYUdjqYl5Ap8uROyd+f0D2s4FuT6fI+EIVGVBwQ= skud@Watson 

(It might say different things at the start and end, but you're looking for a 
few lines of gibberish with a user@host at the end of it.)

2. Add this key to .ssh/authorized_keys2

3. The person should now be able to ssh into the appropedia account using 
their key, not the account's password.

## If they don't yet have a key

You should probably be dubious of a tech person who doesn't have an SSH key to login to the VPS and
doesn't know how to create one for themselves.  But assuming you have good reasons for wanting them to be
able to login, then tell them to do the following (copy and paste if you like).

* From the Unix command line, "ssh-keygen".  Default options are fine.  
* Choose a passphrase of some kind (don't leave it blank).
* Two files will be saved:

    .ssh/id_dsa 		Your private key - DO NOT SHARE THIS
    .ssh/id_dsa.pub		Your public key -- provide this to use as above

On Windows: use putty.exe, and google for "create ssh key with putty" or 
similar. Though I'd be surprised if a Windows user were doing tech work
here.
