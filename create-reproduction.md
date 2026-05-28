# Create a Minimal Reproduction Repository or Sample

When reporting an issue or bug for any of the Apache Cordova packages, it is helpful to create and include a link to a reproduction repository or sample. This helps maintainers when reproducing, evaluating, debugging and finally fixing the associated issue. See also [this article on Stack Overflow](https://stackoverflow.com/help/minimal-reproducible-example).

## Why?

The goal of the reproduction repository is to replicate the bug in a minimal project that contains only the necessary platforms, libraries, and plugins to reproduce the bug.

For a Cordova maintainer it can be a lot of work to reproduce your specific issue as there are many aspects to your  working environment and source code. By creating a reproduction repository, you can prodive _all_ useful information to the maintainer and make this process much easier and faster.

Very often users creating a minimal project discover that their problem is not actually a bug, but something unrelated that only manifests in their main project for other reasons. They also learn much more about why a problem is occuring and can add this information to their GitHub issue.

## How?

The steps below show how to create a reproduction repository on GitHub. (Any public accessible Git remote service is acceptable: GitHub, BitBucket, GitLab, etc).

### TLDR:

- Create a new Cordova project,
- implement a reproduction of your problem,
- put the project on Github,
- and post the link to the repository in your issue.

### Step 1: Create a new GitHub repository

1. [Create a new repository](https://github.com/new) on GitHub
1. Insert a `Repository name`
1. Select `Public` to make the repository publicly accessible
    **IMPORTANT:** Do not check "Initialize this repository with a README"
1. Click `Create repository`

### Step 2: Upload the clean Cordova project

1. Create a new Cordova project
1. Initialize a Git repository in the newly created project folder
1. Commit the unchanged Cordova project
1. Add the GitHub repository as a remote to that project
1. Push the commit got GitHub

Execute the following commands in the terminal to achieve the steps above:

```
$ cordova create reproduction-sample
$ cd reproduction-sample
$ git init
$ git add .
$ git commit -m "Initialize new Cordova project"
$ git remote add origin git@github.com:<USERNAME>/<REPO_NAME>.git
$ git push -u origin master
```

### Step 3: Add necessary dependencies

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

### Step 4: Reproduce the issue

Update the project source code to reproduce and trigger the problem.

### Step 5: Upload the finished reproduction code

Commit and push the reproduction code.

**Example:**
```
$ git commit -m "Reproduce problem"
$ git push origin master
```

### Step 6: Create and submit the issue

In the Apache Cordova GitHub issue, supply the link to the public repository.

Later, the repository can be used to test if the problem has been resolved in a future update in regards to the library that was faulty.
