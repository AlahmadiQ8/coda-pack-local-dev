# Local Coda Pack Development with Docker Containers <!-- omit from toc -->

**TLDR:** Install docker, install VSCode, install [Remote - Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers), clone this template, open vscode command pallete and run `Reopen in Container`, open bash terminal and run `npx coda init`. 

---

- [Background](#background)
- [How it works](#how-it-works)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
  - [Option 1: Use this Template](#option-1-use-this-template)
    - [1 - Clone the  template](#1---clone-the--template)
    - [2 - Open template directory in a VSCode workspace](#2---open-template-directory-in-a-vscode-workspace)
  - [Option 2: Start from scratch](#option-2-start-from-scratch)
  - [Initialize new coda pack project](#initialize-new-coda-pack-project)

---

# Background

For large coda packs, developing locally is more productive than using Coda Pack Studio. Straight out of Coda SDK Docs, here are some benefits: 

* You can use your own code editing tools, such as Visual Studio Code.
* You can use your own version control system, such as GitHub.
* You can use popular JavaScript libraries1, such as those in NPM.
* Instant feedback loop for testing your code. Just `npx coda execute ...` to test your pack blocks. 

Unfortunately, setting up local development environment for Coda SDK is a not easy just having NodeJs and npm installed. but you also need to install `isolated-vm` which already has its [own requirements](https://github.com/laverdet/isolated-vm#requirements). Instructions also differ whether you are on Windows, MacOs, or Linux. 

Now you can get started with local development within 5 minutes regardless of your platform. All you need is to have Docker and VSCode installed. 

# How it works

VSCode allows you to open any folder inside (or mounted into) a docker container and take advantage of Visual Studio Code's full feature set. A [devcontainer.json](/.devcontainer/devcontainer.json) file tells VS Code how to access (or create) a development container with a well-defined tool and runtime stack.

This template is almost exact copy of the container configurations generated from the [VSCode Remote - Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers). There are only a couple of line changes. See [start from scratch option](#option-2-start-from-scratch)

More information information, checkout the full documentation: https://code.visualstudio.com/docs/remote/containers. 

# Prerequisites

* Install Docker: Follow the steps at https://code.visualstudio.com/docs/remote/containers#_getting-started
* VSCode
* [VSCode Remote - Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) 

# Setup

There are two options to setup. Either just use this template, or start from scratch by generating the `.devcontainer` congiruations yourself via `Add Development Container Configuration Files...` command and making some changes. 

The benefits of the first options is that we might add more custom configratutions in the future where all you need to do is just clone the template. 

## Option 1: Use this Template 

### 1 - Clone the  template

Click on `Use this template` as shown below: 

![](https://user-images.githubusercontent.com/3461501/181458534-fa965a5d-b4ac-4693-99d1-651e2f780e64.png)

### 2 - Open template directory in a VSCode workspace

Open a new VSCode workspace for the template repository you just cloned. VSCode will prompt you to reopn the workspace in a docker container as shown below: 

![](https://user-images.githubusercontent.com/3461501/181879418-cf58f09f-4e4c-4af1-8a6c-b359e4af62ae.png)
<!-- https://user-images.githubusercontent.com/3461501/181745855-4cd4177e-e2f6-4166-9cf1-195e3de25782.png -->

Click on `Reopen in Container`. This will do the following: 

1. Build a docker image based on the dockerfile inside `.devcontainer` folder
2. Launch a docker container using the docker image
3. Reopens VSCode inside the container

## Option 2: Start from scratch

Open a new blank workspace. Run the following command to add `.devcontainer` configurations for Noejs environment. 

![gif-record-2](https://user-images.githubusercontent.com/3461501/181899898-c8b6163a-07fe-4069-a8ab-02a35171d3e7.gif)

In the `.devcontainer.json`, make sure you setup port forwarding:

```json
  //  ...
	"forwardPorts": [3000],
  // ...
```

In the `Dockerfile` add the following line at the end 

```Dockerfile
RUN su node -c "npm install -g @codahq/packs-sdk"
```


## Initialize new coda pack project

![](https://user-images.githubusercontent.com/3461501/181888989-987f829b-c074-4f57-85d0-e6bf6409adea.gif)

