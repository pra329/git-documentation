# **Git and GitHub Documentation**

## **What is Git?**
- **Git** is a version control system that helps you track changes in files.
- It helps in managing the history of the code and merging changes from different branches.
- Before **Git** becomes mainstream there were many version control system such as SCCS (Source code control system) , Perforce , Subversion etc.

## **What is GitHub?**
- **GitHub** is a web-based hosting service for Git repositories.
- It allows developers to store, share, and collaborate on code with others.

---

## **Flow of Git**

1. **Initialize Repository**
   - Use `git init` to initialize a folder as a Git working directory.
   - Git creates a hidden `.git` folder to track changes.
   - At this stage, files are not tracked.

2. **Add Files to Staging Area**
   - Use `git add <fileName>` to add files to the staging area.
   - Git starts tracking the changes made in the files.

3. **Staged Files**
   - Files present in the staging area are ready to be committed.

4. **Commit Changes**
   - Use `git commit -m "message"` to save the changes permanently.

<p align="center">
  <img src="images/Git Flow.png" alt="Git Flow Diagram" width="300"><br/>
  <em>Git Workflow</em>
</p>

---

## **Basic Git Commands**

### **1. `git init`**
- Initializes a folder as a Git repository.
- Creates the `.git` directory.

### **2. `git status`**
- Shows the current status of the working directory.
- Displays which files are staged, unstaged, or untracked.

### **3. `git add <fileName>`**
- Adds a file to the staging area.
- Git starts tracking the file.

### **4. `git restore --staged <fileName>`**
- This command is used to unstage the file from the staging area.

### **5. `git commit -m "message"`**
- Commits the staged changes with a meaningful message.
- Saves changes in Git history.
- Each commit will get a unique 40 hexadecimal character long id which is called as SHA id (Secure hash algorithm id) it help in unique identification of the commit.

### **6. `git log`**
- Show you all the commits made in the working directory 
- Use --oneline flag in order to only see the names of the commit and their id in the trimmed format.

### **7. `git diff`** 
- This command will show you the changes made in the code after the last git add command.

### **8. `git show <commitId>`**
- This command will show you the changes made in the particular commit whose id is specified.

### **9. `git blame <fileName>`** 
- Show you which line is added under which commit and author who has added this line and respective date.

---

### <u> **GitIgnore File** </u>
---
Git ignore file tells the git which files and folder show be ignored. It is way to prevent git from tracking certain files and folder. You can create a gitignore file and add list of files and folders to ignore.

---
