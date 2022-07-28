# Local Coda Pack Development with Docker Containers

<details>
  <summary>Background</summary>
For large coda packs, developing locally is more productive than using Coda Pack Studio. Straight out of Coda Docs, here are some benefits: 

* You can use your own code editing tools, such as Visual Studio Code.
* You can use your own version control system, such as GitHub.
* You can use popular JavaScript libraries1, such as those in NPM.

However, the biggest benefit is the instant feedback loop for testing your code. 
</details>

<details>
  <summary>Why this template</summary>
  
Sadly, installing dependencies for Coda SDK on my local machine was very cumbersome and couldn't get it to fully work. If you're on Windows like me, then you'll even have tougher time.

This template aims to remove all the headache by requiring you to only have the following two dependencies: 

* Docker 
* VSCode

VSCode allows you to develop directly inside a docker container. Therefore, this template contains docker configurations that has all the nessesary dependencies to develop Coda Packs locally. 
</details>

---

## Prerequisites

* Install Docker: Follow the steps at https://code.visualstudio.com/docs/remote/containers#_getting-started
* VSCode
* [VSCode Remote - Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) 

## Using the Template 

### 1 - Clone the  template

Click on `Use this template` as shown below: 

![](https://user-images.githubusercontent.com/3461501/181458534-fa965a5d-b4ac-4693-99d1-651e2f780e64.png)

### 2 - Open template directory in VSCode

### 3 - Reopen directory in container 

### 4 - Initialize new coda pack project
