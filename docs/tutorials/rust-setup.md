[TOC]

# Setting up a Dev Container for Rust
* **Primary author**: [Betsy George](https://github.com/betsygeo)
* **Reviewer**: [Onyi Igwe](https://github.com/igtricia)

# Prerequisites

Before we dive in, make sure you have:

* **A GitHub account**: If you don’t have one yet, sign up at [GitHub](https://github.com/).
* **Git installed**: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.
* **Visual Studio Code (VS Code)**: Download and install it from [here](https://code.visualstudio.com/).
* **Docker installed**: Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop).

# Part 1.
## Project SetUp

(1) In your host machine's terminal, create a new directory for your project and cd into the directory
``` 
mkdir rust-project
cd rust-project
```
(2) Initialize a new Git repository:

``` 
git init
```

(3) Create a README file
```
echo "# rust-project" > README.md
git add README.md
git commit -m "Initial commit with README"
```

(3) Navigate your GitHub account to the [Create a New Repository](https://github.com/new) page and fill in the details as you wish

Link your local repository to Github using the code snippet below:
```
git remote add origin https://github.com/<your-username>/rust-project
```
(4)Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main

(5) Push local commits to Github repository using the code below:
```
git push --set-upstream origin main
```

# Part 2 

## Setting Up the Development Environment

1. Open your rust-project directory in VSCode
2. Install the Dev Containers extension for VS Code if not installed already
3. Create a .devcontainer directory in the root of your project with the following :
```
.devcontainer/devcontainer.json
```
4. Update the devcontainer.json file with the following code snippet :


```yaml
{
  "name": "rust-project",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": [
        "rust-lang.rust-analyzer"
      ]
    }
  },
  
}
```
> **Name**: A descriptive name for container
>
> **Image**: The docker image to use- the latest version of rust
>
>**Customizations**: Useful configurations to vs code that installs the official rust-analyzer VSCode plugin

(5) Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option.

Once your dev container setup completes, close the current terminal tab, open a new terminal pane within VSCode, and try running rustc --version to see your dev container is running a recent version of Rust without much effort! (As of this writing: 1.83.0 released in Novemeber of 2024.)

# Part 3 

## Build Your Hello World Project

Run the following commands in your terminal(inside the container)
1. Create a binary project without automatically creating a new git repository using the code below:
```
cargo new hellocomp423 --vcs none

```
2. Navigate to the project directory using the code below
```
cd hellocomp423
``` 
3. Update the main.rs File in the default location src/main.rs with the code snippet below
```rust
fn main() {
    println!("Hello COMP423");
}
```
4. You can choose either of the follwoing options for the next step

* Build and Run Manually using cargo build: This is the equivalent to the gcc command used to compile a C program and generate an executable file . The cargo build command essentially compiles your project and generates the executable in the target/debig directory and is useful when you are only interested in building without immediately running, for example, deployment process.

```
cargo build
```
After building , you manually run the executable file using the code snippet below
```
./target/debug/hellocomp423
```

* Run Directly using the cargo run command that compiles and runs the project in a singular step.

```
cargo run
```

The key difference between this two is that cargo run is faster and compiles the project all over again irrespective of the previous build. cargo build is mainly used to have access to the executable file. 

Congratulations! You have written a program in Rust Programming Language. You can now push your local commits to your repository.