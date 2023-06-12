# Kubectl Plugins
Welcome to the world of kubectl plugins! Kubectl plugins are custom extensions that enhance the functionality of the kubectl command-line tool. They allow you to interact with Kubernetes resources in a more efficient and tailored way. Whether you need to automate repetitive tasks, retrieve specific information, or extend kubectl with new commands, plugins have got you covered.

Let`s check some of the more popular plugins:

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
kubectl krew ctx
kubectl krew ns
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