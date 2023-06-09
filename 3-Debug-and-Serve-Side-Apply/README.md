
# Debug and Server-Side Apply: Your New Kubernetes Superpowers

Welcome back, intrepid Kubernetes explorer! Are you ready to venture deeper into the `kubectl` toolset? In this section, we're putting the spotlight on `kubectl debug` and `kubectl server-side apply`. These might not seem like the flashiest commands, but trust us, they're secret superpowers in your Kubernetes toolkit.

## kubectl debug
Imagine being able to sleuth around your Kubernetes pods like a seasoned detective, identifying bugs and diagnosing issues without disrupting their routine. That's what you get with `kubectl debug`! It acts as an in-built inspector, allowing you to scrutinize your code in its live environment, without touching its normal operations. It's like having Sherlock Holmes at your service, dedicated to unmasking the mysteries of your Kubernetes pods!
Behind the scenes, `kubectl debug` leverages the ability of Kubernetes to share process namespaces between containers in a pod. This feature is fundamental to the operation of `kubectl debug`. 
For a deeper understanding, you can refer to the Kubernetes documentation on sharing process namespaces, available at this link: [Share Process Namespace between Containers in a Pod](https://kubernetes.io/docs/tasks/configure-pod-container/share-process-namespace/).


```bash
kubectl apply -f resources/no-sh-deployment.yaml
kubectl get pods

# Fail to exec
kubectl exec <Pod_Name> -it -- sh
kubectl exec <Pod_Name> -it -- cat /etc/config/VARIABLE_1

# kubectl debug
kubectl debug <Pod_Name> -it --image=busybox --target=container
ps -ef
cd /proc/<PID>/root
cd etc/config/
cat VARIABLE_1
cat VARIABLE_2
exit

# Cleanup
kubectl delete -f resources/no-sh-deployment.yaml

```


## kubectl server-side apply
Think of this: what if you could commit your changes directly on the server with complete confidence? No guesswork, just precise alterations. Well, `kubectl server-side apply` makes this dream come true. It's like having an infallible courier service delivering your Kubernetes resources right to their destination, while diligently tracking the modifications you've implemented. Managing your Kubernetes resources just got a whole lot smarter, thanks to server-side apply!

```bash
# Apply
kubectl apply -f ./resources/server-side-apply.yaml

# Change image
sed -i 's/nginx:latest/nginx:1.17/g' ./resources/server-side-apply.yaml

# Apply
kubectl apply -f ./resources/server-side-apply.yaml

kubectl get pod large-pod  -o json | jq -r '.metadata.annotations'
```
