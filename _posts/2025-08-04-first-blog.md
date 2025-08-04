---
layout: post
read_time: true
show_date: true
title:   Deleting git branches
date:   2025-08-04 21:31:00 +0800
description:  Deleting git branches
img: posts/20210210/Game_of_Life.jpg
tags: [blogging, tutorial]
author: Amrit  Dhakal
github: daredoon/Jekyll/
---





## To completely reset your Git repository to a state with **no branches** (essentially a fresh start while keeping your files), follow these steps:

---

### **1. Delete All Branches (Including `main`/`master`)**
```bash
# Move to a temporary branch (can't delete current branch)
git checkout --orphan temp_branch

# Delete ALL branches except temp_branch
git branch | grep -v "temp_branch" | xargs git branch -D
```

### **2. Remove All Git History**
```bash
# Remove all tracked files (keeps working files)
git rm -rf .

# Remove Git metadata (except .git/config)
rm -rf .git/refs .git/objects .git/logs
```

### **3. Reinitialize Git**
```bash
# Fresh Git init (keeps your files)
git init

# Optional: Recreate main branch
git checkout -b main
```

### **4. Push to Remote (If Needed)**
```bash
# Force-push empty state (destroys remote history)
git remote add origin <your-repo-url>
git push --force origin main
```

---

### **What This Does**
- Creates a new Git history with **no branches** initially
- Preserves your working files (they become unstaged)
- Clears all commit history, tags, and branches

---

### **Alternative (Nuclear Option)**
To **completely remove Git** and start fresh:
```bash
rm -rf .git  # Deletes all Git data
git init     # New repository
```

---

### **Important Notes**
⚠️ **This is destructive!**  
- You’ll lose all branch history  
- Remote repos need `--force` pushes  
- Backup first if unsure (`cp -r project project-backup`)

---

### **After Resetting**
1. Add files:
   ```bash
   git add .
   git commit -m "Initial commit"
   ```
2. Connect to remote:
   ```bash
   git remote add origin <your-repo-url>
   git push -u origin main
   ```
