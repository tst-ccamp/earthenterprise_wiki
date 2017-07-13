## Why do I get an error complaining about a gzip file not being valid? (gzip: stdin: not in gzip format)
Open GEE uses git-lfs to store its large files, such as gz files, in GitHub. Follow the [GitHub git-lfs Instructions](https://git-lfs.github.com/) on how to install git-lfs. After installing the extension you will need to clone the repo again or try running `git lfs pull` in the repo.

## I've signed a CLA. Why does GitHub have an X on my commit and it says "Failure: need a CLA for one or more commit authors" when I hover over the X?
The email field set on each commit should match the email address specified in your GitHub account. Follow the instructions [here](https://help.github.com/articles/setting-your-email-in-git/). Next, rebase your commits, verify they have the correct email set, and do `git push origin --force` on the branch you want to merge.

## Why do I get errors downloading files due to API Rate Limit?
This happens because the clone/download was initiated without authenticating with Github. Add your ssh key and clone the repository using SSH.

## I’ve built GEE Fusion and Server. Now how do I install them?
Instructions for installing GEE Fusion and Server are available [on the wiki](https://github.com/google/earthenterprise/wiki/Install-Fusion-or-Earth-Server).

## Why do I get "Fusion warning: Unable to connect to System Manager: socket connect '127.0.1.1:13031': Connection refused" when I run the Fusion tool?
The gefusion process may not be running. Try executing the command `sudo service gefusion restart`. If it was not already running this will tell you and start it. Now try your operation again. If that doesn't fix the problem it may be more serious. Consider asking your question in the Slack chat or create an issue for support.

## How do I submit issues?
If you are experiencing issues with GEE and want to report a bug please include the following in your issue:
* Command that results in error
* The directory the command was run in
* Expected result
* Reproduction steps

## What client can I use for viewing globes created from Google Earth Enterprise ?

Clients for 3D Globes

1. Google Earth Enterprise Client - Non-Open Sourced Client by Google
Download links available at :
https://github.com/google/earthenterprise/wiki/Google-Earth-Enterprise-Client-(EC)

Note : The Google Earth installers are currently blocked for download in these countries: Cuba, North Korea, Sudan and Syria. But some users have encountered problems not be able to reach the installers from China, that could be related to Great Firewall.

Google does not permit redistribution of the installers. So please defer from sharing/distributing the installers.

2.  Cesium:
Open Sourced Web Client by AGI.
More info on viewing globes hosted by Google Earth Enterprise in Cesium at https://cesiumjs.org/for-google-earth-developers.html

No clients are not supported by this project, and bugs in clients or client usage are out-of-scope for this project. 

## Why am I getting "The Google Earth Plugin Failed to load " error when accessing the 3D globe in browser?

Google Earth 3D browser plugin is no longer supported because it is based on old NPAPI technology that in general not supported by newer browsers. It might work for very old browsers though if you so much willing to try. 

Also, The Plugin is not Open Sourced.

## Why do I receive an error when saving/working with data about a "Known Volume"?

Files in GEE are expected to reside in locations known as known volumes. During the Install process a default known volume is chosen, which defaults to /geovol/src. It is possible to create other known volumes using the command "geconfigureassetroot". 

Since source files may be needed in the future when running fusion, it makes sense to have a designated place for the source data. If you see this error while working with the tutorial data, it is likely the data was installed after the installation process and is not located in a known volume. If you would like to add them as a known volume use this command:

```
sudo service gefusion stop

sudo /opt/google/bin/geconfigureassetroot --addvolume tutorial:/opt/google/share/tutorials/fusion --srcvol /opt/google/share/tutorials/fusion

sudo service gefusion start
```

To find more information, reference the documentation on this topic here: http://www.opengee.org/geedocs/answer/3481558.html#63542

In addition, there is documentation about configuring your data locations here: http://www.opengee.org/geedocs/answer/3481499.html 

## Where can I download the data for the Fusion Tutorial?

For information on the Fusion Tutorial data, see this GEE support page:
http://www.opengee.org/geedocs/answer/6028272.html

## While trying to create a mask for an image in fusion, I keep getting this 
error message "A XXXXX pixels x YYYYYY lines mask would be too large. 
Creation failed"

This is due to an old size limitation in GeoTIFFs. You may want to downsample the imagery and try again.

## Can I build GEE without an internet connection?
This has not been tested, there is no technical reason that it should not work.  Follow the steps below:

1. Make sure the prerequisites listed on the [build instructions](https://github.com/google/earthenterprise/wiki/Build-Instructions) page are installed on the machine on which you will build GEE.
1. Clone the git repo on a machine that does have internet access: `git clone git@github.com:google/earthenterprise.git`
1. Copy the `earthenterprise` directory to the machine on which you will build GEE.
1. Follow the remaining [build instructions](https://github.com/google/earthenterprise/wiki/Build-Instructions) and [install instructions](https://github.com/google/earthenterprise/wiki/Install-Fusion-or-Earth-Server) to build and install GEE.

If you have problems building and installing in an offline environment, please let us know.

## Can I build GEE on one machine and install it on another machine?
This has not been tested, there is no technical reason that it should not work.  Follow the steps below:

1. On the building machine, follow the [build](https://github.com/google/earthenterprise/wiki/Build-Instructions) and [install](https://github.com/google/earthenterprise/wiki/Install-Fusion-or-Earth-Server) instructions, but stop before running the `install_fusion.sh` and `install_server.sh` scripts.
1. Copy the contents of `earthenterprise/earth_enterprise/src/installer` and `/tmp/fusion_os_install` to the computer on which you will install GEE.  `fusion_os_install` must be placed under `/tmp`, but the `installer` directory can be placed anywhere.
1. You may also need to install some or all of the prerequisites listed in the [build instructions](https://github.com/google/earthenterprise/wiki/Build-Instructions) on the machine on which you will install GEE.
1. Run the `install_fusion.sh` and `install_server.sh` scripts to install fusion and server.

If you run into problems with the above instructions, please let us know.