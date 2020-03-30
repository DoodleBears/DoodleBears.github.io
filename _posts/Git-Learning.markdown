---
layout: post
title:  "Git Learning"
date:   2020-03-30 21:19:51 +0800
categories: Git
---

# Git Learning
:::info
主要存储学习Git的一些笔记
:::
###### tags: `Git` `编程`
<style>
.hui_Color{
   color:rgba(215, 58, 38, .95)!important;
}
</style>
# codecademy - Learn Git

## English

 - let’s solidify your new skills even more.
     - solidify: make sth. solid

## Git Workflow
A Git project can be thought of as having three parts:

1. **A Working Directory:** where you’ll be doing all the work: creating, editing, deleting and organizing files
2. **A Staging Area:** where you’ll list changes you make to the working directory

![](https://i.imgur.com/MEZpfFF.png)

3. **A Repository:** where Git permanently stores those changes as different versions of the project

The Git workflow consists of editing files in the working directory, adding files to the staging area, and saving changes to a Git repository. In Git, we save changes with a commit


## git command

 - `git init` creates a new Git repository
 - `git status` inspects the contents of the working directory and staging area
 - `git add` adds files from the working directory to the staging area
 - `git diff` shows the difference between the working directory and the staging area
 - `git commit` permanently stores file changes from the staging area in the repository
 - `git log` shows a list of all previous commits

---

 - `git checkout HEAD filename` Discards changes in the working directory.
 - `git reset HEAD filename` Unstages file changes in the staging area.
 - `git reset commit_SHA` Resets to a previous commit in your commit history.

---

 - `git branch` Lists all a Git project’s branches.
 - `git branch branch_name` Creates a new branch.
 - `git checkout branch_name` Used to switch from one branch to another.
 - `git merge branch_name` Used to join file changes from one branch to another.
 - `git branch -d branch_name` Deletes the branch specified.

---

 - `git clone` Creates a local copy of a remote.
 - `git remote -v` Lists a Git project’s remotes.
 - `git fetch` Fetches work from the remote into the local copy.
 - `git merge origin/master` Merges origin/master into your local branch.
 - `git push origin <branch_name>` Pushes a local branch to the origin remote.


### <span class="hui_Color">`git init`</span>
init means initialize.
> used to set up all the tools that Git needs to begin tracking changes made to the project.

```
git remote add origin https://github.com/your-user-name/your-user-name.github.io.git
```
### <span class="hui_Color">`git status`</span>
> used to check the status of your project's content(if they were changed).
 - untracked files
     - Git sees the file but has not started to tracking changes yet.
     - use git add (file_name) will let git start to track the specific file

![](https://i.imgur.com/OkspSNF.png)

### <span class="hui_Color">`git add filename`</span>
filename such as scene-1.txt
> used to let git start to track the specific file(in order to track this file, the file needs to be added to the staging area)

`git add file_1 file_2`可以一次性add多个文件

![](https://i.imgur.com/JlkQQdH.png)

### <span class="hui_Color">`git diff`</span>
> used to check the difference between the working directory and the staging area.

**In the Output**
 - Changes to the file are marked with `a` + and are indicated in green.

![](https://i.imgur.com/mvtqQXI.png)

### <span class="hui_Color">`git commit`</span>
the option `-m` followed by a message which used to describe the commit

> used to permanently store changes from the staging area inside the repository.
 - Must be in quotation marks
 - Written in the present tense
 - Should be brief (50 characters or less) when using `-m`

### <span class="hui_Color">`git log`</span>
> used to see the commit in the repository

![](https://i.imgur.com/mdiPoyq.png)

**In the Output**
 - A 40-character code, called a SHA, that uniquely identifies the commit. This appears in orange text.
 - The commit author (you!)
 - The date and time of the commit
 - The commit message

### <span class="hui_Color">`git show HEAD`</span>
> similar to `git log` but only show the `HEAD` commit

use `git checkout HEAD` to check which file was modified in the HEAD now.

### <span class="hui_Color">`git checkout HEAD file_name`</span>

**有时候我们需要reset到某一个commit，然后使用checkout，复原回当时的情况（code）**
![](https://i.imgur.com/2iwlWyl.png)

![](https://i.imgur.com/6PrCSx6.png)

> equals to 
```
git checkout -- filename 
```
What if you decide to change the ghost’s line in the working directory, but then decide you **wanted to discard that change**?

> used to restore the file in your working directory to look exactly as it did when you last made a commit.

```
$ git add text.txt
$ git commit -m “First save, null”
```
此时 文件内容为空

---

1. 修改内容，新增一行文本“Version 0.0.1”
2. 将修改提交到暂存区
```
$ git add test.txt
```

1. 第二次修改内容，新增文本“Version 0.0.2”
2. 不提交内容

3个情况下的文件内容为：
 - 空
 - Version 0.0.1
 - Version 0.0.1
   Version 0.0.2



1. `git checkout HEAD`
> 结果：文件内容为空

暂存区`staging`的文件没了，工作区`working directory`的文件被上次提交commit的文件换掉了。【回到上次`git commit`的file】
即上次 git commit -m 时的内容：**空**

2. `git checkout`
> 结果：文件内容为:"Version 0.0.1"

用暂存区`staging`中filename文件来覆盖工作区`working directory`中的filename文件。相当于撤销自上次执行git add filename (内容为：Version 0.0.1)以来的本地修改。【回到上次`git add`的file】

### <span class="hui_Color">`git reset HEAD file_name`</span>

> unstage that file from the staging area

![](https://i.imgur.com/fe3DCjR.png)


ignore some change you made to be commited to repository?

### <span class="hui_Color">`git reset commit_SHA`</span>

> Just like retracing your steps on that hike, Git enables you to rewind to the part before you made the wrong turn.

回到之前的某个时间点
![](https://i.imgur.com/qOB0CxH.png)
Before reset:
- HEAD is at the most recent commit

After resetting:
- HEAD goes to a previously made commit of your choice
- The gray commits are no longer part of your project
- You have in essence rewound the project’s history

The commits that came after the one you reset to are gone. The HEAD commit has been reassigned. 

---

### <span class="hui_Color">`git branch`</span>

> check which branch I am on now(view all the branches)

![](https://i.imgur.com/3t1elCu.png)

#### branching overview
![](https://i.imgur.com/kWpiytN.png)
 - The circles are commits, and together form the Git project’s commit history.
 - New Branch is a different version of the Git project. It contains commits from Master but also has commits that Master does not have.

### <span class="hui_Color">`git branch new_branch`</span>

> To create new branch

![](https://i.imgur.com/3dPBFHE.png)

### <span class="hui_Color">`git checkout branch_name`</span>

>switch to the new branch
![](https://i.imgur.com/uanpVnz.png)

 - The commits you see were all made in the `master` branch. `fencing` inherited them.
 - This means that every commit `master` has, `fencing` also has.

### <span class="hui_Color">`git merge branch_name`</span>

> include all the changes made to the fencing branch on the master branch

 - Your goal is to update `master` with changes you made to `fencing`.
 - `fencing` is the **giver** branch, since it provides the changes.
 - `master` is the **receiver** branch, since it accepts those changes.

> The merge is a “fast forward” because Git recognizes that fencing contains the most recent commit.
> ![](https://i.imgur.com/hjNW2nD.png)

### <span class="hui_Color">merge conflict</span>

You’ve made commits on separate branches that alter the same line in conflicting ways. Now, when you try to merge `fencing` into `master`, Git will not know which version of the file to keep.

### <span class="hui_Color">`git branch -d branch_name`</span>

In Git, branches are usually a means to an end. You create them to work on a new project feature, but the end goal is to merge that feature into the `master` branch. After the branch has been integrated into `master`, it has served its purpose and can be deleted.

## <span class="hui_Color">Git Teamwork</span>

> - A complete replica of the project on your own computers
> - A way to keep track of and review each other’s work
> - Access to a definitive project version

### <span class="hui_Color">`git clone remote_location clone_name`</span>

In this command:
- `remote_location` tells Git where to go to find the remote. This could be a web address, or a filepath, such as:```/Users/teachers/Documents/some-remote```
- `clone_name` is the name you give to the directory in which Git will clone the repository.

### <span class="hui_Color">`git remote -v`</span>
> see a list of a Git project’s remotes

![](https://i.imgur.com/BGNDA7j.png)

### <span class="hui_Color">`git fetch`</span>
Sally changed the science-quizzes Git project in some way. If so, your clone will no longer be up-to-date.

An easy way to see if changes have been made to the remote and bring the changes down to your local copy is with:

```
git fetch
```

> It brings those changes onto what’s called a remote branch.

### <span class="hui_Color">`git merge`</span>

Your local master branch has not been updated yet, so you can’t view or make changes to any of the work she has added.

> new commits are on the origin/master branch

```
git merge origin/master
```

### <span class="hui_Color">Teamwork Workflow</span>


The workflow for Git collaborations typically follows this order:

1. etch and merge changes from the remote
2. Create a branch to work on a new project feature
3. Develop the feature on your branch and commit your work
4. Fetch and merge from the remote again (in case new commits were made while you were working)
5. Push your branch up to the remote for review

### <span class="hui_Color">`git push`</span>

```
git push origin your_branch_name
```
![](https://i.imgur.com/CW3DEup.png)
