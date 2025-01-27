# Setting up a dev container for Go.
* Primary Author: [Nithya Indlamuri](https://github.com/nithyaindla)
* Reviewer: [Megha Thumma](https://github.com/mthumma20)

## What is Go?
    Go, also known as Golang, is an open-source programming language that Google developed to address software engineering challenges. It's used to develop a variety of applications, including web applications, cloud services, and network servers. Feel free to install Cloud Client Libraries for Go, Google Cloud CLI, and more depending on your project.

## Prerequisites
1. __A GitHub account:__ If you don’t have one yet, sign up at GitHub.
2. __Git installed:__ Install Git if you don’t already have it.
3. __Visual Studio Code (VS Code):__ Download and install it from here.
4. __Docker installed:__ Required to run the dev container. Get Docker here.
5. __Command-line basics:__ Your COMP211 command-line knowledge will serve you well here. If in doubt, review the Learn a CLI text!


## Creating the Repo
1. Make sure Docker is running. 
2. Create a local directory and initialize git
Open your terminal or command prompt. Create new directory for your project. Initialize new Git repo. Create and add to to the README file.
```
    mkdir go-tutorial-notes
    cd go-tutorial-notes
    git init

2. Create a remote Repo on GitHub
    1. Log in to GitHub > Create a New Repo
    2. Decide Repo name, description, and visibility
    3. Do not initialize rep with a README, .gitignore, or license
    4. Click Create Repo
3. Link your Local Repo to GitHub
    1. Add GitHub repo as a remote.
    ```
    git remote add origin https://github.com/<your-username>/<remote-repo-name>.git
    ```
    2. Check default branch name. If not "main", then do:
    ```
    git branch -M main
    ```
    3. Push local commits to GitHub
    ```
    git push --set-upstream origin main
    ```
## Setting up Dev Environment
1. Open Project in VS Code
2. Install Dev Containers extension and Go extension
3. Create a .devcontainer folder with devcontainer.json file using the following commands:
```
mkdir .devcontainer
code .devcontainer/devcontainer.json
```
4. Add the configuration:
```
{
  "name": "Go Dev Environment",
  "image": "golang:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.go"]
    }
  },
  "postCreateCommand": "go mod init go-course-notes && go mod tidy"
}
```
go mod init go-tutorial-notes
    echo <Text-to-add-to-README>> README.md
    git add README.md
    git commit -m "Initial commit with README"
```
!!! note What is "go mod"
    "go mod" is a tool that helps you track and manage which packages (or dependencies) your project uses. It's like having a list of books in your library, so you know exactly which books are part of your project and which version of them you’re using.

    Without go mod, managing dependencies would be messy. If you use packages but don't track which version you're using, your code could break if a new version of a package is released. go mod keeps everything organized and ensures you're using the right versions.
    When you start a Go project, you run go mod init <"module-name">. This creates a file called go.mod, which is like the table of contents for your project. It lists the packages your project uses and the versions of those packages.

    The two main commands:
    go mod init <"module-name">: Initializes a new module for your project.
    go mod tidy: Cleans up your module by removing any unused packages or dependencies.

## Running and Testing
1. Add a main.go file `code main.go`
2. Add the following to the file:
```
package main
func main() {
    log.Println("Hello COMP423")
}
```
3. Open terminal and run `go run main.go` Check to see if it outputted "Hello COMP423".

4. Enter the following: 
```
go build
main.exe
```
This should return "Hello COMP423".

!!! note "What is go build?"
    "go build" is a command in Go (Golang) that compiles your Go source code into an executable binary. It takes the Go source code in the current directory (or the files you specify) and compiles them into a binary file. This binary is an executable program but does not run until told. It automatically has the same name as your project directory.