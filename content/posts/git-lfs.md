---
categories:
    - git
date: "2018-11-27T07:13:17Z"
description: Resources and instruction how to use git-lfs.
tags: 
    - git
title: Use large files with git-lfs
draft: false
---
GitHub has a repository upload limit of 100MB.

    The maximum size of Git objects that can be pushed to repositories on this appliance. Allowing large objects to be pushed into Git can degrade performance, consider other options (e.g. git-lfs) before increasing this value.

<!--more-->

Sometimes you have documentation in MS Office formats or binary dependencies in you project. In GitHub it build to handle (ascii) source files. To handle binaries a Git extension, Git LFS exist.

    Git Large File Storage (LFS) replaces large files such as audio samples, videos, datasets, and graphics with text pointers inside Git, while storing the file contents on a remote server like GitHub.com or GitHub Enterprise.

Reorganizing the repository with Git LFS is in most case the solution. For more information please checkout the following links.

    https://git-lfs.github.com/
    https://help.github.com/articles/configuring-git-large-file-storage/
    http://www.strichnet.com/migrating-your-project-to-git-lfs/
    [https://stackoverflow.com/questions/34946134/how-to-migrate-a-repo-to-git-lfs-without-losing-all-the-commit-history]https://stackoverflow.com/questions/34946134/how-to-migrate-a-repo-to-git-lfs-without-losing-all-the-commit-history()
    https://docs.microsoft.com/en-us/vsts/repos/git/manage-large-files?view=vsts

## Set up git-lfs

1. Install git-lfs on your local machine
1. Set your git buffer size with ```git config --global http.postBuffer 104857600``` Where 104857600 is your buffer size in byte (100MB).
1. Define which file type is 'large' with ```git lfs track "*.jar *.zip *.pack"```
1. Add and commit the resultting .gitattributes file.
1. If you have an existing repository, use ```git lfs migrate import --include="*.<extension> --include-ref=refs/heads/master --include-ref=refs/heads/<branchname>```
1. When you have large files in multiple branches and need to delete them and to rewrite history use ```git filter-branch --tree-filter 'rm -f filename' HEAD ```
1. Push your repository to the upstream. (Force push if changing branches)
