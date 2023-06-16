# Welcome: Kubernetes Visualization and Kubectl Tricks

Hello, and welcome! This repository is part of a Sela Software Development Practices (SDP) lecture titled "Kubernetes Visualization and Kubectl Tricks". This is more than just a lecture—it's a journey through the fascinating world of Kubernetes, its visualization techniques, and some clever tricks for using `kubectl`.

The lecturers guiding you on this journey are [Noam Amrani](https://www.linkedin.com/in/noamamrani/) and [Natali Cutic](https://www.linkedin.com/in/natali-cutic-24a444157/). 

This repo builds upon our previous work on kind kubernetes dashboard, which you can find in [this repository](https://github.com/amraninoam/k8s-kind-dashboard).

Now, buckle up as we dive into the depths of `kubectl`.

![Welcome Robot](Images/Welcome-robot.jpg)

---

## Kubernetes: Exploring kubectl

Welcome to this comprehensive journey into the world of `kubectl`, a versatile command-line tool for interacting with a Kubernetes cluster.

### What is kubectl?

`kubectl` is a powerful CLI tool that is used to deploy, manage, and scale containerized applications using Kubernetes, an open-source container orchestration system.

### Key Features

- Deploy and manage applications on Kubernetes
- Get insights into your application and cluster
- Create, update, and delete various Kubernetes resources
- Use labels to organize Kubernetes resources
- Auto-completion support for Bash and Zsh shells to save typing

Fun Fact: Did you know that `kubectl` supports autocompletion for Bash and Zsh? This can save you a lot of typing!

### Installation

Before we proceed, it's important to ensure that you have `kubectl` installed on your system.

For detailed instructions on how to install `kubectl`, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

### Autocompletion in Bash and Zsh

To make your journey easier and more efficient, `kubectl` supports autocompletion for both Bash and Zsh shells. Here is how you can set it up:

#### Bash

Ensure bash-completion is installed. The procedures vary based on the Linux distribution:

```bash
# macOS
brew install bash-completion@2

# Ubuntu
apt-get install bash-completion
```

Once installed, add the following lines to your `~/.bash_profile` file for `kubectl` autocompletion,
For Zsh, add the completion script to your `.zshrc` file:

```bash
echo 'source <(kubectl completion bash)' >>~/.bash_profile
echo 'alias k=kubectl' >>~/.bash_profile
echo 'complete -F __start_kubectl k' >>~/.bash_profile
source ~/.bash_profile
```


### Setting KUBE_EDITOR

You can set your preferred editor for Kubernetes like this:

```bash
echo "export KUBE_EDITOR=\"nano\"" >>  ~/.bash_profile
```

### Setting Alias

It is very reomended to set an alias when working whith kubectl

```bash
echo "alias k=kubectl" >>  ~/.bash_profile
```


### Next Steps

As we move forward, we will dive deep into each functionality that `kubectl` offers, providing practical examples that you can try out yourself.

Enjoy the journey!

---

Next: [Mastering the basics](./1-Mastering-the-basics)

Remember to go through the cluster initialization process if you want to follow allong [Initializing the cluster](./0-Cluster-Setup/)

---

This README is part of a lecture series on `kubectl`. Find more information in the upcoming slides. Stay tuned!

---
