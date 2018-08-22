# Deprecation and Archiving

[Apache Cordova's Deprecation Policy](https://cordova.apache.org/deprecation_policy.html) defines why, when and how Cordova projects are deprecated and archived. These are the steps to be taken by a contributor to "execute" such an deprecation:

## Deprecating or Archiving a Repository

### 1. Make changes in `README.md`

Add the [Deprecation Notice Template](#deprecation-notice-templates) to the `README.md` of the project. Add a reason and a link to further information (e.g. blog post, web standard definition etc.).

### 2. Request GitHub repository changes

A [PMC](TODO) member has to [open an issue with Apache INFRA](https://issues.apache.org/jira/browse/INFRA) to request changes to the GitHub repository.

For deprecation:

1. Make sure deprecation notice is in `README.md` and contains all information
1. [Open an issue](https://issues.apache.org/jira/browse/INFRA) and request that the repository description is prefixed with `[DEPRECTATED]`

For archiving:

1. Make sure there are no more open Issues and Pull Requests for this repository  
If there are, please close them with this suggested text or similar:
   > TODO  
   > We are archiving this repository following our deprecation policy documented at ..TODO..  
   > Thanks for your issue or pull request anyway.  
   > TODO
1. Make sure deprecation notice is in `README.md` and contains all information
1. [Open an issue](https://issues.apache.org/jira/browse/INFRA) and request a) that the repository description is prefixed with `[DEPRECTATED]` and b) the repository is archived on GitHub

## Deprecation Notice Templates

---
**Deprecation Notice**

This repository is deprecated and no more work will be done on this by Apache Cordova. You can continue to use this and it should work as-is in the future but any more future issues will not be fixed by the Cordova community.

Feel free to fork this repository and improve your fork. Existing forks are listed in [Network](network) and [Forks](network/members).

- Reason for deprecation: ...
- Learn more: https://example.org/article
---

### Markdown

```markdown
---
**Deprecation Notice**

This repository is deprecated and no more work will be done on this by Apache Cordova. You can continue to use this and it should work as-is in the future but any more future issues will not be fixed by the Cordova community.

Feel free to fork this repository and improve your fork. Existing forks are listed in [Network](network) and [Forks](network/members).

- Reason for deprecation: ...
- Learn more: https://example.org/article
---
```