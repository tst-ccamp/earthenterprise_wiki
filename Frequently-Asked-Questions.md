## Why do I get an error complaining about gz file not being valid?
Open GEE uses git-lfs to store its large files, such as gz files, in GitHub. Follow the [GitHub git-lfs Instructions](https://git-lfs.github.com/) on how to install git-lfs. After installing the extension you will need to clone the repo again.

## I've signed a CLA. Why does GitHub have an X on my commit and it says "Failure: need a CLA for one or more commit authors" when I hover over the X?
The email field set on each commit should match the email address specified in your GitHub account. Follow the instructions [here](https://help.github.com/articles/setting-your-email-in-git/). Next, rebase your commits, verify they have the correct email set, and do `git push origin --force` on the branch you want to merge.

## Why do I get errors downloading files due to API Rate Limit?
This happens because the clone/download was initiated without authenticating with Github. Add your ssh key and clone the repository using SSH.

## I’ve built GEE Fusion and Server. Now how do I install them?
There is currently no official installer for the open source version of GEE Fusion and Server, but we're working on it. Previous versions of GEE used a commercial tool that requires a license to create installers. Since that option is not available for the open source version, we are rewriting the installers from scratch.  There are two workarounds that you can try:

 - You can run the beta version of the installer, which is available on the [fusion_installer branch](https://github.com/google/earthenterprise/tree/fusion_installer).  You can also see it on the related [pull request](https://github.com/google/earthenterprise/pull/43).  Keep in mind that this installer is in active development and may contain bugs. Although unlikely, some bugs may cause problems with your Linux installation. We recommend testing this installer on a virtual machine or on non-production hardware. We expect (but do not guarantee) that the installer will work on Ubuntu 14.04, but it may fail on other operating systems. However, you are welcome to make changes to the script in order to get it to work on your system.
 - If you have access to GEE Server and Fusion Pro 5.1.3, you can install that version of Fusion and Server, and then run ``tmp/build_and_deploy_gee.sh --build`` to build and install the open source version of GEE as described in the [build instructions](https://github.com/google/earthenterprise/wiki/Build-Instructions#build-and-deploy-if-you-have-access-to-the-513-installer). GEE 5.1.3 is the last commercial version of GEE and is not available publicly, so if you or your organization did not purchase a GEE license from Google, you probably do not have access to GEE 5.1.3.

If neither of the above options works for you, please be patient.  We are working to create an open source installer for Ubuntu 14.04 and Red Hat Enterprise Linux 7 and hope to have it available soon.  Installers for other operating systems such as Ubuntu 16.04 and CentOS 6 and 7 may become available in the future depending on project priorities and developer availability.
