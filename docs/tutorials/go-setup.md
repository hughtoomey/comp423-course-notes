# Setting up a dev container for Go

* Primary author: [Hugh Toomey](https://hughtoomey)
* Reviewer: [Cem Baykal](https://baykalcem)

## Features in this tutorial
* <b>Code Blocks</b> <br>
Code Blocks allow for code snippits to be highlighted and easily copied or explained.
```py title="Hello World in Python"
print("Hello World!")
```
We will use codeblocks to highlight commands and code snippets to make this tutorial easy to follow along.
* <b>Admonitions</b> <br>
Admonitions will be used to provide extra context for any steps within this tutorial
!!! note
    This is an example of an Admonition. 

## Prerequisits
1. <b>A GitHub account:</b> If you don’t have one yet, sign up at GitHub.
2. <b>Git installed:</b> <a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git">Install Git</a> if you don’t already have it.
3. <b>Visual Studio Code (VS Code):</b> Download and install it from <a href="https://code.visualstudio.com/">here</a>.
4. <b>Docker installed:</b> Required to run the dev container. <a href="https://www.docker.com/products/docker-desktop">Get Docker here.</a>
5. <b>Command-line basics:</b> Your COMP211 command-line knowledge will serve you well here. If in doubt, review the Learn a CLI text!

## Part 1: Create your repository
1. ### Create a Local Directory and Initialize Git
    1. Open your terminal or command prompt.
    2. Create a new directory for your project.
    ```
    mkdir go-project
    cd go-project
    ```
    3. Initialize a new Git repository:
    ```
    git init
    ```
    4. Create a README file:
    ```
    echo "# Go Project" > README.md
    git add README.md
    git commit -m "Initial commit with README"
    ```
2. Create a Remote Repository on GitHub
    1. Log in to your GitHub account and navigate to the <a href="https://github.com/new">Create a New Repository page</a>.
    2. Fill in the details as follows:
        - <b>Repository Name:</b> `go-project`
        - <b>Description:</b> "My first project with Go"
        - <b>Visability:</b> Public
    3. Do not initialize the repository with a README, .gitignore, or license.
    4. Click <b>Create Repository</b>
3. Link your Local Repository to GitHub
    1. Add the GitHub repository as a remote:
    ```
    git remote add origin https://github.com/<your-username>/go-project.git
    ```
    Replace &lt;your-username&gt; with your GitHub username.
    2. Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main. Old versions of git choose the name master for the primary branch, but these days main is the standard primary branch name.
    3. Push your local commits to the GitHub repository:
    ```
    git push --set-upstream origin main
    ```
    4. Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use `git log` locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.