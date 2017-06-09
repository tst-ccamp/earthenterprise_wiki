## 1. Why do I get an error complaining about a gzip file not being valid? (gzip: stdin: not in gzip format)
Open GEE uses git-lfs to store its large files, such as gz files, in GitHub. Follow the [GitHub git-lfs Instructions](https://git-lfs.github.com/) on how to install git-lfs. After installing the extension you will need to clone the repo again or try running `git lfs pull` in the repo.
## 2. I've signed a CLA. Why does GitHub have an X on my commit and it says "Failure: need a CLA for one or more commit authors" when I hover over the X?
The email field set on each commit should match the email address specified in your GitHub account. Follow the instructions [here](https://help.github.com/articles/setting-your-email-in-git/). Next, rebase your commits, verify they have the correct email set, and do `git push origin --force` on the branch you want to merge.

## 3. Why do I get errors downloading files due to API Rate Limit?
This happens because the clone/download was initiated without authenticating with Github. Add your ssh key and clone the repository using SSH.

## 4. I’ve built GEE Fusion and Server. Now how do I install them?
Instructions for installing GEE Fusion and Server are available [on the wiki](https://github.com/google/earthenterprise/wiki/Install-Fusion-or-Earth-Server).

## 5. Why do I get "File has unknown problems" when trying to load a file?
If the file type is .jp2, then that format is not supported yet so you will see this error. If this error was encountered while executing the GEE tutorial, use the .tif file in the same directory instead.
If it is not a .jp2 file, then this error is likely due to file permissions with the sample data. Update the permissions on the files to give write permissions to gefusionuser and then try to load the file again. A bug has been created to fix this issue ([#16](https://github.com/google/earthenterprise/issues/16)).

## 6. Why do I get "Fusion warning: Unable to connect to System Manager: socket connect '127.0.1.1:13031': Connection refused" when I run the Fusion tool?
The gefusion process may not be running. Try executing the command `sudo service gefusion restart`. If it was not already running this will tell you and start it. Now try your operation again. If that doesn't fix the problem it may be more serious. Consider asking your question in the Slack chat or create an issue for support.

## 7. Why do I keep getting an error indicating failed to setup and configure postgresdb when trying to install GEE Server?
The problem comes from the fact that the fusion installer will remove the /tmp/fusion_os_install directory after it successfully runs by default. So, if you ran install_fusion.sh without the -nop flag, you'll need to repeat these steps specified in the [Installation Guide](https://github.com/google/earthenterprise/wiki/Install-Fusion-or-Earth-Server#building-the-install-package) before running install_server.sh.

## 8. How do I submit issues?
If you are experiencing issues with GEE and want to report a bug please include the following in your issue:
* Command that results in error
* The directory the command was run in
* Expected result
* Reproduction steps

## 9. What client can I use for viewing globes created from Google Earth Enterprise ?

Clients for 3D Globes

1. Google Earth Enterprise Client - Non-Open Sourced Client by Google
Download links available at :
https://github.com/google/earthenterprise/wiki/Google-Earth-Enterprise-Client-(EC)

Note : The Google Earth installers are currently blocked for download in these countries: Cuba, North Korea, Sudan and Syria. But some users have encountered problems not be able to reach the installers from China, that could be related to Great Firewall.

Google does not permit redistribution of the installers. So please defer from sharing/distributing the installers.

2.  Cesium:
Open Sourced Web Client by AGI.
More info on viewing globes hosted by Google Earth Enterprise in Cesium at https://cesiumjs.org/for-google-earth-developers.html

## 10. Why am I getting "The Google Earth Plugin Failed to load " error when accessing the 3D globe in browser?

Google Earth 3D browser plugin is no longer supported because it is based on old NPAPI technology that in general not supported by newer browsers. It might work for very old browsers though if you so much willing to try. 

Also, The Plugin is not Open Sourced.

## 11. Why do I receive an error when saving/working with data about a "Known Volume"?

Files in GEE are expected to reside in locations known as known volumes. During the Install process a default known volume is chosen, which defaults to /geovol/src. It is possible to create other known volumes using the command "geconfigureassetroot". 

Since source files may be needed in the future when running fusion, it makes sense to have a designated place for the source data. If you see this error while working with the tutorial data, it is likely the data was installed after the installation process and is not located in a known volume. If you would like to add them as a known volume use this command:

```
sudo service gefusion stop

sudo /opt/google/bin/geconfigureassetroot --addvolume tutorial:/opt/google/share/tutorials/fusion --srcvol /opt/google/share/tutorials/fusion

sudo service gefusion start
```

To find more information, reference the documentation on this topic here: http://www.opengee.org/geedocs/answer/3481558.html#63542

In addition, there is documentation about configuring your data locations here: http://www.opengee.org/geedocs/answer/3481499.html 