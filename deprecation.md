# Deprecation and Archiving Policy

Apache Cordova has been around quite some time, having been started back in August 2008. As it consists of many individual "parts", some of those stopped being useful for any number of reasons. This "Deprecation and Archiving Policy" describes why, when and how projects can be deprecated and archived - and what that actually means.

## Deprecation Policy

When a piece of Apache Cordova stops being useful or necessary we vote on deprecating it on our [dev mailing list](mailing-lists.md).

### Reasons for Deprecation

Common reasons for deprecation of a piece of Apache Cordova are:

- General availability of a web standard that achieves the same thing
- A better replacement is available somewhere else
- Usage of a platform declined to a non relevant level
- A platform was deprecated itself by its producer

### Meaning of Deprecation

When we deprecate something it means no more work will be done on it. We make the deprecation clearly visible in the project's `README.md` (see [Deprecation notice templates](#deprecation-and-archiving-notice-templates) which might also include a reason and links to alternatives if available) and repository description.

**Users can still use the software** as before, we just put them on notice that the software might break in the future - e.g. with new operating system releases or bugs might be found - and we won't fix this any more.

**Users can also still fork the repository** and create their own bug fixes and even new features. The forks will be discoverable with the GitHub "Network" and "Forks" features. There you can see all forks available and easily spot extra commits people have done in an easy and visual way.

**Cordova might still accept bug fix Pull Requests** on the original repository and create a patch release.

## Archiving Policy

A deprecated repository might also be archived when we won't provide support of any kind (Issues, Pull Requests, any releases) for this piece of software any more. Again the decision is made on our [dev mailing list](mailing-lists.md).

A repository can be deprecated and archived at the same time.

### Meaning of Archiving

Additionally to the points listed in [Meaning of Deprecation](#meaning-of-deprecation), an archived repository is "read only" in any way: No more commits, Issues or Pull Requests are possible.

This is achieved by using GitHub's [archive repositories](https://help.github.com/articles/about-archiving-repositories/) feature:

> When a repository is archived, its issues, pull requests, code, labels, milestones, projects, wiki, releases, commits, tags, branches, reactions, and comments become read-only. To make changes in an archived repository, you must unarchive the repository first.

## Deprecating or Archiving a Repository

### 1. Make changes in README

Add the [deprecation or archiving notice template](#deprecation-and-archiving-notice-templates) to the `README.md` of the project.

### 2. Request GitHub repository archiving

To request archiving of a repository, a [PMC](TODO) member has to [open an issue with Apache INFRA](https://issues.apache.org/jira/browse/INFRA).

For deprecation:

1. Make sure deprecation notice is in README and contains all information
1. Open an issue and request that the repository description is prefixed with [DEPRECTATED]

For archiving:

1. Make sure there are no more open issues and Pull Requests for this repository. If there are, please close them with this suggested text or similar:
   > We are archiving this repository following our deprecation policy documented at ..TODO.. Thanks for your issue or pull request anyway.
1. Make sure deprecation notice is in README and contains all information
1. Open an issue and request a) that the repository description is prefixed with [DEPRECTATED] and b) the repository is archived.

## Deprecation and Archiving notice templates

### Deprecated Repository

```markdown
---
**Deprecation Notice**
This repo is deprecated. No more development, we still might release security fixes and other necessary patch updates. Please find other way to solve the problem.
- Reason for deprecation: ...
- Relevant links: ...
Feel free to fork this repository and work on your fork. Your fork will show up in https://github.com/apache/cordova-.../network/member where other users can look for updated forks.

No more work will be done on this plugin by the Cordova development community. You can continue to use this plugin and it should work as-is in the future but any more arising issues will not be fixed by the Cordova community.
---
```

### Archived Repository

```markdown
---
**Deprecation and Archiving Notice**
This repo is archived. No more development.
GitHub repository is archived, which means no more code changes, issues or pull requests.
- Reason for deprecation: ...
- Relevant links: ...
Feel free to fork this repository and work on your fork.
---
```


---
> Mailing list discussion on the topic:
> https://lists.apache.org/thread.html/34369ada22f8a616e90471d38c8fd7def2eb17ff3ddbf4ba0b47987f@%3Cdev.cordova.apache.org%3E