
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
   $ echo "Adding a plot twist" >> file.txt
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
   $ echo "Initial content" > testrevert1.txt
   $ echo "Initial content" > testrevert2.txt
   $ git add .
   $ git commit -m "adding empty files"
   ```

   This creates a commit with the message "adding empty files" and adds two new files, `testrevert1.txt` and `testrevert2.txt`.

2. **Modify and Commit Changes**

   Next, we make changes to `testrevert1.txt` and `testrevert2.txt` and commit those changes:

   ```bash
   $ echo "Some changes" >> testrevert1.txt
   $ echo "Some changes" >> testrevert2.txt
   $ git add .
   $ git commit -m "Made changes in testrevert1 and testrevert2"
   ```

   This creates a new commit with the message "Made changes in testrevert1 and testrevert2".

3. **View Commit History**

   To see the commit history, use:

   ```bash
   $ git log --oneline
   ```

   You should see something like this:

   ```bash
   d6562e2 (HEAD -> main) Made changes in testrevert1 and testrevert2
   0b34283 adding empty files
   ```

4. **Revert the Last Commit**

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
   c439b6b (HEAD -> main) Revert "Made changes in testrevert1 and testrevert2"
   d6562e2 Made changes in testrevert1 and testrevert2
   0b34283 adding empty files
   ```

### Summary

By following these steps, you can effectively manage your Git repository by creating branches, making changes, merging them, and using `git revert` to undo changes when necessary. This comprehensive tutorial covers essential Git operations that will help you maintain a clean and organized project history.
