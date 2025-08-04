---
layout: post
read_time: true
show_date: true
title:  How to Create Jekyll Websites Part 2
date:   2025-08-04 17:51:00 +0800
description: Creating github pages from exitsting jekyll themes
img: posts/20210210/Game_of_Life.jpg
tags: [coding, python]
author: Amrit  Dhakal
github: daredoon/Jekyll/
---

### Creating github pages from exitsting jekyll themes

- Search and find a repository theme you like
- Fork or clone it to the local machine
- Edit the main parts to see the changes
- Use installed jekyll and ruby to see changes locally
- After enough changes to post it on the github pages open bash terminal and use following codes
- First cd to the folder where the cloned and edited themed page is then
- Delete previous .git
 ```bash
rm rf .git
```
- Initiate new .git
```bash
git init
```
- Checkout github pages branches
```bash
git checkout -b gh-pages
```
- To see the git status of current directory
```bash
git status
```
- Stage all files and folders in the current directory to commit to github pages
```bash
git add .
```
- Initial commit
```bash
git commit -m "Initial commit"
```
- Create a empty repository in github

- Now to link the current local repository to the github repository we just created.
- Go and grab the link from the newly created empty repository the link with remote add origin - fifth line, then use following command in local repository
```bash
git remote add origin http://github.com ...
```
- Now we just push the gh-pages
```bash
git push origin gh-pages
```
- Go ahead and refresh the github repository online and we can see the files uploaded. Make sure the branch is gh-pages and the all the files are there.

- After that just goto `Settings` tab on top and then go to `Pages` tab on left where you can see the link to newly created github page as Your site is live at `https://Username.github.io/RepositoryName/`.


Video tutorial: 
https://www.youtube.com/watch?v=fqFjuX4VZmU
