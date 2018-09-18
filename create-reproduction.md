# Create a Minimal Reproduction Repository or Sample

When reporting an issue or bug for any of the Apache Cordova packages, it is helpful to create and include a link to a reproduction repository or sample.

## Why

When an Apache Cordova team member reviews a GitHub issue, they need to be able to identify if the issue a bug, a problem originating from the users' source code, or how the user is using one of the Cordova's libraries.

For an efficient evaluation, supplying a detailed report with [enough and correct information](TODO) is necessary. 

As a Cordova Maintainer, it can be cumbersome and even tough to reproduce an issue when there are many aspects to the working environment and users' source code.

By creating a reproduction repository, a maintainer should have _all_ of the same information.

The goal of the reproduction repository is to replicate the bug in a minimal project that contains only the necessary platforms, libraries, and plugins to reproduce the bug. Often, being able to replicate a bug outside of the usual project will lead to explaining more information.

When creating the minimal project, it may be possible to discover that it is not a bug, but something unrelated and only manifests in the main project for other reasons.

## How

The steps below show how to create a reproduction repository, on GitHub. This repository is for Apache Cordova maintainers for reproducing, evaluating, and debugging the associated issue ticket. Any public accessible git remote service is acceptable. For example GitHub, BitBucket, GitLab, etc.

### Step 1: Creating a Blank GitHub Repository
1. Go to (Create a new repository)[https://github.com/new] on GitHub.
1. Insert a `Repository name`
1. Select `Public` to make the repository public accessible
1. Click `Create repository`

**IMPORTANT:** Do not check `Initialize this repository with a README`

### Step 2: Uploading the Clean Project
In the terminal, execute the following commands:
```
$ cordova create sample-project
$ cd sample-project
$ git init
$ git add .
$ git commit -m "Initialize with Clean Project"
```

### Step 3: Adding Necessary Dependencies
1. Add the necessary platform(s) and/or plugin(s) needed to reproduce the problem.

    **Example:**
    ```
    $ cordova platform add android
    $ cordova plugin add cordova-plugin-inappbrowser
    ```

1. Commit and push the changes to the reproduction repository with a commit message that includes the exact commands in the order of execution.

    **Example:**
    ```
    $ git commit -m "Step-by-Step Command Execution:
    - cordova platform add android
    - cordova plugin add cordova-plugin-inappbrowser
    "
    $ git push origin master
    ```

### Step 4: Reproducing the Issue
1. Update the project source code to reproduce and trigger the problem.
1. Commit and push the issue reproduction code
    ```
    $ git commit -m "Issue Reproduction Code"
    $ git push origin master
    ```

### Step 5: Creating and Submitting the Issue Ticket
In the GitHub issue ticket, supply the link to the public repository.

Later, the repository can be used as a "test" to confirm if the problem has been resolved in a future update in regards to the library that was faulty.
