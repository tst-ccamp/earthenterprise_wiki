## **Supported Operating Systems**
The installer has been successfully tested on Ubuntu 14.04, Ubuntu 16.04 and Red Hat Enterprise Linux 7.

## **Prerequisite Steps**
To install Fusion or Earth Server, you must prepare the install package from a successful build of the source (which contains Fusion and Earth Server source code) and Third Party packages (in release mode).  For more information on building Fusion, please review the following link:

[Building Earth Enterprise (Fusion, Server) on Ubuntu 14.04/16.04 LTS, RHEL 7 and CentOS 7](Build-Instructions)

## **Building the Install Package**
You will need to build the install package.  The install package is built using scons.  Please note that the default temporary staging area for the install package is /tmp/fusion_os_install.  This can be changed by specifying a different **installdir** parameter. Please note that all steps must use the same directory location.

In the commands below, you may need to change "optimize=1" to "release=1", depending on which type you used when building the source code.  You should use the same flag for both the build and install commands.

**Note:** You will need to run the commands in this step before installing Fusion and again before installing Server. If you plan to install both, you can add the "-nop" flag to the fusion install command.

To build the install package, run the following commands:

#### **Step 1: Mandatory - copy binaries**

    cd /earth_enterprise/src
    scons -j2 installdir=/tmp/fusion_os_install optimize=1 install

#### **Step 2: Mandatory - copy data and docs**

    cd ..  (you should be in /earth_enterprise)
    scons -j2 installdir=/tmp/fusion_os_install install 

#### **Step 3: Optional step if you want to install the Fusion tutorial data files**
##### **A: Prepare the location**

    cd earth_enterprise/tutorial 
    mkdir FusionTutorial

##### **B: Download and extract the tutorial files**
You will need to run the following command to download the tutorial file archive.

    wget http://data.opengee.org/FusionTutorial-Full.tar.gz
    tar -xvzf FusionTutorial-Full.tar.gz -C FusionTutorial

##### **C: Add tutorial files to the install package**

    scons installdir=/tmp/fusion_os_install

**At this point, you have fully built the install package.  The Fusion and Earth Server installers use this package to install their respective components.

## **Installing Fusion**
To install fusion only run the following command:

    cd earth_enterprise/src/installer
    sudo ./install_fusion.sh

If you plan to also install Server, instead run:

    cd earth_enterprise/src/installer
    sudo ./install_fusion.sh -nop

The installer can use the default install directory of /tmp/fusion_os_install.  If you placed the install package in a different location, you can pass that location as a parameter to the installer.

Run the following to get an explanation of all available customizations:

`sudo ./install_fusion.sh -h`

## **Installing Earth Server**
To install fusion run the following command:

    cd earth_enterprise/src/installer
    sudo ./install_server.sh

The installer can use the default install directory of /tmp/fusion_os_install.  If you placed the install package in a different location, you can pass that location as a parameter to the installer.

Run the following to get an explanation of all available customizations:

`sudo ./install_server.sh -h`

