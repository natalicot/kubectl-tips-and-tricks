# Mastering the Basics: kubectl Commands

Well hello there, aspiring Kubernetes master! Ready to dive into some `kubectl` goodness? Here are some of the basic commands that you'll use often - it's like the ABCs of `kubectl`.

## kubectl get

This command is like the Google of Kubernetes. Use it to display one or many resources. Say, you forgot how many pods you have running? No worries, `kubectl get pods` to the rescue! Need to know the status of all your services? Just a quick `kubectl get services` and you'll be swimming in information.

```bash
kubectl get pods
kubectl get services


## kubectl describe

Now, if `kubectl get` is the Google, `kubectl describe` is like your private detective. It shows you the details of a specific resource or a group of resources. Want to know everything about a specific pod? `kubectl describe pod my-awesome-pod` and voila! You get all the nitty-gritty details.

```bash
kubectl describe pod my-awesome-pod

## kubectl logs

Ever wish you could be a fly on the wall in your containers? Meet `kubectl logs`. This command is used to print the logs for a container in a pod. So next time your application is acting up, just ask `kubectl logs my-buggy-pod` and unravel the mystery!

```bash
kubectl logs my-buggy-pod


## kubectl exec

Last but not least, meet the puppet master command - `kubectl exec`. This command is used to execute a command in a container. Want to check something quickly in your container? `kubectl exec my-pod -- ls /` lets you list everything at the root directory. Talk about power at your fingertips!

```bash
kubectl exec my-pod -- ls /

And that's your crash course to `kubectl`! Remember, with great power comes great responsibility. Use your commands wisely!

In the next section, we'll explore some more advanced `kubectl` commands. Stay tuned!

---

Next: [Advanced kubectl Commands](slide-3.md)

---
