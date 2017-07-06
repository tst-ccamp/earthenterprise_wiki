## Table of Contents

1. [Building Portable Server on Linux and Windows](#building-portable-server-on-linux-and-windows)
    1. [Portable on Linux](#portable-on-linux)
    1. [Portable on Windows](#portable-on-windows)

# Building Portable Server on Linux and Windows

Software build prerequisites:

    * Python
    * Python pexpect installed
    * Swig with support for Python
    * g++

Portable run-time prerequisites:

    * Python
    * Python tornado installed


## Portable on Linux

Make sure you have Python, the `pexpect` Pip package, as well as `tornado`, g++, and Swig with Python support installed.  E.g.:

    sudo apt-get install g++ python python-pexpect python-tornado swig

Run

    earthenterprise/earth_enterprise/src/portableserver/build.py

The build script will produce a compressed archive with a name that looks like `earthenterprise/earth_enterprise/src/portableserver/build/portableserver-linux-5.1.3-20170412.tar.gz`. The build date part of the file name will change depending on the day you build.

To run Portable Server from this archive package:

    1. Extract all archive contents
    2. cd portableserver-linux-5.1.3-20170412/server/ #(substituting your extracted directory)
    3. python portable_server.py

You can edit `portableserver-linux-5.1.3-20170412/server/portable.cfg` and `portableserver-linux-5.1.3-20170412/server/remote.cfg` for your configuration needs before starting the server.

To clean build files, run 

    earthenterprise/earth_enterprise/src/portableserver/build.py --clean


## Portable on Windows

### Install a g++ Compiler

You can install [MinGW](http://www.mingw.org/) with a g++ compiler, or run the build from a Git-BASH or Git-Cmd shell from [Git-Scm](https://git-scm.com/), which should come with `g++`.

Make sure `g++` is in your `PATH`.


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

Run

    python earthenterprise\earth_enterprise\src\portableserver\build.py

The build script will produce a compressed archive with a name that looks like `earthenterprise\earth_enterprise\src\portableserver\build\portableserver-windows-5.1.3-20170412.zip`. The build date part of the file name will change depending on the day you build.

To run Portable Server from this archive package:

    1. Extract all archive contents
    2. cd portableserver-windows-5.1.3-20170412\server\ #(substituting your extracted directory)
    3. python portable_server.py

You can edit `portableserver-windows-5.1.3-20170412\server\portable.cfg` and `portableserver-windows-5.1.3-20170412\server\remote.cfg` for your configuration needs before starting the server.

To clean build files, run 

    python earthenterprise\earth_enterprise\src\portableserver\build.py --clean