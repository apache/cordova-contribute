# Deprecation and Archiving

[Apache Cordova's Deprecation Policy](https://cordova.apache.org/deprecation_policy.html) defines why, when and how Cordova projects are deprecated and archived. These are the steps to be taken by a contributor to "execute" such an deprecation:

## Deprecating or Archiving a Repository


### 1. Vote

Similar to other important decisions, Apache Cordova uses a [voting process](https://www.apache.org/foundation/how-it-works.html#decision-making) on deprecations and archiving of components. If you intend to deprecate or archive a component or repository, send an email to the [appropriate mailing list](https://cordova.apache.org/contact/) describing the intended action and start a vote on it.  

Only proceed if the vote succeeds.

### 2. Document deprecation in [`cordova-deprecated`](https://github.com/apache/cordova-deprecated)

Document the deprecation of the component in [`cordova-deprecated`](https://github.com/apache/cordova-deprecated) by editing the `README.md`. You can include information as the the reason for deprecation, a link to the deprecation announcement, links to vital forks, alternatives etc.

### 3. Make changes in `README.md`

Add the [Deprecation Notice Template](#deprecation-notice) to the `README.md` of the project. Make sure the template is adapted to the specific component as described.

### 4. Archiving only: Close Issues and Pull Requests

As archiving will make Issues and Pull Requests read only, it is common and [suggested by GitHub](https://help.github.com/articles/about-archiving-repositories/) to clean up issues and pull requests before archiving a repository. If there are open issues or PRs with the component's repository, please close them with the [suggested Issue and Pull Request closing text](#suggested-issue-and-pull-request-closing-text) or similar. 

### 5. Request GitHub repository changes from Apache INFRA

A PMC member has to [open an issue with Apache INFRA](https://issues.apache.org/jira/browse/INFRA) to request changes to a GitHub repository.

For deprecation:

1. Make sure the deprecation notice is in `README.md` and contains all information.
1. [Open an issue](https://issues.apache.org/jira/browse/INFRA) and request that the repository description is prefixed with `[DEPRECATED] `.

For archiving:

1. Make sure the deprecation notice is in `README.md` and contains all information.
1. Make sure there are no more open Issues and Pull Requests for this repository.
1. [Open an issue](https://issues.apache.org/jira/browse/INFRA) and request that   
  a) the repository description is prefixed with `[DEPRECATED] ` and   
  b) the repository is archived on GitHub.

### 6. Announce

Announce the successful execution of all deprecation and/or archiving actions to your fellow Apache Cordova PMC members and developers on the [appropriate mailing list](https://cordova.apache.org/contact/). Thanks!


## Templates

### Deprecation Notice

This template is to be used in the `README.md` of depreacted components. The "Learn more" link should be customized to link to the corresponding headline in [`cordova-deprecated`](https://github.com/apache/cordova-deprecated) (replace `xyz` with the correct link anchor).

---
📌 **Deprecation Notice**

This repository is deprecated and no more work will be done on this by Apache Cordova. You can continue to use this and it should work as-is but any future issues will not be fixed by the Cordova community.

Feel free to fork this repository and improve your fork. Existing forks are listed in [Network](network) and [Forks](network/members).

- Learn more: https://github.com/apache/cordova-deprecated#xyz
---

#### Markdown

```markdown
---
📌 **Deprecation Notice**

This repository is deprecated and no more work will be done on this by Apache Cordova. You can continue to use this and it should work as-is but any future issues will not be fixed by the Cordova community.

Feel free to fork this repository and improve your fork. Existing forks are listed in [Network](network) and [Forks](network/members).

- Learn more: https://github.com/apache/cordova-deprecated#xyz
---
```

### Suggested Issue and Pull Request closing text

We are archiving this repository following [Apache Cordova's Deprecation Policy](https://cordova.apache.org/deprecation_policy.html). We will not continue to work on this repository. Therefore all issues and pull requests are being closed. Thanks for your contribution.

#### Markdown

```markdown
We are archiving this repository following [Apache Cordova's Deprecation Policy](https://cordova.apache.org/deprecation_policy.html). We will not continue to work on this repository. Therefore all issues and pull requests are being closed. Thanks for your contribution.
```
