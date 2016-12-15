%title: GIT Rebase Merge Squash
%author: Yisrael Dov Lebow
%date: 14th of Kislev, 5777


# VS SVN and others 

## What bad stuff can happen with SVN

An untested commit to *trunk* will make your whole project undeployable.

^
  \* - a good commit
  \* - an untested commit
  \* - a commit that we want to deploy
  
^
## How do we fix that ?

Using *branches*

^
But tracking branches is difficult in SVN ( and friends )

---
# GIT is not for backup

## GIT is for keeping a development journal

Git tells your development story.


---
## Why use command line?

Better to get to know git. 

Think about WYSIWYG HTML editors.

---
# Branching Demo

* create a repository 
* create some commits
* create some branches

Easy stuff


->  *DEMO* <- 

--- 

# Merging 

## Merging is easy with git !

Git tracks your merges and branches and the parents.

---

# Merging

 *2.5* Types of merging

 * ff
 * no-ff
 * squash 
 

---

## Fast Forward Merge 

Current branch pointer can be moved to the head of merging branch.

Keeps a linear history, but loses info about branch

`--ff-only` to stop if can't ff

---
## True merge, 2 headed, 3 way

2 branches are merged together in a *merge commit*.

Non linear history, but more verbose about changes.

`--no-ff` to force 

---

## Squash - not a real merge

Makes 1 new commit with all the changes 
of the branch squashed together.

*Throws away history.*

Can cause issues with future merges.

`--squash`

---

# Merging Demo 

* create a new branch 
* do some work 
* ff merge
* create a new branch a few commits ago
* do some work 
* merge will be no-ff
* do some work and force no-ff
* create another branch
* do some work 
* squash it

-> *DEMO* <-

---

# Sharing work

## Remotes can be anything

clone sets the origin remote automatically 

^
## tracking branches
~~~~

git checkout --track origin/branch
git checkout branch 

git checkout -b branch
git branch -u origin/branch
~~~~

---- 
## Push 



## Pull 

^
## Push and Pull are merges

Really a fetch followed by a merge

---
# REMOTES DEMO

--- 
# Git Is a time machine
Lets you go back and change history 

# Rebase

*Do not rebase commits that exist outside your repository.*

> If you follow that guideline, you’ll be fine. 
> If you don’t, people will hate you, 
> and you’ll be scorned by friends and family.

[Official Git Documentation](https://git-scm.com/book/ch3-6.html)

# Cherry pick


# The Nuclear Option: filter-branch

---


# Rebase Demo

* `--amend`
* `rebase onto another branch`
* `git rebase -i`


--- 

# Git work flows

## Git-flow

complex
good for physical releases

## GitHub Flow

simple
good for SAS

---

## GitLab Flow

simple or complex as needed 
basic for SAS
more complex for physical releases

----

# Git flow

Work is done on `develop` branch ( this is non standard )

Work flow example:

- Create branch for task `feature/JIR-123-super-feature`
- Develop branch
- When done merge into `develop`
- When ready to release 
  - make a release branch 
  - make bug-fixes
    - back-port to `master` and `develop`
  - finish release 
    - Tag

---

# GitHub Flow

* Anything in the master branch is deployable
* To work on something new, create a descriptively named branch off of master (ie: new-oauth2-scopes)
* Commit to that branch locally and regularly push your work to the same named branch on the server
* When you need feedback or help, or you think the branch is ready for merging, open a pull request
* After someone else has reviewed and signed off on the feature, you can merge it into master
* Once it is merged and pushed to ‘master’, you can and should deploy immediately

---
# GitLab Flow


Same as git hub flow with the addition of:

* Environment branches
  * Push from *master*
  * To *Pre-production* or *Staging*
  * To *Live*

Good for *CI* or  *CD*

Can use `release` branch and tags for physical product.

* Cherry-pick bug-fixes from master to 

---

All of the above use merges and not rebase

^
# Atlasian 

Same as *GitHub* but rebase to master instead of merge

nice history but ...

---

# Alternative 

##  WIP branch and cleaned branch

--

# Links for further reading

https://www.youtube.com/watch?v=O4SoB3TFkjA
https://www.youtube.com/watch?v=W39CfI3-JFc&t=2301s&list=WL&index=7
https://git-scm.com/book/ch3-6.html
http://stackoverflow.com/a/17115844/7292620
https://www.youtube.com/watch?v=o4PFDKIc2fs
https://www.youtube.com/watch?v=enMumwvLAug
https://about.gitlab.com/2014/09/29/gitlab-flow/
