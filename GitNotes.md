#  A Comprehensive Git and GitHub Tutorial

## Chapter 1: First Steps with Git

1. Open your terminal and navigate to your project folder.

2. Initialize your first Git repository:

   ```bash
   git init
   ```

3. Create a file called "story.txt" and add your first line, "Once upon a time..."

4. Stage your changes:

   ```bash
   git add story.txt
   ```

5. Make your first commit:

   ```bash
   git commit -m "Begin Lina's story"
   ```

6. Check the status of your repository:

   ```bash
   git status
   ```

7. View your commit history:

   ```bash
   git log
   ```

## Chapter 2: Branching

1. Create a new branch to explore a plot twist:

   ```bash
   git branch plot-twist
   ```

2. Switch to your new branch:

   ```bash
   git checkout plot-twist
   ```

3. Make changes to "story.txt" and commit them:

   ```bash
   git add story.txt
   git commit -m "Add a plot twist"
   ```

4. Merge your plot twist into the main story:

   ```bash
   git checkout main
   git merge plot-twist
   ```

## Chapter 3: Collaborate on GitHub

1. Create a GitHub repository.

2. Configure Git with your username and email:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your@email.com"
   ```
   Set Personal access token (PAT)

   On GitHub, goto "Settings" > Developer settings > Personal access tokens > Tokens (classic) > Generate new token (classic)
   Copy & save the newly generated token in a notepad

3. Connect your local repository to GitHub (replace `<username>` and `<token>` with your GitHub username and personal access token):

   ```bash
   git remote add origin https://github.com/lina/story.git
   git remote set-url origin https://<username>:<token>@github.com/lina/story.git
   git push -u origin main
   ```

4. Your friend, Alex, can contribute to your story by forking your repository on GitHub and cloning it locally:

   ```bash
   git clone https://github.com/alex/story.git
   ```

5. Alex makes changes, commits them, and pushes to his forked repository:

   ```bash
   echo "Improve the story ending" >> story.txt
   git add story.txt
   git commit -m "Improve the story ending"
   git push origin main
   ```

6. Alex creates a pull request on GitHub for you to review and merge.

7. After merging the pull request, pull the latest changes to your local repository:

   ```bash
   git pull origin main
   ```

## Chapter 4: Pull Requests

1. Open your project on GitHub and click on the "Pull requests" tab.

2. Click "New pull request".

3. Compare changes between branches (e.g., main and feature-branch).

4. Add a title and description for your pull request, then click "Create pull request".

5. Review comments and code changes.

6. Merge the pull request once it's reviewed and approved:

   ```bash
   git pull origin main
   ```

## Chapter 5: Time Travel with Git
. Use `git stash` to save unfinished changes:

   ```bash
   git stash
   ```

2. Later, apply the stashed changes:

   ```bash
   git stash apply
   ```

3. Travel to a specific commit using `git checkout`:

   ```bash
   git checkout <commit-hash>
   Note: refer recovery process at the end of this notes for a demo
   ```

4. Cherry-pick a specific commit from one branch to another:

   ```bash
   git checkout main
   git cherry-pick <commit-hash>
   ```
1

## Chapter 6: Troubleshooting with Git

1. Use `git reflog` to view the history of your repository:

   ```bash
   git reflog
   ```

2. Recover a deleted commit by checking out the corresponding commit hash from the reflog:

   ```bash
   git checkout <commit-hash>
   git branch recovered-branch
   ```

3. Use `git bisect` to find the commit that introduced a bug:

   ```bash
   git bisect start
   git bisect bad
   git bisect good <good-commit-hash>
   ```

4. Test each commit Git presents and mark it as "good" or "bad" until the buggy commit is found.

5. End the bisect session:

   ```bash
   git bisect reset
   ```


## Chapter 7: Handling Merge Conflicts

1. Create a new branch for a new change:

   ```bash
   git branch new-change
   git checkout new-change
   ```

2. Make changes to "story.txt" and commit them:

   ```bash
   echo "Lina met a dragon." >> story.txt
   git add story.txt
   git commit -m "Add dragon encounter"
   ```

3. Switch back to the main branch and make conflicting changes:

   ```bash
   git checkout main
   echo "Lina found a treasure." >> story.txt
   git add story.txt
   git commit -m "Add treasure discovery"
   ```

4. Attempt to merge the new change into the main branch:

   ```bash
   git merge new-change
   ```

5. Resolve the conflict by editing "story.txt":

   ```plaintext
   <<<<<<< HEAD
   Lina found a treasure.
   =======
   Lina met a dragon.
   >>>>>>> new-change
   ```

6. Choose which changes to keep or combine them, then stage and commit the resolution:

   ```bash
   git add story.txt
   git commit -m "Resolve merge conflict between treasure and dragon"
   ```

## Chapter 8: GitLens Essentials

GitLens is a powerful extension for Visual Studio Code that enhances Git capabilities. Here are some main concepts:

- Installation:
  - Install GitLens from the Visual Studio Code Marketplace.
- Blame Annotation:
  - View who made changes to the current line or block of code.
  - Hover over a line of code to see the author, commit message, and time of the change.
- File History:
  - View the commit history of a file.
  - Right-click on a file and select "GitLens: Show File History".
- Line History:
  - View the commit history of a specific line or block of code.
  - Right-click on a line and select "GitLens: Show Line History".
- Diff Comparison:
  - Compare changes between commits, branches, or your working directory.
  - Use the "GitLens: Compare" command to start a comparison.
- Commit Details:
  - View detailed information about a specific commit.
  - Hover over a commit in the GitLens sidebar to see its details.

## refer gitlense to see the difference.

## understand git recovery process

```
Understanding git checkout and Detached HEAD
When you use git checkout to switch to a specific commit, you can end up in a "detached HEAD" state. This means that your HEAD is pointing directly to a specific commit rather than to the latest commit on a branch. Let's break this down with a diagram and an explanation.

Diagram: Branch and Detached HEAD States
Initial State:
plaintext
Copy code
   A -- B -- C -- D -- E (HEAD -> master)
The branch master is pointing to commit E.
HEAD points to the same commit as master.

Scenario 1: Checking out a specific commit (detached HEAD state):
plaintext
Copy code
   A -- B -- C -- D -- E (master)
               ^
               |
            (HEAD)
You checkout commit C.
HEAD now points directly to commit C, not to any branch.

Scenario 2: Creating a new branch from a specific commit:
plaintext
Copy code
   A -- B -- C -- D -- E (master)
               |
               F (HEAD -> new-branch)
You create a new branch new-branch from commit C.
HEAD now points to new-branch.
Any new commits you make will be part of new-branch.

Scenario 3: Moving master branch to a specific commit:
plaintext
Copy code
   A -- B -- C -- D (HEAD -> master)
               |
               E
You move the master branch to point to commit C.
HEAD points to master and master points to commit C.
This effectively makes master and HEAD point to commit C.

Explanation
Checking Out a Specific Commit (Detached HEAD State):

git checkout C
plaintext
Copy code
   A -- B -- C -- D -- E (master)
               ^
               |
            (HEAD)
You checkout commit C.
HEAD now points directly to commit C, not to any branch.
You are in a detached HEAD state, meaning any new commits you make won't belong to any branch.
Creating a New Branch from a Specific Commit:

git checkout -b new-branch
plaintext
Copy code
   A -- B -- C -- D -- E (master)
               |
               F (HEAD -> new-branch)
You create a new branch new-branch from commit C.
HEAD now points to new-branch.
Any new commits you make will be part of new-branch.
Moving master Branch to a Specific Commit:

git checkout master
git reset --hard C

   A -- B -- C -- D (HEAD -> master)
               |
               E
You move the master branch to point to commit C.
HEAD points to master and master points to commit C.
This effectively makes master and HEAD point to commit C.
Recovering Deleted Files on the Same Branch
If you want to recover deleted files and commit them on the same branch without entering a detached HEAD state, follow these steps:

Checkout the Commit where the Files Were Last Present:


git checkout <commit-id>
This will put you in a detached HEAD state.

Copy the Deleted Files to a Safe Location:


cp -r . /path/to/safe/location
Switch Back to Your Original Branch:


git checkout master
Copy the Files Back to Your Working Directory:


cp -r /path/to/safe/location/* .
Add and Commit the Recovered Files:


git add .
git commit -m "Recovered all deleted files"
Visualizing the Process
Initial State:

   A -- B -- C -- D -- E (HEAD -> master)
Check out specific commit (detached HEAD state):
plaintext
Copy code
   A -- B -- C -- D -- E (master)
               ^
               |
            (HEAD)
Copy files, switch back to master:
plaintext
Copy code
   A -- B -- C -- D -- E (HEAD -> master)
Copy files back to working directory and commit:
plaintext
Copy code
   A -- B -- C -- D -- E -- F (HEAD -> master)
Summary
Checking out a specific commit can put you in a detached HEAD state.
In a detached HEAD state, you can make changes and commit, but these commits won't belong to any branch unless you create a new branch or merge them back into an existing branch.
To recover deleted files and commit them on the same branch, you can checkout the commit, copy the files to a safe location, switch back to the branch, and then add and commit the recovered files.
```

## Assignment 
## Demo of git fetch.
go to github do some changes to a file online.
```
git fetch

```

Scenarios
1> Create a repo in github and clone it do changes and push changes.
2> Fork a repo, clone it , done changes, push changes, PR request.
3> Cloned repo, 1,2,3,4,5,6 commit. Remove commit 6 completely.
4> Cloned repo, 1,2,3,4,5,6 commit.. retain commit 6, but move head to 5.
5> Git stash

List of Commands used.

- `git init`
- `git add`
- `git commit -m`
- `git status`
- `git log`
- `git branch`
- `git checkout <branch>`
- `git merge`
- `git config --global user.name`
- `git config --global user.email`
- `git remote set-url origin https://<username>:<token>@github.com/lina/story.git`
- `git push -u origin`
- `git clone`
- `git pull`
- `git stash`
- `git stash apply`
- `git checkout <commit-hash>`
- `git cherry-pick`
- `git reflog`
- `git reset --hard`
- `git fetch`

```
1. Initial Setup
Initialize a Git repository:


git init
Configure Git with your username and email:
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

2. First Commit
Create and add a file:


echo "Once upon a time..." > story.txt
git add story.txt
Commit the changes:


git commit -m "Begin Lina's story"
Check the status of the repository:


git status
View the commit history:


git log
3. Working with Branches
Create a new branch:


git branch plot-twist
Switch to the new branch:


git checkout plot-twist
Make changes, add, and commit:


echo "A surprising twist!" >> story.txt
git add story.txt
git commit -m "Add a plot twist"
Merge the new branch back into the main branch:

git checkout main
git merge plot-twist
4. Connecting to GitHub
Set the remote URL (with authentication token):


git remote set-url origin https://<username>:<token>@github.com/lina/story.git
Push the local repository to GitHub:


git push -u origin main
5. Collaborating
Clone the repository (another collaborator):


git clone https://<username>:<token>@github.com/lina/story.git
Make changes, add, commit, and push:

echo "Adding more details..." >> story.txt
git add story.txt
git commit -m "Enhance the story"
git push origin main
Pull the latest changes:


git pull origin main
6. Working with Stash
Stash changes:


echo "Unfinished work..." >> story.txt
git stash
Apply stashed changes:


git stash apply
7. Exploring History and Recovery
Checkout a specific commit:


git checkout <commit-hash>
Cherry-pick a specific commit:


git cherry-pick <commit-hash>
View the reflog:


git reflog
Reset to a specific commit:


git reset --hard <commit-hash>
8. Fetching Updates
Fetch changes from the remote repository:

git fetch
```
