# Slurm for Bioinformatics Tutorial

This repository is intended to be a tutorial for implementing common bioinformatics tasks with the job scheduler Slurm on a High-Performance Computing (HPC) cluster. This tutorial may be useful for anybody using Slurm as a job scheduler on an HPC cluster but is created with researchers using Wayne State University's HPC cluster (i.e. WSU's Grid) in mind. Much of the information in this tutorial can be found on WSU's Grid's tutorials page ([https://tech.wayne.edu/kb/high-performance-computing/hpc-tutorials](https://tech.wayne.edu/kb/high-performance-computing/hpc-tutorials)) or by consulting the Slurm documentation ([https://slurm.schedmd.com/documentation.html](https://slurm.schedmd.com/documentation.html)).

## Table of Contents
- [1. Getting Started](#getting-started)
   - [1.1 Create Grid Account](#create-account)
   - [1.2 Logging into the Grid](#logging-in)
      - [1.2.1 Mac OS / Linux](#logging-in-mac-linux)
      - [1.2.2 Windows](#logging-in-windows)
   - [1.3 Linux Command Line Interface (CLI) Basics](#basics)
      - [1.3.1 Linux Shell Prompt](#shell-prompt)
      - [1.3.2 Navigating, Creating, and Removing Directories](#navigating)
      - [1.3.3 Creating and Editing Files](#editing)
      - [1.3.4 Asterisk Symbol](#asterisk)
      - [1.3.5 View Disk Space Usage](#disk-space)
      - [1.3.6 Grep](#grep)
      - [1.3.7 Pipe, >, and >> Operators](#operators)


<a name="getting-started"></a>
## 1. Getting Started
<a name="create-account"></a>
### 1.1 Create Grid Account
To WSU's HPC cluster, you must first apply for a Grid account which can be done via the "Renew or request Grid account tab" on WSU's HPC homepage ([https://tech.wayne.edu/hpc](https://tech.wayne.edu/hpc)).

<a name="logging-in"></a>
### 1.2 Logging into the Grid
It is recommended to connect to the Grid using ssh (which stands for Secure Shell Protocol) which is a method allowing one to access computers over an unsecured network.
<a name="logging-in-mac-linux"></a>
#### 1.2.1 Mac OS / Linux
If you are using Mac OS X or Linux, open up a terminal window, and run `ssh (AccessID)@grid.wayne.edu` where (AccessID) is replaced with your own AccessID. For example, since my AccessID is fy7392, I run the command `ssh fy7392@grid.wayne.edu` to connect to the grid. You will then be prompted for your WSU password which is the same password 
you use to log into WSU Academica. You should then be prompted with a QR code and instructions
to set-up Google Authenticator. This will require you download the Google Authenticator app
on a smartphone, tablet, or computer. Once you have installed Google Authenticator and scanned the QR 
code, when you connect to the Grid in the future, you will input your WSU password, press enter, 
and then input your WSU HPC secret token found in your Google Authenticator app.

<a name="logging-in-windows"></a>
#### 1.2.2 Windows
If you are using Windows, download and install the PuTTY ssh client from
([http://www.putty.org/](http://www.putty.org/)) . PuTTY is free and open-source. After running
PuTTY, set connection type to ssh and enter grid.wayne.edu for the
hostname. You can leave everything else as default (for example, the default
port number, 22, is the correct one for ssh). After pressing the “Open”
button to open the connection, you will asked for a login/username, and
here you enter your AccessID.

<a name="basics"></a>
### 1.3 Linux Command Line Interface (CLI) Basics
<a name="shell-prompt"></a>
#### 1.3.1 Linux Shell Prompt
Once you are logged into the Grid, you will see a shell prompt like `fy7392@warrior ~]$` except with fy7392 replaced with your AccessID. The shell prompt consists of two primary parts:
  * Node: "warrior" is the name of the node of the server which you are logged into by default when you first log into the Grid. The "warrior" node is not to be used for running heavy computations and is instead used to schedule jobs (which can involve heavy computations) to be run on other nodes. All available nodes can be found on WSU's HPC webpage ([https://tech.wayne.edu/hpc/nodes](https://tech.wayne.edu/hpc/nodes)).
  * Path to current working directory: The tilde symbol ~ refers to your home directory (note that directories and folders are the same thing). The command `pwd` shows you the full path to your current working directory (i.e. pwd stands for path to working directory), which is always your home directory by default when you first log in. Note that only you have permission to read, write, and execute all files in your home directory (or subdirectories of your home directory) with perhaps the system administrators of the Grid being the only exceptions. The 2TB of disk space allotted to us in our home directories is typically not enough for working with Next-Generating Sequencing data bioinformaticians work with, and if you are a member of the Biostatistics and Bioinformatics Core here at Karmanos Cancer Institute / WSU, you should create a subdirectory of our BBC's directory /rs/rs_grp_bbc/ for your project. If you do not have the necessary permission to navigate to our BBC directory, please let me know and we will request that you obtain read, write, and execute privileges for our directory. As of November 2024, we have 50TB of disk space allotted to us in our BBC directory. Note that (i) creating and (ii) navigating among directories are covered elsewhere in this tutorial.

<a name="navigating"></a>
#### 1.3.2 Navigating, Creating, and Removing Directories
To create a new directory called 'RNAseq' in your current working directory, use the command `mkdir RNAseq` (note mkdir stands for make directory). Then to navigate to 
the 'RNAseq' directory, use `cd RNAseq` (note cd stands for change directory). To navigate back one directory, use `cd ../`. If we want to create subdirectories of 
RNAseq called 'data', 'output', and 'scripts', we can navigate back to the 'RNAseq' directory with 
`cd RNAseq` and then use `mkdir data output scripts`. If we are currently in the 'RNAseq' directory (as we are) and wish to remove the 'data' directory, we can run 
`rm -r data` (note rm stands for remove and -r is a flag passed to the rm command which allows us to remove entire directories; be careful when running `rm` and 
make sure that you are certain that you really do want to delete whatever directories/files you specify). If we wish to 
create a subdirectory of 'scripts' called 'preprocessing', we could navigate to the 'scripts' directory with `cd scripts` and then run `mkdir preprocessing`. Alternatively, we could specify 
the absolute path of the directory to create by running `mkdir /wsu/home/fy/fy73/fy7392/RNAseq/scripts/preprocessing` (with my AccessID replaced by yours), which will create 
the desired directory regardless of your current working directory. To list all non-hidden files and subdirectories in your current working directory, run `ls` (note ls stands for list). 
You can navigate to your home directory by running `cd ~` or `cd` regardless of your current working directory. To view the structure of all files and subdirectories in your current working directory, run `tree`.

<a name="editing"></a>
#### 1.3.3 Creating and Editing Files
To create and edit a file, we have several text editors available. VIM and Emacs are very powerful and have a steep learning curve, whereas Nano is less powerful and simpler. If you 
plan to spend substantial time working in the command line, then it may be a good idea to invest some time into becoming fluent with VIM or Emacs, but if not, then you may want 
to use Nano. To edit a file with Nano - regardless of whether the file already exists or not - we can run `nano test_file.txt`. You can type whatever you want to include in the file 
and then press Ctrl+O to write (i.e. save) the file and Ctrl+X to exit nano. 

<a name="asterisk"></a>
#### 1.3.4 Asterisk Symbol 
The asterisk symbol is very useful to familiarize yourself with. To illustrate an example of how it can be used, 
navigate to your home directory (e.g. run `cd ~`) and create five new directories 
with `mkdir scRNAseq_OCT2024 scRNAseq_NOV2024 bulkRNAseq_AUG2024 bulkRNAseq_OCT2024 WGS_SEP2024`. 
As mentioned before, `ls` will list all non-hidden files and subdirectories in your current working directory. 
To list all files and subdirectories in your current working directory beginning with 'scRNA', one can run `ls scRNA*`. 
To list all files and subdirectories in your current working directory ending with 'OCT2024', run `ls *OCT2024`. 
To list all files and subdirectories in your current working directory containing the phrase 'RNA' run `ls *RNA*`. 
The asterisk symbol * behaves similarly if used in most other Bash commands too. For example, if we want to remove 
all files and subdirectories of the current working directory ending in 'OCT2024', we can run `rm -r *OCT2024`.

<a name="disk-space"></a>
#### 1.3.5 View Disk Space Usage
To view the amount of disk space in your home directory that (i) you currently are using and (ii) you have available, run `wsuquota`. 
To view the amount of disk space consumed by every file in your current working directory, you can run `du` (du stands for disk space usage). 
To make the output more human-readable, you can add the -h flag: `du -h`. If there are lots of files in the subdirectories of your current working directory, you 
can display the disk space consumed by all files and subdirectories in your current working directory with `du -h --max-depth 1`.

<a name="grep"></a>
#### 1.3.6 Grep
Grep is a command-line tool used for searching a text-based file for a specified regular expression.

<a name="operators"></a>
#### 1.3.7 Pipe, >, and >> Operators



