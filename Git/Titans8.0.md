Create a GitHub repository.

Configure Git with your username and email:
```
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
Connect your local repository to GitHub (replace <username> and <token> with your GitHub username and personal access token):

git remote add origin https://github.com/lina/story.git
git remote set-url origin https://<username>:<token>@github.com/lina/story.git
git push -u origin main
```

Repo Already existing in Github

1> git clone <repo link ---> code>   ---> .git
2> cd folder
3> added file.txt
4> git add . 
5> git commit -m "messge"
6> push code..

### Scenrio 2 you have code locally, you  need to push to remote
1>  Create repo in remot (github.com)
2> git init
3> git remote add origin
4> git set-url...
5> git add . 
6> git commit 
7> git push....


