# 🚀 Git Push/Pull Reference Guide

This guide contains all the essential Git commands for pushing and pulling changes between your local repository and GitHub.

## 📥 **PULLING Changes (GitHub → Local)**

### **Basic Pull (when you have no local changes):**
```bash
git pull origin main
```

### **When you have local changes:**
```bash
# Step 1: Check what changes you have
git status

# Step 2: Stash your local changes (saves them temporarily)
git stash push -m "Your message here"

# Step 3: Pull from GitHub
git pull origin main

# Step 4: Choose what to do with your stashed changes
git stash list                    # See your stashed changes
git stash pop                     # Apply stashed changes back
# OR
git stash drop                    # Delete stashed changes permanently
```

## 📤 **PUSHING Changes (Local → GitHub)**

### **Basic Push Process:**
```bash
# Step 1: Check what files changed
git status

# Step 2: Add files to staging
git add .                         # Add all files
# OR
git add filename.txt              # Add specific file

# Step 3: Commit with a message
git commit -m "Your commit message here"

# Step 4: Push to GitHub
git push origin main
```

## 🔄 **Complete Workflow Examples**

### **Example 1: You made changes locally and want to push:**
```bash
git status                        # See what changed
git add README.md                 # Add specific file
git commit -m "Updated my profile information"
git push origin main              # Push to GitHub
```

### **Example 2: You made changes on GitHub and want to pull:**
```bash
git pull origin main              # Pull if no local changes
```

### **Example 3: Both you and GitHub have changes (conflict situation):**
```bash
git status                        # Check local changes
git stash push -m "My local changes"  # Save local changes
git pull origin main              # Pull GitHub changes
git stash pop                     # Apply your changes back
# Fix any conflicts if they occur
git add .                         # Add resolved files
git commit -m "Merged changes"    # Commit the merge
git push origin main              # Push final result
```

## 🛠️ **Useful Commands to Remember**

### **Checking Status:**
```bash
git status                        # See current state
git log --oneline -5              # See last 5 commits
git diff                          # See what changed
git diff filename.txt             # See changes in specific file
```

### **Stash Management:**
```bash
git stash list                    # See all stashes
git stash show stash@{0}          # See what's in a stash
git stash pop                     # Apply and remove latest stash
git stash apply                   # Apply stash but keep it
git stash drop                    # Delete latest stash
git stash clear                   # Delete all stashes
```

### **Remote Management:**
```bash
git remote -v                     # See your GitHub connection
git fetch origin                  # Download latest info (no merge)
git branch -a                     # See all branches
```

## 🚨 **Common Scenarios & Solutions**

### **Scenario 1: "Your branch is behind"**
```bash
git pull origin main
```

### **Scenario 2: "Your local changes would be overwritten"**
```bash
git stash push -m "Temporary save"
git pull origin main
git stash pop
```

### **Scenario 3: "Everything is up to date"**
```bash
# Nothing to do! You're synced.
```

### **Scenario 4: Push rejected (GitHub has newer changes)**
```bash
git pull origin main              # Pull first
git push origin main              # Then push
```

### **Scenario 5: Merge conflicts after git stash pop**
```bash
# Edit the conflicted files manually
# Look for <<<<<<< ======= >>>>>>> markers
# Choose which version to keep
git add .                         # Stage resolved files
git commit -m "Resolved conflicts"
```

## 📋 **Quick Reference Card**

### **Daily Workflow:**
1. `git status` - Check what's changed
2. `git add .` - Stage your changes  
3. `git commit -m "message"` - Commit changes
4. `git push origin main` - Push to GitHub

### **Before starting work:**
1. `git pull origin main` - Get latest changes

### **When in trouble:**
1. `git status` - See what's happening
2. `git stash push -m "save"` - Save work temporarily
3. `git pull origin main` - Get updates
4. `git stash pop` - Restore your work

## 🔍 **Understanding Git States**

```
Working Directory → Staging Area → Local Repository → Remote Repository
     (edit)           (git add)      (git commit)       (git push)
```

**Pull Direction:**
```
Remote Repository → Local Repository → Working Directory
                       (git pull)
```

## 💡 **Pro Tips**

1. **Always check status first:** `git status`
2. **Pull before you start working:** `git pull origin main`
3. **Write meaningful commit messages:** "Fix header styling" not "update"
4. **Commit often:** Small, frequent commits are better
5. **When in doubt, stash:** Better safe than sorry!
6. **Use descriptive stash messages:** `git stash push -m "WIP: adding contact form"`

## 🆘 **Emergency Commands**

### **Undo last commit (but keep changes):**
```bash
git reset --soft HEAD~1
```

### **Undo last commit (and discard changes):**
```bash
git reset --hard HEAD~1
```

### **See what you're about to pull:**
```bash
git fetch origin
git log HEAD..origin/main --oneline
```

### **Force push (use with caution!):**
```bash
git push origin main -f
```

## 📚 **Commit Message Best Practices**

### **Good commit messages:**
- "Add contact form validation"
- "Fix navigation menu on mobile"
- "Update README with installation steps"
- "Remove deprecated API calls"

### **Bad commit messages:**
- "update"
- "fix"
- "changes"
- "test"

---

**Created by:** Abhijay Shah  
**Repository:** https://github.com/Abhijayshah  
**Last Updated:** July 2025

---

> 💡 **Tip:** Keep this file handy and refer to it whenever you need to perform Git operations! 