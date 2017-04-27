## **Supported Operating Systems**
The installer has been successfully tested on Ubuntu 14.04, Ubuntu 16.04 and Red Hat Enterprise Linux 7.

## **Prerequisite Steps**
To install Fusion, you must prepare the install package from a successful build of Fusion and Third Party packages (in release mode).  For more information on building Fusion, please review the following link:

[Building Earth Enterprise (Fusion, Server) on Ubuntu 14.04 LTS, Ubuntu 16.04 LTS and RHEL 7 (#Build-Instructions)

## **Building the Install Package**
You will need to build the install package.  The install package is built using scons.  Please note that the default temporary staging area for the install package is /tmp/fusion_os_install.  This can be changed by specifying a different **installdir** parameter. Please note that all steps must use the same directory location.

To build the install package, run the following commands:

#### **Step 1: Mandatory build install package step**

    cd /earth_enterprise/src
    sudo scons -j2 installdir=/tmp/fusion_os_install release=1 install

#### **Step 2: Mandatory build install package step**

    cd ..  (you should be in /earth_enterprise)
    sudo scons -j2 installdir=/tmp/fusion_os_install 

#### **Step 3: Optional step if you want to install the Fusion tutorial data files**
##### **A: Prepare the location**

    cd earth_enterprise/tutorial 
    mkdir FusionTutorial

##### **B: Download and extract the tutorial files**
You will need to run the following command to download the tutorial file archive.

    wget http://data.opengee.org/FusionTutorial-Full.tar.gz
    tar -xvzf FusionTutorial-Full.tar.gz -C FusionTutorial

##### **C: Add tutorial files to the install package**

    sudo scons installdir=/tmp/fusion_os_install

**At this point, you have fully built the install package.  The Fusion installer uses this package to install the fusion service/console.**

## **Installing Fusion**
To install fusion run the following command:

    cd earth_enterprise/src/installer
    sudo ./install_fusion.sh


