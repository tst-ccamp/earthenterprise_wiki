# Building Earth Enterprise (Fusion, Server) on Ubuntu 14.04 LTS and RHEL 7 

## Common steps

Run these commands on either Ubuntu or RHEL/CentOS

1. Install git according to the instructions for your Linux OS below
2. Install git-lfs according to the instructions specified at https://git-lfs.github.com
3. Clone the gee-os repository with git
4. In the build instructions below, the scons commands for building GEE/Fusion have the following options:
* internal=1 - Build using non-optimized code, best for development and debugging
* optimize=1 - Build using optimized code, but with some debugging information
* release=1 - Build a release using optimized code and no debugging information
* -j# - Specifies the number of simultaneous build jobs to use. Replace # with an integer. It should roughly match the number of processing cores available
* --debug=stacktrace - If there is an error within a scons script, this will give you more detailed information on how to debug it
* --config=force - If you accidentally delete the .sconf_temp directory or make some changes to your system build libraries, use this to force the configuration to run again, otherwise the scons build may complain about missing libraries
5. Build using the steps bellow for your target platform
6. Run unit tests
* cd NATIVE-OPT-x86_64/bin/tests
* ./RunAllTests.pl 
* Or run an individual test

## Steps for Building on Ubuntu 14.04.5 LTS:

1. Install git:
sudo apt-get install git (installs version 1.9.1)

To get the most recent version of git, do the following (version 1.9.1 works for purposes of interacting with the repository, but if you want to download the latest version of git, the steps to do this have been outlined below):

sudo -i
add-apt-repository ppa:git-core/ppa
apt-get update
apt-get install git

This will install version 2.11
_Note: Be sure to exit "sudo" before proceeding_

2. Install the following packages (if they’re not installed already):
`sudo apt-get install gcc g++ scons automake autoconf libperl4-corelibs-perl libtool xorg-dev doxygen python-dev alien swig libgtest-dev libstdc++6 libxml2-dev libgtest-dev gettext libxinerama-dev libxft-dev libxrandr-dev libxcursor-dev libgdbm-dev libc6 libc6-dev libmng-dev zlib1g-dev libcap-dev libpng12-0 libpng12-dev freeglut3-dev flex libx11-dev python-dev bison++ bisonc++ libjpeg-dev libjpeg8-dev python2.7 python2.7-dev libgtest-dev libogdi3.2-dev libgif-dev libxerces-c-dev libgeos-dev libgeos++-dev libfreetype6 libfreetype6-dev python-imaging libproj-dev python-setuptools libgif-dev libxerces-c-dev libcap-dev libpq-dev`

3. Build the third party library:
For reference: GEEDIR=<new directory location>/googleclient/geo/earth_enterprise

cd $GEEDIR/src
scons -j8 optimize=1 third_party

4. Build Fusion/Earth Server 
scons -j8 optimize=1

## Steps for building on RHEL 7

1. Install git
sudo yum install git

2. Install Development Tools
sudo yum --setopt=group_package_types=mandatory,default,optional groupinstall "Development Tools"

3. Install additional packages
`sudo yum install scons perl-Perl4-CoreLibs xorg-x11-server-devel python27-python-devel perl-Alien-Packages gtest-devel openssl-devel libxml2-devel libXinerama-devel libXft-devel libXrandr-devel libXcursor-devel gdbm-devel libmng-devel libcap-devel libpng12-devel libXmu-devel freeglut-devel zlib-devel libX11-devel bison-devel openjpeg-devel openjpeg2-devel geos-devel proj-devel ogdi-devel giflib-devel xerces-c-devel`
 
4. Build third-party libraries
GEEDIR=<new directory location>/googleclient/geo/earth_enterprise
cd $GEEDIR/src
scons -j8 optimize=1 third_party

5. Build Fusion/Earth Server
scons -j8 optimize=1

## Build and deploy if you have access to the 5.1.3 installer
A build and deploy script is provided that can simplify the build and installation process if you have the GEE and Fusion 5.1.3 installers. In the future this script will be updated to work without the previous installers. 
1. Install GEE and Fusion 5.1.3
2. cd $GEEDIR/src
3. ./tmp/build_and_deploy_gee.sh --build

