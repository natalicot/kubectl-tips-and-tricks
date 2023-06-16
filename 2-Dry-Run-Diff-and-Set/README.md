# The Power of Dry Run, Diff and Set

Welcome back, Kubernetes padawan! Ready to wield some more `kubectl` powers? This time, we'll look at `kubectl dry-run`, `kubectl diff` and `kubectl set`. These commands might not sound like much, but they are your secret weapons for managing your Kubernetes resources efficiently.

## kubectl dry-run

Imagine being able to predict the future, to know the consequences of your actions before you take them. Well, with `kubectl dry-run`, that's exactly what you can do! This command allows you to preview changes without applying them to the cluster. It's like having a "try before you buy" option!

With `kubectl dry-run`, you can test it out:

```bash
kubectl apply -f resources/configmap.yaml
kubectl describe cm example-config
sed -i 's/example.property: "Hello, world!"/example.property: "New value"/' resources/configmap.yaml
# Validate syntax
kubectl apply -f resources/configmap.yaml --dry-run=client
# Check config map
kubectl describe cm example-config
kubectl apply -f resources/configmap.yaml

```

## kubectl dry-run - extra

Another Amazing thing you can do dry-run is creating kubernetes manifests on the fly!

```bash
# Create a yaml on the fly
kubectl create deployment my-deployment --image="natalicot/my_awsome_app:flut-log1" --dry-run=client --output=yaml > deployment.yaml
cat deployment.yaml
kubectl apply -f deployment.yaml
kubectl get deployments

# Cleanup
kubectl delete deployment my-deployment
```
## kubectl diff

Imagine having the power to understand the objects in your Kubernetes cluster at a granular level, to analyze the definitions and decode the nature of their existence. Well, with kubectl diff, that's exactly what you can do! This command allows you to compare your local changes with the live state of your Kubernetes cluster. It's like having a powerful magnifying glass to inspect every tiny detail before you finalize your deployment!

```bash
sed -i 's/example.property: "New value"/example.property: "Hello, world!"/' resources/configmap.yaml
kubectl diff -f resources/configmap.yaml

# Cleanup
kubectl delete -f resources/configmap.yaml
```



## kubectl set

Now, let's talk about `kubectl set`. This command is like your magic wand. It allows you to change specific fields on objects already deployed on your cluster. Let's say you want to update the image used by your running pod:

```bash
# Get image
kubectl get deployment my-awesome-app -o=jsonpath='{.spec.template.spec.containers[0].image}'

# Set new image
kubectl set image deployment/my-awesome-app my-awesome-app=natalicot/my_awsome_app:1.0.2

# get deployments
kubectl get deployments

# Get image
kubectl get deployment my-awesome-app -o=jsonpath='{.spec.template.spec.containers[0].image}'

# Check resources
kubectl describe deployment my-awesome-app | grep -A 10 "Containers:"

# set the resources
kubectl set resources deployment/my-awesome-app --requests=cpu=200m,memory=512Mi --limits=cpu=500m,memory=1Gi

# Check resources
kubectl describe deployment my-awesome-app | grep -A 10 "Containers:"
```

---

So there you go, more `kubectl` powers unlocked! Stay tuned for more exciting commands in the next section.

---

Next: [Even More kubectl Commands](../3-Debug-and-Explain/)

---
