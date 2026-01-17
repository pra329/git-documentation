# **Git and GitHub Documentation**

## **What is Git?**
- **Git** is a version control system that helps you track changes in files.
- It helps in managing the history of the code and merging changes from different branches.
- Before **Git** becomes mainstream there were many version control system such as SCCS (Source code control system) , Perforce , Subversion etc.

## **What is GitHub?**
- **GitHub** is a web-based hosting service for Git repositories.
- It allows developers to store, share, and collaborate on code with others.


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
  <img src="images/Git Flow.png" alt="Git Flow Diagram" width="60%"><br/>
  <em>Git Workflow</em>
</p>


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


### <u> **GitIgnore File** </u>

Git ignore file tells the git which files and folder should be ignored. It is way to prevent git from tracking certain files and folder. You can create a gitignore file and add list of files and folders to ignore.

---


### <u> **Reverting The Commits** </u>
Before understanding how to revert back the commit we must understand what is the need of reverting the commit. The below example provide the clear explanation when we need reverting the commit.

#### <u> Example </u>: 
<li> Suppose we have index.js file and we add first two line of code to index.js file and then commit the changes with the commit message "Initial Commit".</li>
<br/>

```js
const name = "Pranjal Jain"
const email="pranjaljain19a@gmail.com"
```

<li>Then after "Initial Commit" we add getName function to index.js file and commit the changes with the commit message "Added getName Function"</li>
<br/>

```js
const name = "Pranjal Jain"
const email="pranjaljain19a@gmail.com"

function getName() {
    console.log("My name is " + name);
}
```
<br/>

<li>Then after "Added getName Function" commit we add getEmail function to index.js file and commit the changes with the commit message "Added getEmail Function".</li>

<br/>

```js
const name = "Pranjal Jain"
const email="pranjaljain19a@gmail.com"

function getName() {
    console.log("My name is " + name);
}

function getEmail() {
    console.log("My email is " + Email);
}
```

<li>If we clearly see the above code we can observe that getEmail function has an error which is Email variable has not been declared. Because of this issue, we want to remove the last commit and bring the code back to the previous stable state (before adding getEmail).</li>

<br/>

<p align="center">
  <img src="images/Reverting the commit.png" alt="Git Flow Diagram" width="75%"><br/>
  <em>Commit WorkFlow</em>
</p>

<li> Here Comes reverting the commit in picture we want to revert the last commit which is Added getEmail Function because the code becomes buggy in this commit itself.</li>

<u> There are two ways for reverting the commit:</u>

### **1. `git reset --hard <CommitId>`**
- This command takes the head pointer directly to the commit which is specified in the commit id. (By default Head points to the latest commit).

- And all the commits below the head pointer will be removed.

- We will run git reset --hard 375ea2ba981ed915c4b913db6a376836fb9e4312 (Commit Id of Added getName Function). so now our head will move to the commit Added getName Function and all the below commits will be removed.

- This command permanently deletes the commit and it is dangerous if commits are alredy pushed to gitHub.

<p align="center">
  <img src="images/Reverting the commit -2.png" alt="Git Flow Diagram" width="75%"><br/>
  <em>Commit WorkFlow</em>
</p>

### **2. `git revert <commitId>`**
- This is more safe to use as compare to that of `git reset --hard <CommitId>` because in this method we does not move the head instead we revert the changes made in the commit. 

- What will happen is suppose we find that Added getEmail Function commit introduces bug to the code and we want to remove this function so we will run the command git revert 6c7bbcbec3bcd1c53e92a (Commit Id of Added getEmail Function Commit) so it will revert the changes (revert the changes means if some code is added it will be removed and if some code is removed in the commit it will again added). and this will generate new commit and we can name it as Revert Added getEmail Function Commit.

<p align="center">
  <img src="images/Reverting the commit - 3.png" alt="Git Flow Diagram" width="75%"><br/>
  <em>Commit WorkFlow</em>
</p>

### <u> Which Is the better command to use `git reset --hard <CommitId>` or `git revert <CommitId>` ?? </u>
`git revert <CommitId>` is better command to use as compared to `git reset --hard <CommitId>` because in git revert command our head pointer does not move instead the changes in the code are revert back and new commit is also created of the revert changes so history is also managed. whereas in git reset --hard command our head pointer move to the commit which we specified and all the commits below the new head will be removed so this is not considered as good practice. 

<p align="center">
  <img src="images/Reverting the commit - 4.png" alt="Git Flow Diagram" width="75%"><br/>
  <em>Commit WorkFlow</em>
</p>

- Suppose we want to remove Commit - 2 so we can not use `git reset --hard <CommitId Of Commit - 1>` Command because it will move the head pointer directly to the first commit and all the commits below will be removed permanently so our Commit - 3 and Commit - 4 will also lost.

<p align="center">
  <img src="images/Reverting the commit - 5.png" alt="Git Flow Diagram" width="75%"><br/>
  <em>Commit WorkFlow</em>
</p>

- So in order to remove Commit - 2 we have lost Commit -3 and Commit - 4 as well.

- In Such scenarion we always use `git revert <CommitId>` command and pass the commit id of Commit - 2 so the changes made in the Commit - 2 will be reverted and the new commit will also create Which can be named Revert Commit-2 and head will point to this commit now.

<p align="center">
  <img src="images/Reverting the commit - 6.png" alt="Git Flow Diagram" width="75%"><br/>
  <em>Commit WorkFlow</em>
</p>