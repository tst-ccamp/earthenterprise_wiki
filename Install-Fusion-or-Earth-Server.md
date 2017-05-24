## **Supported Operating Systems**
The installer has been successfully tested on Ubuntu 14.04, Ubuntu 16.04, Red Hat Enterprise Linux 7, and CentOS 7.

## **Prerequisite Steps**
To install Fusion or Earth Server, you must prepare the install package from a successful build of the source (which contains Fusion and Earth Server source code) and Third Party packages.  For more information on building Fusion, please review the following link:

[Building Earth Enterprise Fusion and Server](Build-Instructions)

## **Building the Install Package**
You will need to build the install package.  The install package is built using scons.  Please note that the default temporary staging area for the install package is /tmp/fusion_os_install.  This can be changed by specifying a different **installdir** parameter. Please note that all steps must use the same directory location.

In the commands below, you may need to change "release=1" to "optimize=1", depending on which type you used when building the source code.  You should use the same flag for both the build and install commands.

1. (Optional) Prepare the tutorial files
    ```
    cd earthenterprise/earth_enterprise/tutorial
    mkdir FusionTutorial
    wget http://data.opengee.org/FusionTutorial-Full.tar.gz
    tar -xvzf FusionTutorial-Full.tar.gz -C FusionTutorial
    ```

1. (Mandatory) Create the install package
    ```
    cd earthenterprise/earth_enterprise
    scons -j8 release=1 stage_install
    ```

At this point, you have fully built the install package.  The Fusion and Earth Server installers use this package to install their respective components.

## **Installing Fusion**
To install fusion run the following command:

    cd earth_enterprise/src/installer
    sudo ./install_fusion.sh

The installer can use the default install directory of /tmp/fusion_os_install.  If you placed the install package in a different location, you can pass that location as a parameter to the installer.

Run the following to get an explanation of all available customizations:

`sudo ./install_fusion.sh -h`

**Note** The installer adds the `/opt/google/bin` to your path by adding a file to /etc/profile.d. However, these files are only read when you first log in, so you need to log out and back in or reboot before this will occur. Until then, you can temporarily add the bin directory to your path by executing the following command in each bash shell you wish to run Fusion from:

    export PATH=$PATH:/opt/google/bin

## **Installing Earth Server**
To install GEE server run the following command:

    cd earth_enterprise/src/installer
    sudo ./install_server.sh

The installer can use the default install directory of /tmp/fusion_os_install.  If you placed the install package in a different location, you can pass that location as a parameter to the installer.

Run the following to get an explanation of all available customizations:

`sudo ./install_server.sh -h`