# 🔐 Git Setup & Commit Guide

**For:** Entire Development Team  
**Purpose:** Ensure proper Git workflow with new structure

---

## ✅ Git Configuration (Already Done)

### What's Configured
```
✅ .gitignore created
✅ _OLD_APP_BACKUPS/ is Git ignored
✅ VS Code settings configured
✅ Repository is clean
```

---

## 📋 For Team Members - First Time Setup

### Step 1: Clone Repository
```bash
git clone [your-repo-url]
cd opd1
```

### Step 2: See What's Included
```bash
# You'll see:
DoctorPortalApp/           ← ✅ Tracked by Git
_OLD_APP_BACKUPS/          ← ✅ Local only (not in Git)
.gitignore                 ← ✅ Configures exclusions
.vscode/                   ← ✅ Shared IDE settings
TEAM_MIGRATION_INSTRUCTIONS.md ← ✅ Team guide
```

### Step 3: Verify Git Status
```bash
git status
```

**Expected Output:**
```
On branch main
nothing to commit, working tree clean
```

**You should NOT see:**
- _OLD_APP_BACKUPS in tracked files
- Old App.js files in git status

---

## 💾 Committing Code

### ✅ DO Commit
```bash
# Good - From DoctorPortalApp
cd DoctorPortalApp
git add src/modules/appointments/components/NewComponent.js
git commit -m "feat: add new appointment component"
```

### ❌ DON'T Commit
```bash
# Bad - Don't commit old apps
git add _OLD_APP_BACKUPS/
git commit -m "..."  # ❌ This will be rejected by .gitignore

# Bad - Don't commit node_modules
git add node_modules/
git commit -m "..."  # ❌ This will be rejected by .gitignore
```

---

## 📝 Sample Git Workflow

### Daily Workflow
```bash
# 1. Start of day
git pull origin main

# 2. Create feature branch
git checkout -b feature/appointments-filter

# 3. Make changes in DoctorPortalApp/
# Edit: src/modules/appointments/components/AppointmentsList.js

# 4. Stage changes
git add DoctorPortalApp/src/modules/appointments/components/AppointmentsList.js

# 5. Commit with clear message
git commit -m "feat(appointments): add filter functionality"

# 6. Push to remote
git push origin feature/appointments-filter

# 7. Create pull request
# → On GitHub/GitLab
```

---

## 🏷️ Commit Message Guidelines

### Format
```
[type](module): description

Examples:
✅ feat(appointments): add appointment filter
✅ fix(schedule): resolve shift display bug
✅ docs(profile): update profile guide
✅ refactor(settings): reorganize settings components
```

### Types
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation
- `refactor` - Code reorganization
- `test` - Tests
- `style` - Formatting (no logic change)

### Modules (from new structure)
- `appointments` - Appointments module
- `schedule` - Schedule module
- `profile` - Profile module
- `settings` - Settings module
- `booking` - Booking module (future)
- `navigation` - Navigation system
- `core` - General/root changes

---

## 🔍 Checking Git Status

### See Current Status
```bash
git status
```

### See Commit History
```bash
git log --oneline
# Shows recent commits with short descriptions
```

### See Branches
```bash
git branch -a
# Shows local and remote branches
```

### See Diff Before Committing
```bash
git diff
# Shows all uncommitted changes
```

---

## 🚨 Troubleshooting Git

### Problem: "Can't commit _OLD_APP_BACKUPS"
**Solution:** It's in .gitignore - that's correct. Don't commit it.
```bash
# This is expected to fail:
git add _OLD_APP_BACKUPS/  # ❌ Won't work (ignored)
```

### Problem: "Git sees files I didn't change"
**Solution:** Make sure you have .vscode/settings.json applied
```bash
# Reload VS Code settings
Command Palette → "Reload Window"
```

### Problem: "I accidentally added old App.js"
**Solution:** Remove it
```bash
git reset HEAD DoctorAppointmentDashboard/App.js
git checkout -- DoctorAppointmentDashboard/App.js
```

---

## 📊 Repository Structure for Git

### What Gets Committed
```
✅ DoctorPortalApp/                  (active code)
✅ .gitignore                        (configuration)
✅ .vscode/settings.json             (team settings)
✅ TEAM_MIGRATION_INSTRUCTIONS.md    (team docs)
✅ DoctorPortalApp/*.md              (project docs)
```

### What Does NOT Get Committed
```
❌ _OLD_APP_BACKUPS/                 (git ignored)
❌ node_modules/                     (git ignored)
❌ .env                              (git ignored)
❌ build/                            (git ignored)
❌ dist/                             (git ignored)
```

---

## 🔄 Team Collaboration

### Before Starting Work
```bash
# Always pull latest code first
git pull origin main
```

### Creating a Feature Branch
```bash
# Create branch for your feature
git checkout -b feature/your-feature-name

# Make your changes
# Commit regularly with clear messages
```

### Creating a Pull Request
```bash
# Push your branch
git push origin feature/your-feature-name

# On GitHub/GitLab:
# 1. Create pull request
# 2. Add description
# 3. Request reviewers
# 4. Wait for approval
# 5. Merge to main
```

### Merging to Main
```bash
# Someone with merge permissions does:
git checkout main
git pull origin main
git merge feature/your-feature-name
git push origin main
```

---

## 📋 Pre-Commit Checklist

Before you commit, ask yourself:

- [ ] Am I committing from DoctorPortalApp/?
- [ ] Are my changes related to one logical feature?
- [ ] Have I tested my changes?
- [ ] Is my commit message clear and descriptive?
- [ ] Am I NOT accidentally committing _OLD_APP_BACKUPS/?
- [ ] Am I NOT committing node_modules/?
- [ ] Have I reviewed the diff before committing?

---

## 💡 Pro Tips

### Keep Commits Small
```bash
# Good - Small, focused commits
git commit -m "feat(appointments): add search functionality"
git commit -m "refactor(appointments): improve component structure"

# Avoid - Large, unfocused commits
git commit -m "fixed stuff and added features and updated docs"
```

### Rebase Before Merging
```bash
# Keep history clean
git fetch origin
git rebase origin/main
git push origin feature/your-feature -f  # Force push after rebase
```

### Review Before Pushing
```bash
# See what you're about to push
git log origin/main..HEAD
```

---

## 🎯 Quick Commands Reference

```bash
# Initialize/Pull
git clone [url]
git pull

# Branching
git checkout -b feature-name
git checkout main
git branch -a

# Making Changes
git status                    # See changes
git diff                      # See detailed changes
git add [file]               # Stage file
git add .                    # Stage all changes
git commit -m "message"      # Commit

# Pushing
git push origin branch-name
git push origin main

# Merging
git merge feature-name
git rebase origin/main

# Undoing
git reset HEAD [file]        # Unstage file
git checkout -- [file]       # Discard changes
git revert [commit-hash]     # Undo commit
```

---

## 🔗 Resources

- ✅ Check TEAM_MIGRATION_INSTRUCTIONS.md for general setup
- ✅ Check DoctorPortalApp/MIGRATION_GUIDE.md for code locations
- ✅ Check DoctorPortalApp/QUICK_REFERENCE.md for development

---

## ✅ Verification

### After setup, verify:
```bash
# 1. Check .gitignore is working
git status
# Should NOT show _OLD_APP_BACKUPS/

# 2. Check you can see DoctorPortalApp
ls -la
# Should show DoctorPortalApp/ and _OLD_APP_BACKUPS/

# 3. Check Git config
git config --list
```

---

**Status:** ✅ Ready for team collaboration  
**Questions?** Ask your team lead or Git admin
