## Table of Contents

1. [Portable Server Prerequisites](#portable-server-prerequisites)
    1. [Build Prerequisites](#build-prerequisites)
    1. [Run-time Prerequisites](#run-time-prerequisites)
1. [Portable Server on Linux](#portable-server-on-linux)
    1. [Building on Linux](#building-on-linux)
    1. [Installing on Linux](#installing-on-linux)
    1. [Running on Linux](#running-on-linux)
1. [Portable Server on Windows](#portable-server-on-windows)
    1. [Building on Windows](#building-on-windows)
    1. [Installing on Windows](#installing-on-windows)
    1. [Running on Windows](#running-on-windows)
1. [Portable Server on Mac OS](#portable-server-on-mac-os)


# Portable Server Prerequisites

## Build Prerequisites:

    * Python
    * Python pexpect installed
    * Swig with support for Python
    * g++

## Run-time prerequisites:

    * Python
    * Python tornado installed


# Portable Server on Linux

## Building on Linux

Make sure you have Python, the `pexpect` Pip package, as well as `tornado`, g++, and Swig with Python support installed.  

On Ubuntu:

    sudo apt-get install g++ python python-pexpect python-tornado swig python-psycopg2

On CentOS/RHEL:

    sudo yum -y install gcc-c++ python python-pip python-tornado swig python-psycopg2
    sudo pip install pexpect

Run

    earthenterprise/earth_enterprise/src/portableserver/build.py

The build script will produce a compressed archive with a name that looks like `earthenterprise/earth_enterprise/src/portableserver/build/portableserver-linux-5.1.3-20170412.tar.gz`. The build date part of the file name will change depending on the day you build.

You can install the built Portable Server from this `.tar.gz` archive. 

To clean build files, run 

    earthenterprise/earth_enterprise/src/portableserver/build.py --clean


## Installing on Linux

Portable Server is not currently packaged for Linux distributions by the GEE Open Source team. Instead, just extract the tarball generated in the [Building on Linux](#building-on-linux) step in a directory you want to run it from.  You could also create links, or start-up shell scripts for your convenience.

You need to have the Python interpreter and package dependencies listed in [Run-time Prerequisites](#run-time-prerequisites) set up and installed in order to run Portable Server.  If you carried out the [Building on Linux](#building-on-linux) step, you already have all of the required dependencies.


## Running on Linux

Change into the directory you extracted the built Portable Server tarball into (in the [Installing on Linux](#installing-on-linux) step).  Then, just start `server/portable_server.py`:

    1. cd portableserver-linux-5.1.3-20170412/server/ #(substituting your extracted directory)
    1. python portable_server.py

You can edit `portableserver-linux-5.1.3-20170412/server/portable.cfg` and `portableserver-linux-5.1.3-20170412/server/remote.cfg` for your configuration needs before starting the server.



# Portable Server on Windows

## Building on Windows

### Install a g++ Compiler

You can install [MinGW](http://www.mingw.org/) with a g++ compiler, or run the build from a Git-BASH or Git-Cmd shell from [Git-Scm](https://git-scm.com/), which should come with `g++`.

_Note: Git-BASH may have a 64-bit MinGW, and may not work by default._

Make sure `g++` is set in your `PATH`.

### Install Swig with Python Support

1. Download a [Swig](http://www.swig.org/download.html) Zip for Windows.
2. Extract the Zip in a desired installation directory.
3. Add the installation directory you extracted to your `PATH`.


### Install Python

Download and install [Python](https://www.python.org/downloads/) 2.7 or later.

Once you have Python installed, make sure you have `pexpect` and `tornado` installed. E.g.:

    cd \Python27\Scripts
    pip install pexpect tornado

Add the directory you installed Python in to your `PATH`.


### Build Portable Server

Open a command prompt with `g++`, `swig` and `python` in your `PATH`.

_Note: Git-BASH may have a 64-bit MinGW, and may not work by default._

E.g., on Windows your `PATH` may look like:

```
C:\swigwin-3.0.12;C:\Python27;C:\MinGW\bin;C:\Program Files\ . . .
```

Run

    python earthenterprise\earth_enterprise\src\portableserver\build.py

The build script will produce a compressed archive with a name that looks like `earthenterprise\earth_enterprise\src\portableserver\build\portableserver-windows-5.1.3-20170412.zip`. The build date part of the file name will change depending on the day you build.

You can install the built Portable Server from this Zip archive.

To clean build files, run 

    python earthenterprise\earth_enterprise\src\portableserver\build.py --clean


## Installing on Windows

We do not currently provide a Windows installer for Portable Server. Instead, just extract the built Portable Server from the Zip archive generated in the [Building on Windows](#building-on-windows) step in a directory you want to run it from.

You need to have the Python interpreter and packages listed in [Run-time Prerequisites](#run-time-prerequisites) set up and installed in order to run Portable Server.  If you carried out the [Building on Windows](#building-on-windows) step, you already have the required dependencies.


## Running on Windows

Change into the directory you extracted the built Portable Server Zip archive into (in the [Installing on Windows](#installing-on-windows) step). Then, just start `server\portable_server.py`:

    1. cd portableserver-windows-5.1.3-20170412\server\ #(substituting your extracted directory)
    1. python portable_server.py

You can edit `portableserver-windows-5.1.3-20170412\server\portable.cfg` and `portableserver-windows-5.1.3-20170412\server\remote.cfg` for your configuration needs before starting the server.



# Portable Server on Mac OS

Currently, building and running Portable Server on Mac OS has not been tested.

Previous versions have run on Mac OS, and the `build.py` script has untested logic for running the Mac OS build commands.  However, at present, you'll have to fix any problems you run into on Mac OS.
