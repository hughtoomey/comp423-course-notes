# Setting up a dev container for Go

* Primary author: [Hugh Toomey](https://hughtoomey)
* Reviewer: [Cem Baykal](https://baykalcem)<br>
* note: some content from this tutorial is reused from an mkDocs tutorial available <a href="https://comp423-25s.github.io/resources/MkDocs/tutorial/">here</a>.


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
## Part 2: Setting Up the Development Environment
1. Add Development Container Configuration
    1. In VS Code, open the `go-project` directory. You can do this via: File > Open Folder.
    2. Install the <b>Dev Containers</b> extension for VS Code.
    3. Create a `.devcontainer` directory in the root of your project with the following file inside of this "hidden" configuration directory:
    ```
    .devcontainer/devcontainer.json
    ```
    Paste this content into your `devcontainer.json'
    ```json
    {
    "name": "Go Dev Container",
    "image": "mcr.microsoft.com/devcontainers/go:1.20",
    "customizations": {
        "vscode": {
            "settings": {},
            "extensions": [
                "golang.go"
            ]
        }
    },
    "postCreateCommand": "go mod tidy"
    }
    ```
    <b>Explanation</b>
    - `name`: The label that appears in your VS Code Dev Container environment.
    - `image`: Points directly to an existing Docker image—in this case, the official Go image on Docker Hub (golang:1.20).
        - If you need a different version, you can change the tag (e.g., golang:1.19).
    - `settings`: Custom VS Code settings inside the container (e.g., go.gopath, default shell).
    - `extensions`: Lists extensions that will be installed automatically in the container. For Go development, golang.go is essential.
    - `postCreateCommand`: Runs after the container is created. Here, go mod tidy cleans up any dependencies.
2. Reopen the Project in a VSCode Dev Container<br><br>
        Reopen the project in the container by pressing `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.<br>

    Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running go --version to see your dev container is running a recent version of Go without much effort!<br>
    Use `go version` in your terminal to confirm that you have a semi recent version of Go installed (go version go1.20.14 linux/amd64 as of Jan/26/2025)
    !!! title="Why Go?"
    Go is an open-source language developed by Google in 2007. It was designed to be simple and efficient. Go is used greatly in web-servers and cloud-services.
    
## Part 3: Creating your own project
1. Make a new directory called `hello`
```
mkdir hello
cd hello
```
2. Initialize your go module
```
go init github.com/<your username>/hello
```
3. Add a new file in the hello directory called `main.go` and write in your first program
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```
!!! title="Why main?"
While a ```main``` function is not required in Go but ```func main() {}``` is required for executables.

4. Now its time to run your program! This can be done with two options:
        1. Run your program directly in your terminal
    ```
    go run main.go
    ```
            * Compiles your Go code in memory and immediately executes it.
            * No standalone binary is produced (the compiled program is temporary).
        2. Create an executable file using the build command. This command creates an file that can be run directly
    ```
    go build main.go
    ./main
    ```
            * Compiles your code into an executable file (e.g., `main` or `main.exe`)
            * Does not automatically run the program; you run the binary separately afterward.
## Thats it!
congratulations on completing your first go project!