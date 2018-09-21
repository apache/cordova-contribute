# Create a Minimal Reproduction Repository or Sample

When reporting an issue or bug for any of the Apache Cordova packages, it is helpful to create and include a link to a reproduction repository or sample. This repository is for Apache Cordova maintainers for reproducing, evaluating, and debugging the associated issue.

## Why

When an Apache Cordova team member reviews a GitHub issue, they need to be able to identify if the issue is a bug, a problem originating from the users' source code, or from how the user is using one of Cordova's libraries.

For an efficient evaluation, supplying a detailed report with [enough and correct information](TODO) is necessary. 

As a Cordova Maintainer, it can be cumbersome and even tough to reproduce an issue as there are many aspects to the working environment and users' source code. By creating a reproduction repository, you can prodive _all_ useful information to the maintainer and make this process much easier.

The goal of the reproduction repository is to replicate the bug in a minimal project that contains only the necessary platforms, libraries, and plugins to reproduce the bug. Often, being able to replicate a bug outside of the usual project will lead to explaining more information.

When creating the minimal project, it may be possible to discover that it is not a bug, but something unrelated and only manifests in the main project for other reasons.

## How

The steps below show how to create a reproduction repository, on GitHub. (Any public accessible git remote service is acceptable: GitHub, BitBucket, GitLab, etc).

### Step 1: Creating a Blank GitHub Repository
1. Go to [Create a new repository](https://github.com/new) on GitHub
1. Insert a `Repository name`
1. Select `Public` to make the repository public accessible
1. Click `Create repository`

**IMPORTANT:** Do not check `Initialize this repository with a README`

### Step 2: Uploading the Clean Project
1. Create a new Cordova project with `cordova create`
1. Initialize a Git repository in the project folder
1. Commit the unchanged Cordova project
1. Add the GitHub repository as a remote to that project
1. Push the commit got GitHub

Execute the following commands in the terminal to achieve the steps above:

```
$ cordova create reproduction-sample
$ cd reproduction-sample
$ git init
$ git add .
$ git commit -m "Initialize with Clean Project"
$ git remote add origin git@github.com:<USERNAME>/<REPO_NAME>.git
$ git push -u origin master
```

### Step 3: Adding Necessary Dependencies
Add and commit each platform(s) (`cordova platform add ...`) and/or plugin(s) (`cordova plugin add ...`) needed to reproduce the problem.

**Example:**
```
$ cordova platform add android
$ git add .
$ git commit -m "cordova platform add android"
$ cordova plugin add cordova-plugin-inappbrowser
$ git add .
$ git commit -m "cordova plugin add cordova-plugin-inappbrowser"
$ git push origin master
```

### Step 4: Reproducing the Issue
1. Update the project source code to reproduce and trigger the problem
1. Commit and push the issue reproduction code

    **Example:**
    ```
    $ git commit -m "Issue Reproduction Code"
    $ git push origin master
    ```

### Step 5: Creating and Submitting the Issue Ticket
In the Apache Cordova GitHub issue, supply the link to the public repository.

Later, the repository can be used to test if the problem has been resolved in a future update in regards to the library that was faulty.
