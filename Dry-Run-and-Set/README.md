# The Power of Dry Run and Set

Welcome back, Kubernetes padawan! Ready to wield some more `kubectl` powers? This time, we'll look at `kubectl dry-run` and `kubectl set`. These commands might not sound like much, but they are your secret weapons for managing your Kubernetes resources efficiently.

## kubectl dry-run

Imagine being able to predict the future, to know the consequences of your actions before you take them. Well, with `kubectl dry-run`, that's exactly what you can do! This command allows you to preview changes without applying them to the cluster. It's like having a "try before you buy" option!

For instance, let's say you want to create a pod but aren't sure if your configuration file is correct. Here's a simple pod configuration file (`my-pod.yaml`):

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-nginx-pod
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.16.1
    ports:
    - containerPort: 80
```

With `kubectl dry-run`, you can test it out:

```bash
kubectl create -f my-pod.yaml --dry-run=client
```

This command will validate your configuration and tell you whether the pod can be created successfully.

## kubectl set

Now, let's talk about `kubectl set`. This command is like your magic wand. It allows you to change specific fields on objects already deployed on your cluster. Let's say you want to update the image used by your running pod:

```bash
kubectl set image pod/my-running-pod my-container=my-new-image
```

Boom! Your pod is now running with the new image. It's that simple.

---

So there you go, more `kubectl` powers unlocked! Stay tuned for more exciting commands in the next section.

---

Next: [Even More kubectl Commands](slide-4.md)

---
