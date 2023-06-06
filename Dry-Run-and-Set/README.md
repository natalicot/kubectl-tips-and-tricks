# The Power of Dry Run and Set

Welcome back, Kubernetes padawan! Ready to wield some more `kubectl` powers? This time, we'll look at `kubectl dry-run` and `kubectl set`. These commands might not sound like much, but they are your secret weapons for managing your Kubernetes resources efficiently.

## kubectl dry-run

Imagine being able to predict the future, to know the consequences of your actions before you take them. Well, with `kubectl dry-run`, that's exactly what you can do! This command allows you to preview changes without applying them to the cluster. It's like having a "try before you buy" option!

With `kubectl dry-run`, you can test it out:

```bash
kubectl apply -f resources/configmap.yaml
sed -i 's/example.property: "Hello, world!"/example.property: "New value"/' resources/configmap.yaml
# Validate sintaks
kubectl apply -f resources/configmap.yaml --dry-run=client
# Check th yaml
kubectl apply -f resources/configmap.yaml --dry-run=client
kubectl delete -f resources/configmap.yaml

# Create a yaml on the fly
kubectl create deployment my-deployment --image="natalicot/my_awsome_app:flut-log1" --dry-run=client --output=yaml > deployment.yaml
cat deployment.yaml
kubectl apply -f deployment.yaml
kubectl get deployments
kubectl delete deployment my-deployment
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

# set the resources
kubectl set resources deployment/my-awesome-app --requests=cpu=200m,memory=512Mi --limits=cpu=500m,memory=1Gi

# Check resources
kubectl describe deployment my-awesome-app | grep -A 10 "Containers:"
```

---

So there you go, more `kubectl` powers unlocked! Stay tuned for more exciting commands in the next section.

---

Next: [Even More kubectl Commands](../Kubectl-diff/)

---
