# Slurm for Bioinformatics Tutorial

This repository is intended to be a tutorial for implementing common bioinformatics tasks with the job scheduler Slurm on a High-Performance Computing (HPC) cluster. This tutorial may be useful for anybody using Slurm as a job scheduler on an HPC cluster but is created with researchers using Wayne State University's HPC cluster (i.e. WSU's Grid) in mind. Much of the information in this tutorial can be found on WSU's Grid's tutorials page ([https://tech.wayne.edu/kb/high-performance-computing/hpc-tutorials](https://tech.wayne.edu/kb/high-performance-computing/hpc-tutorials)) or by consulting the Slurm documentation ([https://slurm.schedmd.com/documentation.html](https://slurm.schedmd.com/documentation.html)).


<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*
- [Getting Started](#getting_started)
   - [Create Grid Account](#create_account)
   - [Logging into the Grid](#loggin_in)
      - [Mac OS / Linux](#logging_in_mac_linux)
      - [Windows](#logging_in_windows)
   - [Navigating in Linux](#navigating)
<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Getting Started
### Create Grid Account
To WSU's HPC cluster, you must first apply for a Grid account which can be done via the "Renew or request Grid account tab" on WSU's HPC homepage ([https://tech.wayne.edu/hpc](https://tech.wayne.edu/hpc)).

### Logging into the Grid
It is recommended to connect to the Grid using ssh (which stands for Secure Shell Protocol) which is a method allowing one to access computers over an unsecured network.
#### Mac OS / Linux
If you are using Mac OS X or Linux, open up a terminal window 1 , and run
ssh (your AccessID)@grid.wayne.edu
where of course you replace (your AccessID) with your own AccessID. For
example, since my AccessID is fy7392, I type “ssh fy7392@grid.wayne.edu”
to log into the grid. You will then be prompted for your password; here you
use the same password you always use to log into Academica or Blackboard.
You may 2 then have to go through the “two-factor authentication” process:
you can opt for a text message to be sent to your cellphone, or to get an
automated phone call. Either way, the phone number you have on file in
WSU’s records will be used.

#### Windows
If you are using Windows, download and install the PuTTY ssh client from
([http://www.putty.org/](http://www.putty.org/)) . PuTTY is free and open-source. After running
PuTTY, you set connection type to ssh, and enter grid.wayne.edu for the
hostname; you can leave everything else as default (for example, the default
port number, 22, is the correct one for ssh). After pressing the “Open”
button to open the connection, you will asked for a login/username, and
here you enter your AccessID.

### Navigating in Linux
hellow orld













