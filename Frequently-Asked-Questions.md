## Why do I get an error complaining about gz file not being valid?
Open GEE uses git-lfs to store its large files, such as gz files, in GitHub. Follow the [GitHub git-lfs Instructions](https://git-lfs.github.com/) on how to install git-lfs. After installing the extension you will need to clone the repo again.

## I've signed a CLA. Why does GitHub have an X on my commit and it says "Failure: need a CLA for one or more commit authors" when I hover over the X?
The email field set on each commit should match the email address specified in your GitHub account. Follow the instructions [here](https://help.github.com/articles/setting-your-email-in-git/). Next, rebase your commits, verify they have the correct email set, and do `git push origin --force` on the branch you want to merge.