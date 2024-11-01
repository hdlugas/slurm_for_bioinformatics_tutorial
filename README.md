# Slurm for Bioinformatics Tutorial

This repository is intended to be a tutorial for implementing common bioinformatics tasks with the job scheduler Slurm on a High-Performance Computing (HPC) cluster. This tutorial may be useful for anybody using Slurm as a job scheduler on an HPC cluster but is created with researchers using Wayne State University's HPC cluster (i.e. WSU's Grid) in mind. Much of the information in this tutorial can be found on WSU's Grid's tutorials page ([https://tech.wayne.edu/kb/high-performance-computing/hpc-tutorials](https://tech.wayne.edu/kb/high-performance-computing/hpc-tutorials)) or by consulting the Slurm documentation ([https://slurm.schedmd.com/documentation.html](https://slurm.schedmd.com/documentation.html)).

## Table of Contents
- [1. Getting Started](#getting-started)
   - [1.1 Create Grid Account](#create-account)
   - [1.2 Logging into the Grid](#logging-in)
      - [1.2.1 Mac OS / Linux](#logging-in-mac-linux)
      - [1.2.2 Windows](#logging-in-windows)
   - [1.3 Navigating in Linux](#navigating)
      - [1.3.1 Linux Shell Prompt](#shell-prompt)

<a name="getting-started"><\a>
## 1. Getting Started
<a name="create-account"><\a>
### 1.1 Create Grid Account
To WSU's HPC cluster, you must first apply for a Grid account which can be done via the "Renew or request Grid account tab" on WSU's HPC homepage ([https://tech.wayne.edu/hpc](https://tech.wayne.edu/hpc)).

<a name="logging-in"></a>
### 1.2 Logging into the Grid
It is recommended to connect to the Grid using ssh (which stands for Secure Shell Protocol) which is a method allowing one to access computers over an unsecured network.
<a name="logging-in-mac-linux"></a>
#### 1.2.1 Mac OS / Linux
If you are using Mac OS X or Linux, open up a terminal window, and run
```
ssh (AccessID)@grid.wayne.edu
```
where (AccessID) is replaced with your own AccessID. For
example, since my AccessID is fy7392, I run the command:
```
ssh fy7392@grid.wayne.edu
```
to connect to the grid. You will then be prompted for your WSU password which is the same password 
you use to log into WSU Academica. You should then be prompted with a QR code and instructions
to set-up Google Authenticator. This will require you download the Google Authenticator app
on a smartphone, tablet, or computer. Once you have installed Google Authenticator and scanned the QR 
code, when you connect to the Grid in the future, you will input your WSU password, press enter, 
and then input your WSU HPC secret token found in your Google Authenticator app.

<a name="logging-in-windows"></a>
#### 1.2.2 Windows
If you are using Windows, download and install the PuTTY ssh client from
([http://www.putty.org/](http://www.putty.org/)) . PuTTY is free and open-source. After running
PuTTY, you set connection type to ssh, and enter grid.wayne.edu for the
hostname; you can leave everything else as default (for example, the default
port number, 22, is the correct one for ssh). After pressing the “Open”
button to open the connection, you will asked for a login/username, and
here you enter your AccessID.

<a name="navigating"></a>
### 1.3 Navigating in Linux
<a name="shell-prompt"></a>
#### 1.3.1 Linux Shell Prompt
Once you are logged into the Grid, you will see a shell prompt like `fy7392@warrior ~]$` except with fy7392 replaced with your AccessID. The shell prompt consists of two primary parts:
  * Node: "warrior" is the name of the node of the server which you are logged into by default when you first log into the Grid. The "warrior" node is not to be used for running heavy computations and is instead used to schedule jobs (which can involve heavy computations) to be run on other nodes. All available nodes can be found on WSU's HPC webpage ([https://tech.wayne.edu/hpc/nodes](https://tech.wayne.edu/hpc/nodes)).
  * Path to current working directory: The tilde symbol ~ refers to your home directory (note that directories and folders are the same thing). The command `pwd` shows you the full path to your current directory (i.e. pwd stands for path to working directory), which is always your home directory by default when you first log in. Note that only you have permission to read, write, and execute all files in your home directory (or subdirectories of your home directory) with perhaps the system administrators of the Grid being the only exceptions. The 2TB of disk space allotted to us in our home directories is typically not enough for working with Next-Generating Sequencing data bioinformaticians work with, and if you are a member of the Biostatistics and Bioinformatics Core here at Karmanos Cancer Institute / WSU, you should create a subdirectory of our BBC's directory /rs/rs_grp_bbc/ for your project. If you do not have the necessary permission to navigate to our BBC directory, please let me know and we will request that you obtain read, write, and execute privileges for our directory. As of November 2024, we have 50TB of disk space allotted to us in our BBC directory. Note that (i) creating and (ii) navigating among directories are covered elsewhere in this tutorial.


