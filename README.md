# Git Flow Workplan

Guide for developers for the project's git flow strategy.


## Merge Request Description Template:

```

### What?
Explain the changes you’ve made. Reference all relevant Youtrack tickets
here

### Why?
Tells us what business or engineering goal this change achieves.

### How?
- Summary of changes / thought process regarding the change
- For backend, mention specific routes added/affected by the code change
- Indicate new packages if added

### Others
Some possible tech debts, architectural change, or refactoring on
similar modules

```



## Create long-lived branches

For every start of sprint, branch out from production branch to create, develop and release branches

Syntax:
* sp-<SPRINT_NUMBER>/<CATEGORY></TICKET_NAME>/<ENVIRONMENT>


Example:
* sp-10/feature/FOP2-999/develop
* sp-10/feature/FOP2-999/STG (for merging to STAGING)
* sp-10/feature/FOP2-999/PROD (for merging to release branch)


## Create long-lived branches

Composing branches should be categorized by their purpose, so it will be easier to know what the branch is about when reviewing the commit history or when doing code reviews.

* Feature: feature/FOP2-999
* Bug Fix: fix/ FOP2-999
* Refactor: refactor/FOP2-999
* Cleanup: cleanup/FOP2-999
* Config: config/FOP2-999


## Commits

[Commitizen](https://commitizen-tools.github.io/commitizen/) assumes your team uses a standard way of committing rules and from that foundation, it can bump your project's version, create the changelog, and update files.

We use Committizen to format our git commits, this is to standardize our commit messages to make them more human-readable and easy to comprehend during code reviews.



## Merging

Once your feature is ready to be merged, create a duplicate branch suffixed by whichever you'd like to merge to:


* To feature-branch = sp-9/feature/FOP2-999/LOCAL
* To staging = sp-9/feature/FOP2-999/STG
* To Production = sp-9/feature/FOP2-999/PRD


## Steps to follow when merging:

* Checkout to staging branch (develop)
* Pull the latest changes on your staging branch (develop)
* Checkout to your feature branch
* Branch out from your feature and add the prefix STG at the name of the branch name
* Merge staging branch (develop) to your develop (STG) branch
* Before pushing your branch to the remote always code scan your branch
* Proceed to pushing if there are not introduced errors from the ESLINT scanning

In hindsight it should look something like this:

```
git checkout develop
git pull origin develop
git checkout ${feature_branch_name}
git checkout -b ${feature_branch_name}/STG
git merge develop
yarn lint (SCQS report scanning)
git push origin ${feature_branch_name}/STG

```

## Git Flow Diagram:

![Screenshot 2023-08-15 at 11 51 32 AM](https://github.com/GavinSalcedo/gitflow/assets/30141651/2511b724-6a0d-4dec-8a60-c5097cc6efd0)


## Code Reviews

* Before merging, all devs should conduct code reviews
* Meetings should only be conducted if necessary. Maximize usage of Gitlab for Code Reviews
* After getting approval from at least minimum of 1 developer(s), merging can proceed
* Code review and merging should always be top priority to speed up QA testing delivery
