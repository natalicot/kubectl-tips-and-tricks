
# Debug and Server-Side Apply: Your New Kubernetes Superpowers

Welcome back, intrepid Kubernetes explorer! Are you ready to venture deeper into the `kubectl` toolset? In this section, we're putting the spotlight on `kubectl debug` and `kubectl server-side apply`. These might not seem like the flashiest commands, but trust us, they're secret superpowers in your Kubernetes toolkit.

![Debug robot](/Images/debug-robot.jpg)

## kubectl debug
Imagine being able to sleuth around your Kubernetes pods like a seasoned detective, identifying bugs and diagnosing issues without disrupting their routine. That's what you get with `kubectl debug`! It acts as an in-built inspector, allowing you to scrutinize your code in its live environment, without touching its normal operations. It's like having Sherlock Holmes at your service, dedicated to unmasking the mysteries of your Kubernetes pods!
Behind the scenes, `kubectl debug` leverages the ability of Kubernetes to share process namespaces between containers in a pod. This feature is fundamental to the operation of `kubectl debug`. 
For a deeper understanding, you can refer to the Kubernetes documentation on sharing process namespaces, available at this link: [Share Process Namespace between Containers in a Pod](https://kubernetes.io/docs/tasks/configure-pod-container/share-process-namespace/).


```bash
kubectl apply -f resources/no-sh-deployment.yaml
kubectl get pods

# Fail to exec
POD_NAME=$(kubectl get pods --namespace sdp --no-headers -o custom-columns=":metadata.name" | grep '^no-sh-deployment')
echo $POD_NAME
kubectl exec $POD_NAME -it -- sh
kubectl exec $POD_NAME -it -- cat /etc/config/VARIABLE_1

# kubectl debug
kubectl debug $POD_NAME -it --image=busybox --target=container
ps -ef
cd /proc/<PID>/root
cd etc/config/
cat VARIABLE_1
cat VARIABLE_2
exit

kubectl get pods

```


## kubectl explain

Imagine having a knowledgeable guide at your side, ready to provide insights into the vast Kubernetes wilderness at a moment's notice. That's what `kubectl explain` offers! It's like having an instant Kubernetes encyclopedia. You'll get a detailed explanation of every resource kind, right in your terminal.

With `kubectl explain`, there's no need to keep a browser tab open to the Kubernetes API reference. It brings the information to you, assisting you in understanding the fields and nested objects of Kubernetes resources. Learning and managing Kubernetes resources has never been easier!

Here's an example of how to use `kubectl explain`:

```bash
# Get an explanation of pods
kubectl explain pods

# Get an explanation of a specific field of pods
kubectl explain pods.spec.containers

# Get an explanation of a different resource kind
kubectl explain services
```

## Extra - kubectl auth

Navigating the authorization maze of Kubernetes can be challenging. That's where `kubectl auth` swoops in! It's like a trusty map, guiding you through the labyrinth of permissions and roles. `kubectl auth` provides a suite of helpful subcommands to test and understand the authorizations of your Kubernetes users and service accounts.

With `kubectl auth`, you can verify user permissions, inspect authorization attributes and much more, right from your command line. No need to wrestle with complex RBAC rules manually, `kubectl auth` brings clarity and simplifies the process.

Here's an example of how to use `kubectl auth`:

```bash
# Check if you can create pods in the default namespace
kubectl auth can-i create pods --namespace default

# Check if a service account can list services in the default namespace
kubectl auth can-i list services --namespace default --as=system:serviceaccount:default:myserviceaccount

# Chack if you do it all
kubectl auth can-i '*' '*'
```

---

And that wraps up this section! You've gained even more `kubectl` prowess and are well on your way to becoming a Kubernetes maestro. But the journey doesn't end here. In the next section, we're delving into the powerful world of `kubectl` plugins. Exciting, isn't it? Stay tuned!

---

Next: [Dive into kubectl Plugins](../4-Kubectl-Plugins/)

---
