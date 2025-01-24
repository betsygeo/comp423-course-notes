# Setting up a dev container for Rust

* Primary author: [Betsy George](https://github.com/betsygeo)

# Prerequisites
Before we dive in, make sure you have:

* A GitHub account: If you don’t have one yet, sign up at [GitHub](https://github.com/).
* Git installed: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.
* Visual Studio Code (VS Code): Download and install it from [here](https://code.visualstudio.com/).
* Docker installed: Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop).

# Part 1. Project SetUp

In your host machine's terminal, make and cd into the directory using the code snippet below:
``` 
mkdir <name_of_repository>
cd <name_of_repository>
```

Initialize a new Git repository:
``` 
git init
```

Navigate your GitHub account to the [Create a New Repository](https://github.com/new) page and fill in the details as you wish

Link your local repository to Github using the code snippet below:
```
git remote add origin https://github.com/<your-username>/<name_of_repository>
git push --set-upstream origin main
```

# Part 2 Setting Up the Development Environment

1. Open your name_of_repository directory 
2. Install the Dev Containers extension for VS Code
3. Create a .devcontainer directory in the root of your project with the following :

.devcontainer/devcontainer.json

4. Update the devcontainer.json file with the following code snippet:
```
{
  "name": "<name_of_repository>",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["rust-lang.rust-analyzer"]
    }
  },
  "postCreateCommand": "rustc --version"
}
```
