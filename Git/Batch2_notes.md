
## Chapter 1: Setting Up Your GitHub Repository

1. **Create a GitHub Repository**

   Create a new repository on GitHub named `demo1`.

2. **Clone the Repository Locally**

   Clone the repository to your local machine:

   ```bash
   $ git clone <repo-url>
   $ cd demo1
   ```

3. **Configure Git**

   Set up your Git configuration:

   ```bash
   $ git config --global user.name "<username>"
   $ git config --global user.email "<email>"
   ```

4. **Set Remote URL with Authentication**

   Set the remote URL to include your username and token:

   ```bash
   $ git remote set-url origin https://<username>:<token>@<repo-url-without-https>
   ```

5. **Create a File Locally and Commit**

   Create a new file and add it to the repository:

   ```bash
   $ echo "Initial content" > file.txt
   $ git add .
   $ git commit -m "Initial commit with file.txt"
   ```

6. **Sync the Repository**

   Push the changes to GitHub:

   ```bash
   $ git push origin main
   ```

## Chapter 2: Branching

1. **Create a New Branch**

   Create a new branch named `plot-twist`:

   ```bash
   $ git branch plot-twist
   ```

2. **Switch to the New Branch**

   Check the current branch and switch to `plot-twist`:

   ```bash
   $ git branch
   $ git switch plot-twist
   ```

3. **Make Changes and Commit**

   Modify `file.txt` and commit the changes:

   ```bash
   # Create a file called file.txt using vscode.
   $ git add file.txt
   $ git commit -m "Add a plot twist"
   ```

4. **Merge Changes into the Main Branch**

   Switch back to the main branch and merge the changes:

   ```bash
   $ git switch main
   $ git merge plot-twist
   ```

5. **View Commit History**

   Check the commit history to see the merge:

   ```bash
   $ git log --oneline
   ```

## Chapter 3: Git Revert Tutorial

### Introduction

This tutorial will guide you through the process of using `git revert` to undo changes made by specific commits. We'll walk through a real-life example where we add and modify files, then revert those changes.

### Example Scenario

1. **Add and Commit Files**

   First, let's add and commit two new files:

   ```bash
   $ Add file revert1.txt (create using vscode ) and add some text.
  
   $ git add revert1.txt
   $ git commit -m "adding revert1.txt"
   ```

   This creates a commit with the message "adding empty files" and adds one new file, revert1.txt.



2. **View Commit History**

   To see the commit history, use:

   ```bash
   $ git log --oneline
   ```

   You should see something like this:

   ```bash
   d6562e2 (HEAD -> main) Made changes in testrevert1 and testrevert2
   0b34283 adding new file
   ```

3. **Revert the Last Commit**

   To revert the commit `d6562e2`, use:

   ```bash
   $ git revert d6562e2
   ```

   This command creates a new commit that undoes the changes introduced by `d6562e2`. The output should be similar to:

   ```bash
   [main c439b6b] Revert "Made changes in testrevert1 and testrevert2"
    2 files changed, 2 deletions(-)
   ```

5. **Verify the Revert**

   Check the commit history again:

   ```bash
   $ git log --oneline
   ```

   The history should now include the revert commit:

   ```bash
   c439b6b (HEAD -> main) Revert "Made changes in revert1"
   d6562e2 Made changes in revert1
   0b34283 adding empty files
   ```

### Summary

By following these steps, you can effectively manage your Git repository by creating branches, making changes, merging them, and using `git revert` to undo changes when necessary. This comprehensive tutorial covers essential Git operations that will help you maintain a clean and organized project history.

######

you can selectively remove the second commit in Git using an interactive rebase. Here’s how you can do it:

1. **Start an interactive rebase**:
   ```sh
   git rebase -i HEAD~3
   ```
   This will open an editor with a list of the last three commits (in reverse order). It will look something like this:

   ```
   pick <commit-hash-3> third commit
   pick <commit-hash-2> second commit
   pick <commit-hash-1> first commit
   ```

2. **Modify the commit list**:
   - Change `pick` to `drop` (or `d`) next to the commit you want to remove. In this case, change it next to the second commit:
     ```
     pick <commit-hash-3> third commit
     drop <commit-hash-2> second commit
     pick <commit-hash-1> first commit
     ```

3. **Save and exit the editor**:
   - For example, if you are using `vim`, you would press `Esc` and type `:wq` to save and quit.

4. **Git will then reapply the remaining commits**:
   - Git will reapply the `third commit` and `first commit` but skip the `second commit`.

5. **Resolve any conflicts** (if necessary):
   - If there are any conflicts during the rebase process, Git will pause and allow you to resolve them. After resolving conflicts, you can continue the rebase with:
     ```sh
     git rebase --continue
     ```

6. **Force push (if necessary)**:
   - If you have already pushed the commits to a remote repository, you will need to force push the changes:
     ```sh
     git push origin <branch-name> --force
     ```


you can tag and push your Day1 class code to Git, and then pull the code for Day1, Day2, and so on as needed. Here are the steps to do this:

### Tagging and Pushing Day1 Code to Git

1. **Commit your changes:**
   Make sure all your changes are committed.

   ```sh
   git add .
   git commit -m "Day1 class code"
   ```

2. **Tag your commit:**
   Create a tag for the Day1 code.

   ```sh
   git tag -a day1 -m "Day1 class code"
   ```

3. **Push your changes and tags to the remote repository:**
   Push the commit and the tag to your remote repository (e.g., GitHub).

   ```sh
   git push origin main --tags
   ```

### Pulling the Code for Day1, Day2, etc.

To pull the code for a specific day, you can check out the corresponding tag. Here’s how:

1. **Fetch the tags from the remote repository:**

   ```sh
   git fetch --tags
   ```

2. **Check out the specific tag:**

   ```sh
   git checkout tags/day1 -b day1-branch
   ```

This will create a new branch (`day1-branch`) based on the Day1 tag. You can do the same for Day2, Day3, etc., by replacing `day1` with the appropriate tag name.

### Example for Day2

1. **Tag your Day2 code:**

   ```sh
   git add .
   git commit -m "Day2 class code"
   git tag -a day2 -m "Day2 class code"
   git push origin main --tags
   ```

2. **Pull the Day2 code:**

   ```sh
   git fetch --tags
   git checkout tags/day2 -b day2-branch
   ```

By following these steps, you can efficiently manage and pull your code for different days using Git tags.

**Note:** Be cautious with rebasing and force pushing, especially if you are working in a shared repository, as it rewrites history and can affect other collaborators.
