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

## 6. Submitting Issues
If you are experiencing issues with GEE and want to report a bug please include the following in your issue:
* Command that results in error
* The directory the command was run in
* Expected result
* Reproduction steps