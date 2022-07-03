---
title: Git 教學 (Git Tutorial)
date: 2019-04-24
cover: /images/Git-Tutorial/git_process.jpg
thumbnail: /images/Git-Tutorial/git_process.jpg
toc: true
categories: Learning-Note-學習筆記
tags:
    - Linux
    - git
---

git 教學與筆記。

<!-- more -->

## Basic settings
```bash
git --version

git config --global user.name MeowLucian
git config --global user.email Meow.Lucian@gmail.com
git config --list
git config --global --edit
git config --global core.editor "vim"
git config --global --unset core.editor
git config --global --add safe.directory '*'

http."https://chipmaster2.qti.qualcomm.com".followRedirects true
```

## Init
```bash
git init
```

## ssh-key
```bash
cd ~/.ssh
ssh-keygen
cat id_rsa.pub
Gitlab -> Profile Settings -> SSH Keys -> 貼上
```

## Clone
```bash
git clone -b "<specific branch>" --single-branch "<git repository url>" "<local folder name>"

# Undo --single-branch clone
git config remote.origin.fetch "+refs/heads/*:refs/remotes/origin/*"
git fetch origin
```

## Add
```bash
git add "<file>"
git add -f .
```

## Status
```bash
git status .
```

## Commit
```bash
git commit -m "<commit name>"
git commit --amend
```

## Patch
```bash
git format-patch -1 <commit> -o ~/test_code/patch      # 從包含 <commit> 往前算共 1 個 commit
git format-patch -1 <commit> -o ~/ -- "<folder>"       # 只包含某 <folder> 的變化
git am test.patch
```

## Cherry-pick
```bash
git cherry-pick "<commit ID>".."<commit ID>"     # (注意第一個編號要是前一個commit)
```

## Log
```bash
git log
git log "<file>"
git log -p "<file>"
git log --all -p "<file>"    # Find from all branchs
git log --oneline -2
git log --pretty="PIC:%an, %s"
git log --grep "test"
git log --stat
git log --author=Lucian
```

## Show
```bash
git show "<commit>" --stat
git show --pretty="" --name-only "<commit>"
git show "<commit>":"<file>"
```

## Diff
```bash
git diff "<commit>" "<commit>"
git diff --stat
git diff --staged "<file>"
git diff --name-only .
```

## grep
```bash
git ls-files | fgrep "test.c"
git grep -n -i --files-with-matches "<text>"
```

## Checkout
```bash
git checkout "<file>"
```

## Reset
```bash
git reset HEAD --hard

# 還原到前一個commit
git reset HEAD^

# 還原到前二個commit
git reset HEAD^^

# 還原到前二個commit
git reset HEAD~2

git reset HEAD "<file>"

git reset "<commit>" "<file>"    # reset a specific file to a specific revision
```

## Clean
```bash
git clean -f -d
```

## Branch
```bash
git branch -a
git checkout "<new branch name>"
git branch -b "<new branch name>" "<started commit ID>"
git branch --contains "<commit>"    # find branch with specific commit

# Find <commit> in all branches
git branch -a --contains <commit>

# Delete branch
git branch -d "<branch name>"
```

## Merge
```bash
git merge "<branch name>"
```

## Remote
```bash
git remote -v
git remote add "<local nickname>" "<git repository url>"
# Local
git remote add TEST /build/lucian/Project/test

git remote remove origin
```

## Push
```bash
git push "<remote>" "<commit SHA>":"<remote branch>"
git push origin 19cbe78:master
```

## Fetch
```bash
git fetch origin
```

## Pull
```bash
git pull
```

## Rebase
```bash
git rebase -i "<commit>"

pick   "<commit_1>"
reword "<commit_2>"   # change commit name
pick   "<commit_3>"
s      "<commit_4>"   # Squash
```

## Tag
```bash
git tag
git tag -l
git tag -n
git tag "<tag ID>"      # Add new tag
git tag -d "<tag ID>"   # Delete tag
git tag -am "<tag comment>" "<tag ID>"
```

## Stash
```bash
git stash
git stash list
git stash pop
git stash drop
git stash clear
```

## Gerrit
```bash
git review -R

cat ~/.ssh/config (必須存在)
User 19002347
```

## Share the code
https://gist.github.com/

## Upgrade to latest git version
```bash
(option) sudo rm -rf /usr/share/ca-certificates
(option) sudo apt-get --reinstall install ca-certificates

sudo add-apt-repository ppa:git-core/ppa -y
sudo apt-get update
sudo apt-get install git -y
```