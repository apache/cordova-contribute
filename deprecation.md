
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