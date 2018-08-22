
## Deprecating or Archiving a Repository

### 1. Make changes in README

Add the [Deprecation Notice Template](#deprecation-notice-templates) to the `README.md` of the project. Add a reason and a link to further information (blog post, web standard definition etc.).

### 2. Request GitHub repository archiving

To request archiving of a repository, a [PMC](TODO) member has to [open an issue with Apache INFRA](https://issues.apache.org/jira/browse/INFRA).

For deprecation:

1. Make sure deprecation notice is in README and contains all information
1. [Open an issue](https://issues.apache.org/jira/browse/INFRA) and request that the repository description is prefixed with [DEPRECTATED]

For archiving:

1. Make sure there are no more open issues and Pull Requests for this repository. If there are, please close them with this suggested text or similar:
   > TODO  
   > We are archiving this repository following our deprecation policy documented at ..TODO..  
   > Thanks for your issue or pull request anyway.  
   > TODO
1. Make sure deprecation notice is in README and contains all information
1. [Open an issue](https://issues.apache.org/jira/browse/INFRA) and request a) that the repository description is prefixed with [DEPRECTATED] and b) the repository is archived.

## Deprecation Notice Templates

---
**Deprecation Notice**

This repository is deprecated and no more work will be done on this by Apache Cordova. You can continue to use this and it should work as-is in the future but any more future issues will not be fixed by the Cordova community.

Feel free to fork this repository and work on your fork. Existing forks are listed in [Network](network) and [Forks](network/members).

- Reason for deprecation: ...
- Learn more: https://example.org/article
---

### Markdown

```markdown
---
**Deprecation Notice**

This repository is deprecated and no more work will be done on this by Apache Cordova. You can continue to use this and it should work as-is in the future but any more future issues will not be fixed by the Cordova community.

Feel free to fork this repository and work on your fork. Existing forks are listed in [Network](network) and [Forks](network/members).

- Reason for deprecation: ...
- Learn more: https://example.org/article
---
```