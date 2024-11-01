# Slurm for Bioinformatics Tutorial

This repository is intended to be a tutorial for implementing common bioinformatics tasks with the job scheduler Slurm on a High-Performance Computing (HPC) cluster. This tutorial may be useful for anybody using Slurm as a job scheduler on an HPC cluster but is created with researchers using Wayne State University's HPC cluster (i.e. WSU's Grid) in mind. Much of the information in this tutorial can be found on WSU's Grid's tutorials page ([https://tech.wayne.edu/kb/high-performance-computing/hpc-tutorials](https://tech.wayne.edu/kb/high-performance-computing/hpc-tutorials)) or by consulting the Slurm documentation ([https://slurm.schedmd.com/documentation.html](https://slurm.schedmd.com/documentation.html)).


## Table of Contents
- [1. Getting Started](#getting-started)
   - [1.1 Create Grid Account](#create-account)
   - [1.2 Logging into the Grid](#logging-in)
      - [1.2.1 Mac OS / Linux](#logging-in-mac-linux)
      - [1.2.2 Windows](#logging-in-windows)
   - [1.3 Navigating in Linux](#navigating)

## 1. Getting Started
### 1.1 Create Grid Account
To WSU's HPC cluster, you must first apply for a Grid account which can be done via the "Renew or request Grid account tab" on WSU's HPC homepage ([https://tech.wayne.edu/hpc](https://tech.wayne.edu/hpc)).

 <a name="logging-in"></a>
### 1.2 Logging into the Grid
It is recommended to connect to the Grid using ssh (which stands for Secure Shell Protocol) which is a method allowing one to access computers over an unsecured network.
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
on a smartphone, tablet, or computer. Once you installed Google Authenticator and scanned the QR 
code, when you connect to the Grid in the future, you will input your WSU password, press enter, 
and then input your WSU HPC secret token found in your Google Authenticator app.

#### 1.2.2 Windows
If you are using Windows, download and install the PuTTY ssh client from
([http://www.putty.org/](http://www.putty.org/)) . PuTTY is free and open-source. After running
PuTTY, you set connection type to ssh, and enter grid.wayne.edu for the
hostname; you can leave everything else as default (for example, the default
port number, 22, is the correct one for ssh). After pressing the “Open”
button to open the connection, you will asked for a login/username, and
here you enter your AccessID.

### 1.3 Navigating in Linux
hellow orld
hellow orld
hellow orld
hellow orld
hellow orld
hellow orld
hellow orld













