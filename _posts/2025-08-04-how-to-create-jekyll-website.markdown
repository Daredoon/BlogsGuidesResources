---
layout: post
read_time: true
show_date: true
title:  How to Create Jekyll Website Part 1
date:   2025-08-04 16:44:00 +0800
description: Creating Jekyll based website on the go.
img: posts/20210210/Game_of_Life.jpg
tags: [website, github pages, jekyllm, blogging, tutorial]
author: Amrit Dhakal
github:  github/repo/
mathjax: yes
---

# **Creating a Jekyll Website Using rbenv on Linux (Step-by-Step Guide)**  

This tutorial will guide you through setting up a **Jekyll static website** using **rbenv** (Ruby environment manager) on Linux (tested on Arch, Ubuntu, and Fedora).  

---

## **Prerequisites**  
- A Linux-based OS (Arch, Ubuntu, Fedora, etc.)  
- Basic terminal knowledge  
- Git (for version control)  

---

## **Step 1: Install rbenv and Ruby**  

### **1.1 Install rbenv and ruby-build**  
```bash
# On Arch Linux
sudo pacman -S rbenv ruby-build

# On Ubuntu/Debian
sudo apt update
sudo apt install rbenv ruby-build

# On Fedora
sudo dnf install rbenv ruby-build
```

### **1.2 Add rbenv to your shell**  
Add these lines to `~/.bashrc` or `~/.zshrc`:  
```bash
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```
Then reload your shell:  
```bash
source ~/.bashrc  # or source ~/.zshrc
```

### **1.3 Install a Ruby version (e.g., 3.3.0)**  
```bash
rbenv install 3.3.0
rbenv global 3.3.0  # Set as default
```
Verify Ruby is installed:  
```bash
ruby -v  # Should show Ruby 3.3.0
```

---

## **Step 2: Install Jekyll and Bundler**  

### **2.1 Install Jekyll & Bundler**  
```bash
gem install jekyll bundler
```
Verify installation:  
```bash
jekyll -v  # Should show Jekyll version
```

### **2.2 Fix Missing Dependencies (if any)**  
Some Ruby 3.4+ systems require extra gems:  
```bash
gem install erb logger forwardable base64
```

---

## **Step 3: Create a New Jekyll Site**  

### **3.1 Generate a New Site**  
```bash
jekyll new my-jekyll-site
cd my-jekyll-site
```

### **3.2 Install Dependencies**  
```bash
bundle install
```

---

## **Step 4: Configure Jekyll for Local Development**  

### **4.1 Edit `_config.yml` (Optional)**  
Open `_config.yml` and modify:  
```yaml
title: My Awesome Site
description: A Jekyll-powered blog
theme: minima  # Default theme
```

### **4.2 Run Jekyll Locally**  
```bash
bundle exec jekyll serve --livereload
```
- Your site will be available at:  
  **👉 http://localhost:4000**  

---

## **Step 5: Customize Your Site**  

### **5.1 Change Themes (Optional)**  
Edit `Gemfile` and add a theme (e.g., **Minimal Mistakes**):  
```ruby
gem "minimal-mistakes-jekyll"
```
Then update:  
```bash
bundle install
```
Update `_config.yml`:  
```yaml
theme: minimal-mistakes-jekyll
```

### **5.2 Add New Posts**  
Create a new Markdown file in `_posts/`:  
```bash
echo "---
title: 'My First Post'
date: $(date +'%Y-%m-%d')
---" > _posts/$(date +'%Y-%m-%d')-my-first-post.md
```

---

## **Step 6: Deploy to GitHub Pages (Optional)**  

### **6.1 Initialize Git**  
```bash
git init
git add .
git commit -m "Initial Jekyll setup"
```

### **6.2 Push to GitHub**  
1. Create a new repo on GitHub (e.g., `username.github.io`)  
2. Push your site:  
```bash
git remote add origin https://github.com/username/username.github.io.git
git push -u origin main
```
3. Enable **GitHub Pages** in repo settings (under `Pages`).  

---

## **Troubleshooting**  

### **1. `rbenv: command not found`**  
Ensure `rbenv` is in your `PATH` (check `~/.bashrc` or `~/.zshrc`).  

### **2. `Jekyll serve` fails with missing gems**  
Run:  
```bash
bundle install
bundle exec jekyll serve
```

### **3. `Cannot load such file -- erb`**  
Install missing Ruby core libraries:  
```bash
gem install erb logger forwardable
```

---

## **Conclusion**  
You now have a **fully functional Jekyll website** running locally with `rbenv`!  

### **Next Steps**  
- [Explore Jekyll Themes](https://jekyllthemes.io/)  
- [Learn Markdown for posts](https://www.markdownguide.org/)  
- [Deploy to Netlify/Vercel](https://jekyllrb.com/docs/deployment/)  

🚀 **Happy blogging!** 🚀