# Initialize Your Kubernetes Cluster

Before you can start exploring `kubectl` commands, you need a Kubernetes cluster to work with. This section provides the steps to set up your cluster using kind and apply the necessary resources.

If you've already followed the instructions in [this repository](https://github.com/amraninoam/k8s-kind-dashboard) and have a kind cluster named `sdp`, you can skip the first command.

```bash
# Create a new cluster named 'sdp' with kind, only if you didn't do so already.
kind create cluster --name sdp --config ./cluster/sdp.yaml

# Apply namespace
kubectl apply -f ./resources/ns.yaml

# Apply demo deployment
kubectl apply -f ./resources/demo-deployment.yaml

# Apply service
kubectl apply -f ./resources/service.yaml

# Set 'sdp' as the default namespace for current context
kubectl config set-context --current --namespace=sdp
```

# Now, your Kubernetes cluster is ready, and you can start exploring `kubectl`!

---

# You've just unlocked your first `kubectl` power: setting up a Kubernetes cluster! This is just the beginning, and there are many more exciting commands to explore in the next section.

---

# Next: [Mastering the Basics of kubectl](../1-Mastering-the-Basics/)

---