If you want to build, install, or run Portable server, see the [Portable Server page](https://github.com/google/earthenterprise/wiki/Portable-Server).

# Building Earth Enterprise Fusion and Server

Building is currently supported on 64-bit versions of Ubuntu 14.04 LTS, Ubuntu 16.04 LTS, RHEL 7, and CentOS 7.

1. Install git
    1. On Ubuntu  
        Install the system default version:
        ```
        sudo apt-get install git
        ```
        Or install the latest version:
        ```
        sudo add-apt-repository ppa:git-core/ppa
        sudo apt-get update
        sudo apt-get install git
        ```
    1. On RHEL/CentOS  
        Install the system default version:
        ```
        sudo yum install git
        ```
        Or install the latest version from the IUS repo (recommended) [ [More Info] ](https://ius.io/GettingStarted/):
        ```
        sudo yum install -y wget
        cd /tmp
        wget https://rhel7.iuscommunity.org/ius-release.rpm
        sudo yum install ius-release.rpm
        sudo yum install git2u-all
        ```
1. Install git-lfs according to the instructions specified at https://git-lfs.github.com
    
    In most cases:
    ```
    curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
    ```
1. Enable additional repos
    1. On Ubuntu  
        This step is not required.
    1. On CentOS  
        ```
        sudo yum install epel-release
        ```
    1. On RHEL  
        If the first command doesn't work, try the alternate methods listed [here](https://www.cyberciti.biz/faq/installing-rhel-epel-repo-on-centos-redhat-7-x/)
        ```
        sudo yum install epel-release
        sudo subscription-manager repos --enable=rhel-7-server-optional-rpms
        sudo subscription-manager repos --enable=rhel-7-server-optional-source-rpms
        ```
1. Install required packages
    1. On Ubuntu
        ```
        sudo apt-get install gcc g++ scons automake autoconf libperl4-corelibs-perl libtool xorg-dev doxygen python-dev alien swig libgtest-dev libstdc++6 libxml2-dev gettext libxinerama-dev libxft-dev libxrandr-dev libxcursor-dev libgdbm-dev libc6 libc6-dev libmng-dev zlib1g-dev libcap-dev libpng12-0 libpng12-dev freeglut3-dev flex libx11-dev bison++ bisonc++ libjpeg-dev libjpeg8-dev python2.7 python2.7-dev python2.7-psycopg2 libogdi3.2-dev libgif-dev libxerces-c-dev libgeos-dev libgeos++-dev libfreetype6 libfreetype6-dev python-imaging libproj-dev python-setuptools libgif-dev libxerces-c-dev libcap-dev libpq-dev openssl libxml2-utils libxmu-dev 
        ```
        
        Note: we recommend gcc and g++ version 4.8 or higher

    1. On RHEL/CentOS
        ```
        sudo yum --setopt=group_package_types=mandatory,default,optional groupinstall "Development Tools"
        sudo yum install scons perl-Perl4-CoreLibs xorg-x11-server-devel python-devel perl-Alien-Packages gtest-devel openssl-devel libxml2-devel libXinerama-devel libXft-devel libXrandr-devel libXcursor-devel gdbm-devel libmng-devel libcap-devel libpng12-devel libXmu-devel freeglut-devel zlib-devel libX11-devel bison-devel openjpeg-devel openjpeg2-devel geos-devel proj-devel ogdi-devel giflib-devel xerces-c xerces-c-devel
        ```
        If you get an error about git having conflicts, add `--skip-broken` to the first command.
1. Clone the gee-os repository with git
    1. Method 1: Clone and download LFS files in one step (may be slower and more error prone)
        ```
        git clone git@github.com:<username>/earthenterprise.git
        ```
    1. Method 2: Clone and download LFS files in two steps
        ```
        GIT_LFS_SKIP_SMUDGE=1 git clone git@github.com:<username>/earthenterprise.git
        cd earthenterprise
        git lfs pull
        ```
1. In the build instructions below, the scons commands for building GEE/Fusion have the following options:
    * `internal=1` - Build using non-optimized code, best for development and debugging
    * `optimize=1` - Build using optimized code, but with some debugging information
    * `release=1` - Build a release using optimized code and no debugging information
    * `-j#` - Specifies the number of simultaneous build jobs to use. Replace # with an integer. It should roughly match the number of processing cores available
    * `--debug=stacktrace` - If there is an error within a scons script, this will give you more detailed information on how to debug it
    * `--config=force` - If you accidentally delete the .sconf_temp directory or make some changes to your system build libraries, use this to force the configuration to run again, otherwise the scons build may complain about missing libraries
1. Build Earth Enterprise Fusion and Server:
    ```
    cd earthenterprise/earth_enterprise
    scons -j8 release=1 build
    ```
1. Run unit tests
    ```
    cd src/NATIVE-REL-x86_64/bin/tests
    ./RunAllTests.pl
    ```
    Or run an individual test

## Install Fusion and Earth Server
For information on how to install Fusion and/or Earth Server, see [Install Fusion or Earth Server](Install-Fusion-or-Earth-Server)