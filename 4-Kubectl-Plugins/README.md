# Kubectl Plugins
Welcome to the world of kubectl plugins! Kubectl plugins are custom extensions that enhance the functionality of the kubectl command-line tool. They allow you to interact with Kubernetes resources in a more efficient and tailored way. Whether you need to automate repetitive tasks, retrieve specific information, or extend kubectl with new commands, plugins have got you covered.

Let`s check some of the more popular plugins:

# Create your own plugin!
```bash
# make the plugin executable
sudo chmod +x ./kubectl-sdp

# place it anywhere in your PATH
sudo mv ./kubectl-sdp /usr/local/bin

# Check you Plugin
kubectl plugin list

# Use the plugin
kubectl sdp
kubectl sdp help
kubectl sdp set-ns
kubectl sdp welcome
```


## Krew

[Krew](https://krew.sigs.k8s.io/) is a package manager for `kubectl` plugins. Krew allows you to discover and install plugins on your machine, enhancing the interaction with Kubernetes. With Krew, you can easily find, share, and use plugins, making your Kubernetes operations more productive and efficient.

### Installing Krew

For detailed installation instructions, please refer to the [official Krew installation guide](https://krew.sigs.k8s.io/docs/user-guide/setup/install/).

After successful installation, don't forget to add the `~/.krew/bin` directory to your `PATH` to be able to run the `kubectl` plugins you install. 

You can verify the installation by running `kubectl krew` in your terminal. This should display the Krew version along with its command structure.

#### Example
```bash
kubectl krew version
kubectl krew list
```

## Kubectl ctx and ns

`kubectl-ctx` and `kubectl-ns` are two plugins that can be used to switch between different Kubernetes contexts and namespaces. They help in simplifying the interaction with different Kubernetes clusters and namespaces by providing short commands to switch between them.

#### Installing kubectl-ctx and kubectl-ns

You can install both `kubectl-ctx` and `kubectl-ns` via Krew. Assuming you have [Krew](https://krew.sigs.k8s.io/docs/user-guide/setup/install/) installed, you can install these plugins with the following commands:

```bash
kubectl krew install ctx
kubectl krew install ns
```

#### Example
```bash
kubectl ctx
kubectl ns
```

### kubectl score

[Kubectl Score](https://github.com/zegl/kube-score) is a tool that performs static code analysis of your Kubernetes object definitions. The aim of kube-score is to provide an easy to use tool to validate your Kubernetes YAML or JSON configuration files. With it, you can get your configuration files scored for best practices and identify potential issues before deploying them to your clusters.

#### Installing Kubectl Score

You can install `kubectl-score` via Krew. Assuming you have [Krew](https://krew.sigs.k8s.io/docs/user-guide/setup/install/) installed, you can install `kubectl-score` with the following command:

```bash
kubectl krew install score
```

#### Example
```bash
kubectl score score ./resources/bad-pod.yaml
kubectl score score ./resources/good-pod.yaml
kubectl score score ./resources/even-better-pod.yaml
kubectl score score ./resources/the-perfect-pod.yaml
```

### kubectl kubescape

[Kubescape](https://github.com/armosec/kubescape) is a Kubernetes-native tool for testing Kubernetes deployments against the Kubernetes Hardening Guide from the NSA and Cybersecurity & Infrastructure Security Agency (CISA). It provides an easy way to check whether your deployment is following best practices for Kubernetes security.

You can install `kubescape` via Krew. Assuming you have [Krew](https://krew.sigs.k8s.io/docs/user-guide/setup/install/) installed, you can install `kubescape` with the following command:

#### Installing kubescape

```bash
kubectl krew install kubescape
```
#### Example
```bash
kubectl kubescape scan
```

### kubectl deprecations

`deprecations` is a Kubernetes-native tool for checking your Kubernetes deployment for deprecated APIs. It can help you update your deployments to use the latest API versions and avoid issues when upgrading your Kubernetes cluster.

You can install `deprecations` via Krew. Assuming you have [Krew](https://krew.sigs.k8s.io/docs/user-guide/setup/install/) installed, you can install `deprecations` with the following command:

#### Installing deprecations

```bash
kubectl krew install deprecations
```
Example
To scan your Kubernetes deployments for deprecated APIs, you would run:

```bash
kubectl deprecations
# Check on version 1.27
kubectl deprecations --k8s-version "v1.27.3"
```
This command will inspect all API objects in your cluster and highlight any that are using deprecated APIs. Please be sure to review the documentation or help output of the plugin for more information and any additional options or features.


### kubectl aws-auth

`kubectl aws-auth` is a kubectl plugin to manage AWS IAM Authenticator's authentication ConfigMap. It simplifies the process of managing AWS IAM Authenticator configuration.


#### Installing kubectl aws-auth

You can install `kubectl aws-auth` via Krew. Assuming you have [Krew](https://krew.sigs.k8s.io/docs/user-guide/setup/install/) installed, you can install `kubectl aws-auth` with the following command:

```bash
kubectl krew install aws-auth
```

#### Example
Note - this example is only valid for an EKS cluster
```bash
kubectl aws-auth get
kubectl aws-auth upsert --maproles --rolearn arn:aws:iam::555555555555:role/test-user --username test-user --groups system:master
# Remove all access belonging to an ARN
kubectl aws-auth remove --maproles --rolearn arn:aws:iam::555555555555:role/test-user
```