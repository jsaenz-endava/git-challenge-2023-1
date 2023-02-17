# **Content**

1. [What is GitFlow and getting started](./Intro%20to%20Git%20Flow.md)
2. [`Develop` and `main` branches](./)
3. [`Features` branches](./)
4. [`Release` branches](./) 
5. [`Hotfix` branches](./)
6. [A summary of GitFlow](./A%20Summary%20of%20Git%20Flow.md) 
7. Troubleshooting examples (_here_)


# **Troubleshooting examples**

While learning about version control, `git-flow`, and working out how to use `Git`, we made a couple mistakes and had a few scares. Here's how we fixed them: 

## Delete accidental branches 
If you mistakenly create a branch from where you shouldn't (as we did in the beginning in our local repositories), it's easy to fix the problem. Using `git`
``` bash
git branch -d localBranchName
```
In case you have already pushed the branch to the remote repository, there is also a fix, it is possible to use
``` bash
git push origin --delete remoteBranchName
```
and you're good to go!

## Can't find your files? 
At one point early in the writing of this tutorial I had a scare because "suddenly" the file I was working on was deleted in the text editor, and when I went to check the project folder in a complete panic, indeed it wasn't there. After consulting with my colleagues, I realized that at some point I changed branches, got distracted, and when I came back I didn't check it. One way to prevent this from happening is to check the status of your repository every time you sit down to work. With `git`
``` bash
 git status
```
Once you know which branch you're standing on, you can either open the files, or switch to the branch with the files you want to work on using a git switch, which looks like
```bash
 git switch BranchName
```
No more scares!
